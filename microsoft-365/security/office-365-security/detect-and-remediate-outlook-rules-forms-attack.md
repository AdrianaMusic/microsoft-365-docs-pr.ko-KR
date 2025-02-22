---
title: Outlook 규칙 및 사용자 지정 양식 주입 공격을 감지하고 수정합니다.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: 04/23/2018
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
description: Office 365에서 Outlook 규칙 및 사용자 지정 양식 주입 공격을 인지하고 재구성하는 방법 알아보기
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cbdc41315d64d341248d6900147aabc5a0b9877c
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663646"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Outlook 규칙 및 사용자 지정 양식 주입 공격 감지 및 재구성

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**요약** Office 365에서 Outlook 규칙 및 사용자 지정 양식 주입 공격을 인지하고 재구성하는 방법 알아보기

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Outlook 규칙과 사용자 지정 양식 주입 공격은 무엇인가요?

공격자는 테넌트에서 계정을 침해하고 침범한 후에 검색되고 제거된 후 계정에 머무르거나 다시 돌아올 방법을 시도하고 설정할 것입니다. 이를 지속성 메커니즘을 설정이라고 합니다. 이 작업을 수행할 수 있는 두 가지 방법은 Outlook 규칙을 활용하거나 Outlook에 사용자 지정 양식을 주입하는 것입니다.
두 경우 모두 해당 규칙이나 양식이 클라우드 서비스에서 데스크톱 클라이언트로 동기화되므로 클라이언트 소프트웨어를 완벽하게 포맷하고 다시 설치하여도 주입 메커니즘을 제거할 수 없습니다. 이는 Outlook 클라이언트 소프트웨어가 클라우드의 사서함에 다시 연결하는 경우 클라우드에서 규칙과 양식이 다시 다운로드되기 때문입니다. 규칙과 양식이 준비되면 공격자는 이를 사용하 여 원격 또는 사용자 지정 코드를 실행하여 일반적으로 로컬 컴퓨터에 맬웨어를 설치합니다. 그런 다음 맬웨어는 자격 증명을 다시 도용하거나 다른 불법 활동을 수행합니다.
여기서 좋은 소식은 클라이언트를 최신 버전으로 유지하면 현재 Outlook 클라이언트 기본값으로 이 두 가지 메커니즘을 차단함에 따라 위협에 취약하지 않다는 것입니다.

이 공격은 일반적으로 다음의 패턴을 따릅니다.

**규칙 활용**:

1. 공격자는 사용자 가운데 한 명의 사용자 이름과 암호를 도용합니다.

2. 그런 다음 공격자는 해당 사용자의 Exchange 사서함에 로그인합니다. 사서함은 Exchange Online에 있거나 Exchange 온-프레미스에 있을 수 있습니다.

3. 그런 다음 공격자는 사서함에서 규칙 조건과 일치하는 전자 메일을 받을 때 트리거되는 사서함에 전달 규칙을 만듭니다. 규칙과 트리거 전자 메일의 조건은 서로에 맞게 구성됩니다.

4. 공격자는 자신의 사서함을 일반적으로 사용하는 사용자에게 트리거 전자 메일을 보냅니다.

5. 전자 메일을 받으면 규칙이 트리거됩니다. 규칙의 작동은 대개 원격(WebDAV) 서버에서 응용 프로그램을 시작하는 것입니다.

6. 일반적으로 응용 프로그램은 사용자 컴퓨터에 로컬로 [Powershell Empire](https://www.powershellempire.com/)와 같은 맬웨어를 설치합니다.

7. 공격자는 이 맬웨어를 사용하여 로컬 컴퓨터에서 사용자의 사용자 이름과 암호 혹은 기타 자격 증명을 다시 도용하고 다른 악의적인 활동을 수행할 수 있습니다.

**양식 활용**:

1. 공격자는 사용자 가운데 한 명의 사용자 이름과 암호를 도용합니다.

2. 그런 다음 공격자는 해당 사용자의 Exchange 사서함에 로그인합니다. 사서함은 Exchange Online에 있거나 Exchange 온-프레미스에 있을 수 있습니다.

3. 그런 다음 공격자는 사용자 지정 메일 양식 서식 파일을 만들어 사용자의 사서함에 삽입합니다. 사용자 지정 양식은 사서함이 사용자 지정 양식을 로드해야 하는 전자 메일을 받을 때 트리거됩니다. 사용자 지정 양식과 전자 메일 서식은 서로에 맞게 구성됩니다.
4. 공격자는 자신의 사서함을 일반적으로 사용하는 사용자에게 트리거 전자 메일을 보냅니다.

5. 전자 메일을 받으면 양식이 로드됩니다. 양식은 원격(WebDAV) 서버에서 응용 프로그램을 시작합니다.

6. 일반적으로 응용 프로그램은 사용자 컴퓨터에 로컬로 [Powershell Empire](https://www.powershellempire.com/)와 같은 맬웨어를 설치합니다.

7. 공격자는 이 맬웨어를 사용하여 로컬 컴퓨터에서 사용자의 사용자 이름과 암호 혹은 기타 자격 증명을 다시 도용하고 다른 악의적인 활동을 수행할 수 있습니다.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>어떠한 규칙 및 사용자 지정 양식 주입 공격이 Office 365와 같아 보일 수 있나요?

이러한 지속성 메커니즘은 사용자가 발견할 가능성이 거의 없으며 일부의 경우에 보이지 않을 수도 있습니다. 이 문서에서는 아래에 나열된 7가지 기호(위험 노출 표시기)를 찾는 방법을 알려줍니다. 이러한 내용을 발견하면 재구성 단계를 수행해야 합니다.

- 규칙 위험 노출 표시기:

  - 규칙 작업은 응용 프로그램을 시작하는 것입니다.

  - 규칙에서 EXE, ZIP 또는 URL을 참조합니다.

  - 로컬 컴퓨터에서 Outlook PID가 보낸 새 프로세스 시작을 찾습니다.

- 사용자 지정 양식 위험 노출 표시기:

  - 사용자 지정 양식이 자신의 메시지 클래스로 저장됩니다.

  - 메시지 클래스가 실행 코드를 포함합니다.

  - 보통 개인 양식 라이브러리 또는 받은 편지함 폴더에 저장됩니다.

  - 양식의 이름은 IPM.Note.[사용자 지정 이름]으로 되어 있습니다.

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>이 공격의 신호를 찾고 확인하는 단계

다음의 두 가지 방법 중 하나를 사용하여 공격을 확인할 수 있습니다.

- Outlook 클라이언트를 사용하여 각 사서함에 대한 규칙과 양식을 수동으로 검사합니다. 이 방법은 철저하지만 한번에 한 명의 사서함 사용자만 검사할 수 있어 검사할 사용자가 많은 경우에는 막대한 시간이 소요됩니다. 또한 검사를 실행하는 컴퓨터를 침해할 수도 있습니다.

- [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 스크립트를 사용하여 테넌트의 모든 사용자에 대한 모든 메일 전달 규칙과 사용자 지정 양식을 자동으로 덤프합니다. 이 방법은 최소한의 오버 헤드를 사용하는 가장 빠르고 안전한 방법입니다.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Outlook 클라이언트를 사용하여 규칙의 공격을 확인

1. 사용자로 사용자 Outlook 클라이언트를 엽니다. 사용자는 사서함에 대한 규칙을 확인하는 데 도움이 필요할 수 있습니다.

2. Outlook에서 규칙 인터페이스를 여는 방법에 대한 절차는 [규칙을 사용하여 전자 메일 메시지 관리](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) 문서를 참조하세요.

3. 사용자가 만들지 않은 규칙 또는 의심스러운 이름을 사용하여 예기치 않은 규칙이나 규칙을 찾습니다.

4. 규칙 설명에서 응용 프로그램을 시작하거나 .EXE, .ZIP을 참조하거나 URL을 실행하는 규칙 작업을 찾아봅니다.

5. Outlook 프로세스 ID를 사용하여 시작하는 새 프로세스를 찾습니다. [프로세스 ID 찾기](https://docs.microsoft.com/windows-hardware/drivers/debugger/finding-the-process-id)를 참조합니다.

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Outlook 클라이언트를 사용하여 양식 공격을 확인하는 단계

1. 사용자로 사용자 Outlook 클라이언트를 엽니다.

2. 사용자 버전의 Outlook에서의 [개발자 탭을 표시](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45)에 나와 있는 단계를 따릅니다.

3. Outlook에서 현재 표시되는 개발자 탭을 열고 **양식 디자인** 을 클릭합니다.

4. **찾기** 목록에서 **받은 편지함** 을 선택합니다. 사용자 지정 양식을 찾습니다. 사용자 지정 양식은 거의 드물지만 사용자 지정 양식이 있는 경우에도 더 깊이 있게 확인할 가치가 있습니다.

5. 특히 숨김으로 표시된 사용자 지정 양식을 조사 합니다.

6. 사용자 지정 양ㅇ식을 열고 **양식** 그룹에서 **코드 보기** 를 클릭하여 양식이 로드될 때 어떤 작업이 실행되는지 확인 합니다.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>PowerShell을 사용하여 규칙과 양식 공격을 확인 하는 단계

규칙 또는 사용자 지정 양식 공격을 확인하는 가장 간단한 방법은 [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 스크립트를 실행하는 것입니다. 이 스크립트는 테넌트의 모든 사서함에 연결하 고 모든 규칙과 양식을 두 개의 .csv 파일로 덤프합니다.

#### <a name="pre-requisites"></a>필수 구성 요소

스크립트가 테넌트의 모든 사서함에 연결하여 규칙과 양식을 읽기 때문에 스크립트를 실행하려면 전역 관리자 권한이 필요합니다.

1. 로컬 관리자 권한으로 스크립트를 실행할 컴퓨터에 로그인합니다.

2. GitHub에서 Get-AllTenantRulesAndForms.ps1 스크립트를 실행할 폴더로 다운로드하거나 복사합니다. 이 스크립트는 이 폴더 MailboxFormsExport-yyyy-mm-dd.csv 및 MailboxRulesExport-yyyy-mm-dd.csv에 2개의 날짜 스탬프가 찍힌 파일을 만듭니다.

3. PowerShell 인스턴스를 관리자로 열고 스크립트를 저장한 폴더를 엽니다.

4. `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1과 같이이 PowerShell 명령줄을 실행합니다.

#### <a name="interpreting-the-output"></a>결과 해석

- **MailboxRulesExport *-yyyy-mm-dd*.csv**: 응용 프로그램 또는 실행 파일이 포함된 작동 조건에 대한 규칙(행 당 하나씩)을 검사합니다.

  - **ActionType(A열)**: "ID_ACTION_CUSTOM" 값이 표시되는 경우 이 규칙은 악의가 있을 가능성이 큽니다.

  - **IsPotentiallyMalicious(D열)**:이 값이 "TRUE" 인 경우 이 규칙은 악의가 있을 가능성이 큽니다.

  - **ActionCommand(G열)**: 응용 프로그램이 나 확장명이 .exe, .zip인 파일 또는 있지 않아야 할 URL을 참조하는 항목이 열거되는 경우 이 규칙은 악의가 있을 가능성이 큽니다.

- **MailboxFormsExport *-yyyy-mm-dd*.csv**: 일반적으로 사용자 지정 양식을 사용하는 경우는 거의 없습니다. 이 통합 문서에서 양식을 찾은 경우 해당 사용자의 사서함을 열고 양식 자체를 확인합니다. 조직에서 의도적으로 이를 추가하지 않은 경우 악의가 있을 가능성이 큽니다.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Outlook 규칙과 양식 공격을 중지하고 재구성하는 방법

이러한 공격에 대한 증거를 발견한 경우에는 재구성이 간단하며 사서함에서 규칙이나 양식을 삭제하기만 하면 됩니다. Outlook 클라이언트에서 이 작업을 수행하거나 원격 PowerShell을 사용하여 규칙을 제거할 수 있습니다.

### <a name="using-outlook"></a>Outlook 사용

1. 사용자가 Outlook에서 사용한 모든 장치를 확인합니다. 이들 장치 모두에서 잠정 맬웨어를 청소해야 합니다. 모든 장치를 청소할 때 까지는 사용자가 로그온 하고 전자 메일을 사용하지 않도록 합니다.

2. 각 장치에 대한 [규칙 삭제](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f)에 있는 단계를 따릅니다.

3. 다른 맬웨어의 존재 여부가 확실하지 않은 경우 장치의 모든 소프트웨어를 포맷하고 다시 설치할 수 있습니다. 모바일 장치의 경우 제조업체의 단계에 따라 장치를 출하 이미지로 재설정할 수 있습니다.

4. 최신 버전의 Outlook을 설치합니다. 최신 버전의 Outlook은 기본적으로 이 두 가지 유형의 공격을 차단한다는 사실을 기억하세요.

5. 사서함의 모든 오프라인 복사본이 제거된 후 사용자의 암호를 다시 설정하고(고품질의 복사본 사용) MFA를 아직 사용하도록 설정하지 않은 경우 사용자에 대해 다단계 인증을 설치하는 단계를 수행합니다. [](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/set-up-multi-factor-authentication) 이렇게 하면 사용자의 자격 증명이 다른 수단(예: 피싱 또는 암호 재사용)을 통해 노출되지 않습니다.

### <a name="using-powershell"></a>PowerShell 사용

위험한 규칙을 제거하거나 해제하는 데 사용할 수 있는 두 개의 원격 PowerShell cmdlet이 있습니다. 다음의 단계를 따릅니다.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Exchange 서버에 있는 사서함에 대한 단계

1. 원격 PowerShell을 사용하여 Exchange 서버에 연결합니다. [원격 PowerShell을 사용하여 Exchange 서버에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)에 있는 단계를 따릅니다.

2. 사서함의 단일 규칙, 여러 규칙 또는 모든 규칙을 완전히 제거하려면 [InboxRule 제거](https://docs.microsoft.com/powershell/module/exchange/Remove-InboxRule) cmdlet을 사용합니다.

3. 추가 조사를 위해 규칙과 해당 콘텐츠를 보존하려면 [InboxRule 비활성화](https://docs.microsoft.com/powershell/module/exchange/disable-inboxrule) cmdlet을 사용합니다.

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Exchange Online의 사서함에 대한 단계

1. [PowerShell을 사용하여 Exchange Online에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)에 있는 단계를 따릅니다.

2. 사서함의 단일 규칙, 여러 규칙 또는 모든 규칙을 완전히 제거하려면 [받은 편지함 제거 규칙](https://docs.microsoft.com/powershell/module/exchange/Remove-InboxRule) cmdlet을 사용합니다.

3. 추가 조사를 위해 규칙과 해당 콘텐츠를 보존하려면 [InboxRule 비활성화](https://docs.microsoft.com/powershell/module/exchange/disable-inboxrule) cmdlet을 사용합니다.

## <a name="how-to-minimize-future-attacks"></a>미래의 공격을 최소화하는 방법

### <a name="first-protect-your-accounts"></a>첫 번째: 계정 보호

사용자 계정 중 하나를 도난 혹은 침해를 받은 경우에만 공격자가 이 규칙과 양식을 활용합니다. 따라서 조직에서 이러한 악용을 방지하는 첫 번째 단계는 사용자 계정을 적극적으로 보호하는 것입니다. 계정을 침해하는 가장 일반적인 방법 중 일부는 피싱 또는 [암호 스프레이](https://www.dabcc.com/microsoft-defending-against-password-spray-attacks/) 공격을 통해 발생합니다.

사용자 계정 및 특히 관리자 계정을 보호하는 가장 좋은 방법은 사용자에 대해 다단계 인증을 [설정하는 것입니다.](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/set-up-multi-factor-authentication) 사용자는 또한:

- 사용자 계정이 [액세스되고 사용되는](https://docs.microsoft.com/azure/active-directory/active-directory-view-access-usage-reports) 방식을 모니터링합니다. 초기 침해를 방지하지 못할 수 있지만 침해의 기간과 영향은 더 일찍 발견하여 줄일 수 있습니다. [Office 365 클라우드 앱 보안 정책](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)을 사용 하여 계정을 모니터링하고 비정상적 활동에 대 한 알림을 사용할 수 있습니다.

  - **로그인 시도의 수차례 실패**: 이 정책은 침해의 시도를 나타낼 수 있는 학습한 기준을 고려하여 단일 세션에서 수차례 로그인 활동에 실패하는 경우 사용자 환경을 프로파일링하고 알림을 트리거합니다.

  - **불가능한 이동**: 이 정책은 사용자 환경을 프로파일링하고 두 위치 사이의 예상 이동 시간 보다 짧은 기간에 여러 위치에 있는 같은 사용자의 다른 위치에서의 활동을 탐지하는 경우 알림을 트리거합니다. 이는 다른 사용자가 동일한 자격 증명을 사용 하고 있음을 의미할 수 있습니다. 이 비정상 동작의 탐지는 새 사용자의 활동 패턴을 학습하는 동안 초기 7일의 학습 기간을 필요로 합니다.

  - **비정상적 가장 활동(사용자)**: 이 정책은 침해의 시도를 나타낼 수 있는 학습한 기준을 고려하여 단일 세션에서 수차례 가장 활동을 수행하는 경우 사용자 환경을 프로파일링하고 알림을 트리거합니다.

- [Office 365 보안 점수](https://securescore.office.com/)와 같은 도구를 활용 하여 계정 보안의 구성과 동작을 관리합니다.

### <a name="second-keep-your-outlook-clients-current"></a>두 번째: Outlook 클라이언트를 최신 상태로 유지

완벽하게 업데이트되고 패치가 적용된 Outlook 2013과 2016은 "응용 프로그램 시작" 규칙/양식 작업은 기본적으로 사용하지 않도록 설정합니다. 이렇게 하면 공격자가 계정을 침해하더라도 규칙과 양식 작업이 차단됩니다. [Office 업데이트 설치](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5)단계를 따라 최신 업데이트 및 보안 패치를 설치할 수 있습니다.

다음은 Outlook 2013 및 2016 클라이언트용 패치 버전입니다.

- **Outlook 2016**: 16.0.4534.1001 이상.

- **Outlook 2013**: 15.0.4937.1000 이상.

개별 보안 패치에 대한 자세한 내용은 다음을 참조하세요.

- [Outlook 2016 보안 패치](https://support.microsoft.com/help/3191883)

- [Outlook 2013 보안 패치](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>세 번째: Outlook 클라이언트 모니터링

패치 및 업데이트가 설치되어 있더라도 공격자가 로컬 컴퓨터 구성을 변경하여 "응용 프로그램 시작" 동작을 다시 사용하도록 설정할 수 있습니다. [고급 그룹 정책 관리](https://docs.microsoft.com/microsoft-desktop-optimization-pack/agpm/)를 사용하여 클라이언트에서 로컬 컴퓨터 정책을 모니터링하고 적용할 수 있습니다.

[64 비트 버전의 Windows를 사용하여 시스템 레지스트리를 보는 방법](https://support.microsoft.com/help/305097)의 정보를 사용하여 "시작 응용 프로그램"이 레지스트리에 오버라이드를 통해 다시 사용하도록 설정되었는지 확인할 수 있습니다. 다음의 하위 키를 확인합니다:

- **Outlook 2016**: `HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**: `HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

EnableUnsafeClientMailRules 키를 찾습니다. 찾았고 1로 설정되어 있으면 Outlook 보안 패치가 오버라이드되었고 컴퓨터가 양식/규칙 공격에 취약합니다. 값이 0 이면 "응용 프로그램 시작" 작업을 사용할 수 없습니다. 업데이트되고 패치가 적용된 버전의 Outlook이 설치되었고 이 레지스트리 키가 없는 경우에는 시스템이 이러한 공격에 취약하지 않습니다.

온-프레미스 Exchange 설치를 사용하는 고객은 사용 가능한 패치가 없는 이전 버전의 Outlook을 차단하는 것이 좋습니다. 이 프로세스에 대한 자세한 내용은 [Outlook 클라이언트 차단 구성](https://docs.microsoft.com/exchange/configure-outlook-client-blocking-exchange-2013-help) 문서를 참조하세요.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>사이버 보안 프로그램과 같은 Microsoft 365 보안

Microsoft 365 구독에는 데이터 및 사용자를 보호하는 데 사용할 수 있는 강력한 보안 기능이 함께 제공됩니다. [Microsoft 365 보안 로드맵 - 최초 30일, 90일 및 그 이후의 최우선 순위](security-roadmap.md)를 사용하여 Microsoft에서 권장하는 Microsoft 365 테넌트 보안을 구현합니다.

- 처음 30일 이내에 수행 할 작업 이러한 작업들은 즉각적인 영향을 미치며 사용자에게 영향을 미치지 않습니다.

- 90일 이내에 수행해야 할 작업 이러한 작업들은 계획하고 구현하는 데 다소 시간이 걸리지만 보안 태세를 갖추는 데 큰 도움이 됩니다.

- 90일 초과 이러한 향상된 기능은 처음 90일간의 작업에서 구축됩니다.

## <a name="see-also"></a>참고 항목:

- 규칙 벡터에 대한 SilentBreak 보안 게시물 [악의적 Outlook 규칙](https://silentbreaksecurity.com/malicious-outlook-rules/)은 Outlook 규칙에 대한 자세한 검토를 제공합니다.

- Mailrule Pwnage에 대한 Sensepost 블로그 [HTTP 및 Mailrule Pwnage를 통한 MAPI](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/)는 Outlook 규칙을 통해 사서함을 이용하게 해주는 Ruler라는 도구에 대해 설명을 합니다.

- 양식 위협 벡터에 대한 Sensepost 블로그의 [Outlook 양식 및 셸](https://sensepost.com/blog/2017/outlook-forms-and-shells/)

- [Ruler 코드 베이스](https://github.com/sensepost/ruler)

- [Ruler 위험 노출 표시기](https://github.com/sensepost/notruler/blob/master/iocs.md)
