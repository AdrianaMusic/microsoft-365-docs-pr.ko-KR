---
title: 아웃바운드 스팸 필터링 구성
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 관리자는 EOP(Exchange Online Protection)에서 아웃바운드 스팸 정책을 보고, 만들고, 수정하고, 삭제하는 방법을 배울 수 있습니다.
ms.openlocfilehash: 1e25d687ea22c70ba36f7c183b1fd8e578f7fa13
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49683334"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>EOP에서 아웃바운드 스팸 필터링 구성

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Exchange Online 사서함이 없는 Microsoft 365 조직 또는 Exchange Online 사서함이 없는 독립 실행형 EOP(Exchange Online Protection) 조직에서는 EOP를 통해 전송되는 아웃바운드 전자 메일 메시지에서 스팸 및 비정상적인 보내는 활동이 자동으로 확인됩니다.

조직의 사용자로부터의 아웃바운드 스팸은 일반적으로 손상된 계정을 나타냅니다. 의심스러운 아웃바운드 메시지는 스팸으로 표시되어(스팸 지수 또는 SCL에 상관없이) [](high-risk-delivery-pool-for-outbound-messages.md) 서비스의 신뢰도 보호를 위해 높은 위험 배달 풀을 통해 라우팅됩니다(즉, Microsoft 365 원본 전자 메일 서버를 IP 차단 목록에서 유지). 관리자는 경고 정책을 통해 의심스러운 아웃바운드 전자 메일 활동 및 차단된 사용자에게 자동으로 [알림을 제공합니다.](../../compliance/alert-policies.md)

EOP는 스팸에 대한 조직의 전반적인 방어의 일부로 아웃바운드 스팸 정책을 사용 합니다. 자세한 내용은 [스팸 방지 보호](anti-spam-protection.md)를 참조하세요.

관리자는 기본 아웃바운드 스팸 정책을 보고 편집하고 구성할 수 있지만 삭제할 수 없습니다. 세분성을 강화하기 위해 조직의 특정 사용자, 그룹 또는 도메인에 적용되는 사용자 지정 아웃바운드 스팸 정책을 만들 수도 있습니다. 사용자 지정 정책은 항상 기본 정책보다 우선하지만, 사용자 지정 정책의 우선순위(실행 순서)를 변경할 수 있습니다.

보안 및 준수 센터 또는 PowerShell(Exchange Online 사서함이 있는 Microsoft 365 조직용 Exchange Online PowerShell, Exchange Online 사서함이 없는 조직의 독립 실행형 EOP PowerShell)에서 아웃바운드 스팸 정책을 구성할 수 있습니다. &

EOP에서 아웃바운드 스팸 정책의 기본 요소는 다음입니다.

- **아웃바운드 스팸 필터 정책:** 아웃바운드 스팸 필터링 판정 및 알림 옵션에 대한 작업을 지정합니다.
- **아웃바운드 스팸 필터 규칙:** 아웃바운드 스팸 필터 정책에 대한 우선 순위 및 받는 사람 필터(정책이 적용되는 사람)를 지정합니다.

보안 및 준수 센터에서 아웃바운드 스팸 & 경우 이러한 두 요소의 차이는 명확하지 않습니다.

- 정책을 만들 때 실제로 둘 다에 대해 동일한 이름을 사용하여 아웃바운드 스팸 필터 규칙과 연결된 아웃바운드 스팸 필터 정책을 동시에 만드는 것입니다.
- 정책을 수정할 때 이름, 우선 순위, 사용 또는 사용하지 않도록 설정된 설정 및 받는 사람 필터와 관련된 설정은 아웃바운드 스팸 필터 규칙을 수정합니다. 다른 모든 설정은 연결된 아웃바운드 스팸 필터 정책을 수정합니다.
- 정책을 제거하면 아웃바운드 스팸 필터 규칙 및 연결된 아웃바운드 스팸 필터 정책이 제거됩니다.

Exchange Online PowerShell 또는 독립 실행형 EOP PowerShell에서 정책과 규칙을 개별적으로 관리합니다. 자세한 내용은 이 문서 부분의 Exchange Online PowerShell 또는 독립 실행형 [EOP PowerShell을](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) 사용하여 아웃바운드 스팸 정책 구성 섹션을 참조하세요.

모든 조직에는 다음 속성이 있는 Default라는 기본 제공 아웃바운드 스팸 정책이 있습니다.

- 정책과 연결된 아웃바운드 스팸 필터 규칙(받는 사람 필터)이 없는 경우에도 이 정책은 조직의 모든 받는 사람에게 적용됩니다.
- 정책의 사용자 지정 우선순위 값은 **가장 낮음** 이며 변경할 수 없습니다(이 정책은 항상 마지막으로 적용됨). 사용자가 만든 모든 사용자 지정 정책은 항상 기본 정책보다 우선합니다.
- 그 정책이 기본 정책(**IsDefault** 속성의 값은 `True`)이고, 기본 정책은 삭제할 수 없습니다.

아웃바운드 스팸 필터링의 효율성을 높이기 위해 특정 사용자 또는 사용자 그룹에 적용되는 더 엄격한 설정을 사용하여 사용자 지정 아웃바운드 스팸 정책을 만들 수 있습니다.

## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용은 무엇인가요?

- <https://protection.office.com/>에서 보안 및 준수 센터를 엽니다. **스팸 방지 설정** 페이지로 바로 이동하려면 <https://protection.office.com/antispam>을 사용하세요.

- Exchange Online PowerShell에 연결하려면 [Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)을 참조하세요. 독립 실행형 EOP PowerShell에 연결하려면 [Exchange Online Protection PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell)을 참조하세요.

- 이 문서의 절차를 수행하려면 먼저 보안 및 준수 센터에서 사용 권한을 받아야 합니다.
  - 아웃바운드 스팸 정책을 추가, 수정 및 삭제하려면 **조직** 관리 또는 보안 관리자 역할 그룹의 구성원이 **되거나** 삭제해야 합니다.
  - 아웃바운드 스팸 정책에 대한 읽기 전용 액세스 권한을  사용하려면 전역 읽기 사용자 또는 보안 읽기 권한이 있는 역할 그룹의 **구성원이** 되거나,

  자세한 내용은 [보안 및 준수 센터의 사용 권한](permissions-in-the-security-and-compliance-center.md)을 참조하세요.

  **참고**:

  - Microsoft 365 관리 센터의 해당 Azure Active Directory 역할에 사용자를 추가하면 사용자에게 보안 및 준수 센터에서 필요한 권한 _및_ Microsoft 365의 다른 기능에 대한 권한이 부여됩니다. 자세한 내용은 [관리자 역할 정보](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)를 참조하세요.
  - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups)의 **보기 전용 조직 관리** 역할 그룹에도 기능에 대한 읽기 전용 권한을 부여합니다.

- 아웃바운드 스팸 정책에 대한 권장 설정은 EOP 아웃바운드 스팸 필터 정책 설정을 [참조하세요.](recommended-settings-for-eop-and-office365-atp.md#eop-outbound-spam-policy-settings)

- 전자 [](../../compliance/alert-policies.md) 메일 보내기 제한이라는 기본 경고 정책, 검색된 의심스러운  전자 메일 전송 패턴 및 사용자가 이미 **TenantAdmins(전역** **관리자)** 그룹의 구성원에게 전자 메일 알림을 보내지 못하도록 제한되어 있으며 아웃바운드 스팸으로 인해 비정상적인 아웃바운드 전자 메일 활동 및 차단된 사용자에 대한 전자 메일 알림을 보내지 못하도록 제한되었습니다.  자세한 내용은 제한된 [사용자에 대한 경고 설정 확인을 참조하세요.](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users) 아웃바운드 스팸 정책의 알림 옵션 대신 이러한 경고 정책을 사용하는 것이 좋습니다.

## <a name="use-the-security--compliance-center-to-create-outbound-spam-policies"></a>보안 및 & 센터를 사용하여 아웃바운드 스팸 정책 만들기

Security & 준수 센터에서 사용자 지정 아웃바운드 스팸 정책을 만들면 스팸 필터 규칙과 연결된 스팸 필터 정책이 동시에 두 가지에 대해 동일한 이름을 사용하여 생성됩니다.

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 방지 **설정 페이지에서** 아웃바운드 정책 **만들기를 클릭합니다.**

3. **아웃바운드 스팸 필터 정책이** 열리면 플라이아웃에서 다음 설정을 구성합니다.

   - **이름**: 정책을 설명하는 고유한 이름을 입력합니다.

   - **설명**: 정책에 대한 선택적 설명을 입력합니다.

4. (선택 사항) 알림 **섹션을** 확장하여 의심스러운 아웃바운드 전자 메일 메시지의 복사본 및 알림을 수신해야 하는 추가 사용자를 구성합니다.

   - **의심스러운** 아웃바운드 전자 메일 메시지 복사본을 특정 사용자에게 보냅니다. 이 설정은 지정된 사용자를 의심스러운 아웃바운드 메시지에 Bcc 받는 사람으로 추가합니다.

     > [!NOTE]
     > 이 설정은 기본 아웃바운드 스팸 정책에서만 작동합니다. 만드는 사용자 지정 아웃바운드 스팸 정책에서는 작동하지 않습니다.

     이 설정을 사용하도록 설정하려면

     1. 설정을 사용하도록 설정하려면 확인란을 선택합니다.

     1. 사용자 **추가를 클릭합니다.** 받는 사람 **추가 또는 제거 플라이아웃에** 다음이 표시됩니다.

     1. 보낸 사람의 전자 메일 주소를 입력합니다. 전자 메일 주소가 여러 개인 경우 각 주소를 세미코론으로 구분하여 지정할 수 ;) 또는 한 줄에 받는 사람 한 명.

     1. 이 ![추가 아이콘](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) 을(를) 추가합니다.

        필요한 만큼 이 단계를 반복합니다.

        추가한 받는 사람은 플라이아웃의 받는 사람 **목록** 섹션에 표시됩니다. 받는 사람을 삭제하려면 제거 ![ 단추를 ](../../media/scc-remove-icon.png) 클릭합니다.

     1. 작업을 마쳤으면 **저장** 을 클릭합니다.

        이 설정을 사용하지 않도록 설정한 경우 확인란의 선택을 취소합니다.

   - **아웃바운드 스팸 전송으로** 인해 보낸 사람이 차단된 경우 특정 사용자에게 알릴 수 있습니다.

     > [!IMPORTANT]
     >
     > - 이 설정은 아웃바운드 스팸 정책에서 사용되지 않습니다.
     >
     > - 전자 [메일을](../../compliance/alert-policies.md) 보내지 않는 **사용자** 제한이라는 기본 경고 정책은 사용자가 받는 사람 제한 섹션의 제한을 초과하여 차단된 경우 **TenantAdmins(전역** **관리자)** 그룹의 구성원에게 이미 전자 메일 알림을 보냅니다.  아웃바운드 스팸 정책에서 이 설정 대신 경고 정책을 사용하여 관리자 및 기타 사용자에게 **알리는 것이 좋습니다.** 자세한 내용은 제한된 [사용자에 대한 경고 설정 확인을 참조하세요.](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users)

5. (선택 사항) 받는 사람 제한 **섹션을 확장하여** 의심스러운 아웃바운드 전자 메일 메시지에 대한 제한 및 작업을 구성합니다.

   > [!NOTE]
   > 이러한 설정은 클라우드 기반 사서함에만 적용됩니다.

   - **사용자당 최대 받는 사람 수**

     유효한 값은 0에서 10000까지입니다. 기본값은 0으로, 서비스 기본값이 사용됩니다. 자세한 내용은 보내기 [제한을 참조하세요.](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1)

     - **외부 시간 제한:** 시간당 최대 외부 받는 사람 수입니다.

     - **내부 시간 제한:** 시간당 최대 내부 받는 사람 수입니다.

     - **일별 제한:** 일별 최대 받는 사람 수입니다.

   - **사용자가 위의** 제한을 초과하는 경우의 작업: 받는 사람 제한  중 하나를 초과할 때 수행하도록 작업을 구성합니다. 모든 작업에 대해 사용자에 지정된  받는 사람이 전자 메일 경고 정책을 보내지  못하도록 제한했습니다(그리고 아웃바운드 스팸 정책의 아웃바운드 스팸 설정으로 인해 보낸 사람이 차단된 경우 현재 중복된 특정 사용자에게 알림).

     - **다음 날까지** 사용자가 메일을 보내지 못하도록 제한합니다. 이 값은 기본값입니다. 전자 메일 알림이 전송됩니다. 사용자는 UTC 시간을 기준으로 다음 날까지 더 이상 메시지를 보낼 수 없습니다. 관리자가 이 블록을 다시 정할 수 있는 방법은 없습니다.

       - 전자 메일을 보내지 못하도록 제한된 **User라는** 활동 경고는 전자 메일을 통해 관리자에게 알림(전자 메일 및 알림 보기 **페이지)에 표시됩니다.**

       - 정책에서 아웃바운드 스팸 설정으로 인해 보낸 사람이 차단된 경우 특정 사용자에게 알림에 지정된 모든 받는 사람도 알림을 보냅니다. 

       - 사용자는 UTC 시간을 기준으로 다음 날까지 더 이상 메시지를 보낼 수 없습니다. 관리자가 이 블록을 다시 정할 수 있는 방법은 없습니다.

     - 사용자가 메일을 보내지 못하도록 **제한:** 전자 메일 알림이 전송되고, 사용자가 보안 & 준수 센터의 **[제한된 사용자] <https://sip.protection.office.com/restrictedusers>** 포털에 추가되고,  관리자가 제한된 사용자 포털에서 전자 메일을 제거할 때까지 전자 메일을 보낼 수 없습니다. 관리자가 목록에서 사용자를 제거하면 해당 일에 대해 사용자가 다시 제한되지 않습니다. 자세한 내용은 스팸 메일을 전송한 후 제한된 사용자 포털에서 [사용자 제거를 참조하세요.](removing-user-from-restricted-users-portal-after-spam.md)

     - **작업 없음, 알림만:** 전자 메일 알림이 전송됩니다.

6. (선택 사항) 자동 **전달 섹션을 확장하여** 사용자가 외부 보낸 사람에 대한 자동 전자 메일 전달을 제어합니다. 자세한 내용은 [Microsoft 365에서](external-email-forwarding.md)자동 외부 전자 메일 전달 제어를 참조하세요.

   > [!NOTE]
   >
   > - 2020년 9월 전에는 이러한 설정을 사용할 수 있지만 적용되지는 않습니다.
   >
   > - 이러한 설정은 클라우드 기반 사서함에만 적용됩니다.
   >
   > - 자동 전달을 사용하지 않도록 설정하면 외부 보낸 사람이 전달이 있는 사서함으로 전자 메일을 보내는 경우 받는 사람은 배달 못함 보고서(NDR 또는 반송 메시지라고도함)를 받게 됩니다. 내부 보낸 사람이 메시지를 보내고  전달 방법이 사서함 [](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) _전달(SMTP_ 전달)인 경우 내부 보낸 사람이 NDR을 얻습니다. 받은 편지함 규칙으로 인해 전달이 발생한 경우 내부 보낸 사람이 NDR을 얻지 못합니다.

   사용 가능한 값은 다음과 같습니다.

   - **자동 - 시스템 제어**: 아웃바운드 스팸 필터링이 자동 외부 전자 메일 전달을 제어할 수 있습니다. 이 값은 기본값입니다.
   - **On**: 자동 외부 전자 메일 전달이 정책에 의해 사용하지 않도록 설정되지 않습니다.
   - **해제:** 정책에 의해 모든 자동 외부 전자 메일 전달이 사용하지 않도록 설정됩니다.

7. (필수) 적용된 **섹션을** 확장하여 정책이 적용되는 내부 보낸 사람 식별

    조건이나 예외는 한 번만 사용할 수 있지만, 조건이나 예외에 대한 값을 여러 개 지정할 수 있습니다. 동일한 조건의 여러 값이나 예외는 OR 논리를 사용합니다(예: _\<sender1\>_ 혹은 _\<sender2\>_). 다양한 조건이나 예외는 AND 논리를 사용합니다(예: _\<sender1\>_ 및 _\<member of group 1\>_).

    사용 가능한 모든 조건을 보려면 **조건 추가** 를 세 번 클릭하는 것이 가장 쉽습니다. ![제거 단추](../../media/scc-remove-icon.png)를 클릭하여 구성하지 않을 조건을 제거할 수 있습니다.

    - **보낸 사람 도메인**: 조직에서 구성된 허용 도메인 중 하나 이상에서 보낸 사람 지정 **태그 추가** 상자를 클릭하여 도메인을 확인하고 선택합니다. 두 개 이상의 도메인을 사용할 수 있는 경우, **태그 추가** 상자를 다시 클릭하여 추가 도메인을 선택합니다.

    - **보낸 사람 :** 조직에서 하나 이상의 사용자를 지정합니다. **태그 추가** 를 클릭하고, 입력을 시작하여 목록을 필터링합니다. 태그 추가 **상자를 다시** 클릭하여 보낸 사람 추가를 선택합니다.

    - **보낸 사람이 다음의** 구성원입니다. 조직에서 하나 이상의 그룹을 지정합니다. **태그 추가** 를 클릭하고, 입력을 시작하여 목록을 필터링합니다. 태그 추가 **상자를 다시** 클릭하여 보낸 사람 추가를 선택합니다.

    - **다음의 경우 제외**: 규칙에 대한 예외를 추가하려면 **조건 추가** 를 세 번 클릭하여 사용 가능한 모든 예외를 표시합니다. 설정 및 동작은 조건과 정확히 같습니다.

8. 작업을 마쳤으면 **저장** 을 클릭합니다.

## <a name="use-the-security--compliance-center-to-view-outbound-spam-policies"></a>보안 및 & 센터를 사용하여 아웃바운드 스팸 정책 보기

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 방지 **설정 페이지에서** 확장 아이콘을 클릭하여 아웃바운드 스팸 ![ 정책을 ](../../media/scc-expand-icon.png) 확장합니다.

   - 아웃바운드 스팸 필터 정책이라는 기본 **정책입니다.**

   - 유형 열의 값이 사용자 지정  아웃바운드 스팸 정책인 경우 만든 사용자 지정 **정책입니다.**

3. 정책 설정이 표시되는 확장된 정책 세부 정보에서 표시되거나 정책 편집을 **클릭할 수 있습니다.**

## <a name="use-the-security--compliance-center-to-modify-outbound-spam-policies"></a>보안 및 & 센터를 사용하여 아웃바운드 스팸 정책 수정

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 방지 **설정 페이지에서** 확장 아이콘을 클릭하여 아웃바운드 스팸 ![ 정책을 ](../../media/scc-expand-icon.png) 확장합니다.

   - 아웃바운드 스팸 필터 정책이라는 기본 **정책입니다.**

   - 유형 열의 값이 사용자 지정  아웃바운드 스팸 정책인 경우 만든 사용자 지정 **정책입니다.**

3. **정책 편집** 을 클릭합니다.

사용자 지정 아웃바운드 스팸 정책의 경우 플라이아웃에 나타나는 사용 가능한 설정은 보안 및 준수 센터를 사용하여 [아웃바운드](#use-the-security--compliance-center-to-create-outbound-spam-policies) 스팸 정책 & 섹션에 설명된 설정과 동일합니다.

아웃바운드 스팸 필터 정책이라는 기본 아웃바운드 스팸 정책의 경우 적용된 섹션을 사용할 수 없습니다(정책은 모든 사용자에 적용), 정책의 이름을 바을 수 없습니다. 

정책을 사용하거나 사용하지 않도록 설정하거나, 정책 우선순위 순서를 설정하거나, 최종 사용자 격리 알림을 구성하려면, 다음 섹션을 참조하세요.

### <a name="enable-or-disable-outbound-spam-policies"></a>아웃바운드 스팸 정책 사용 또는 사용 안 하도록 설정

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 **방지** 설정 페이지에서 확장 아이콘을 클릭하여 만든 사용자 지정 정책을 확장합니다(유형 열의 값은 사용자 지정 아웃바운드 ![ 스팸 ](../../media/scc-expand-icon.png)  **정책).**

3. 표시되는 확장된 정책 세부 정보에서 **켬** 열에 있는 값을 확인합니다.

   토글을 왼쪽으로 이동하여 정책을 사용하지 않도록 설정합니다. ![토글 끔](../../media/scc-toggle-off.png)

   토글을 오른쪽으로 이동하여 정책을 사용하도록 설정합니다. ![토글 켬](../../media/scc-toggle-on.png)

기본 아웃바운드 스팸 정책은 사용하지 않도록 설정할 수 없습니다.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>사용자 지정 아웃바운드 스팸 정책의 우선 순위 설정

기본적으로 아웃바운드 스팸 정책에는 만들어진 순서에 따라 우선 순위가 부여됩니다(새 정책은 이전 정책보다 우선 순위가 낮음). 낮은 우선순위 번호는 정책의 높은 우선순위(0이 가장 높음)를 나타내고 정책은 우선순위 순서에 따라 처리됩니다(높은 우선순위 정책은 낮은 우선순위 정책보다 먼저 처리됨). 두 정책의 우선순위는 동일 할 수 없으며, 첫 번째 정책이 적용된 후에는 정책 처리가 중지됩니다.

사용자 지정 아웃바운드 스팸 정책은 처리되는 순서대로 표시됩니다(첫 번째 정책의 우선 순위 값은 0).  아웃바운드 스팸  필터 정책이라는 기본 아웃바운드 스팸 정책의 우선 순위 값은 **가장** 낮습니다. 이 정책은 변경할 수 없습니다.

정책의 우선순위를 변경하려면 목록에서 정책을 위나 아래로 이동합니다. 보안 및 준수 센터에서 **우선순위** 번호를 직접 수정할 수는 없습니다.

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 방지 **설정** 페이지에서 유형 열의 값이 사용자  지정 아웃바운드 스팸 정책인 **정책을 확인합니다.** **우선순위** 열의 값을 확인합니다.

   - 우선 순위가 가장 높은 사용자 지정 아웃바운드 스팸 정책의 값은 ![ 아래쪽 화살표 아이콘 ](../../media/ITPro-EAC-DownArrowIcon.png) **0입니다.**

   - 우선 순위가 가장 낮은 사용자 지정 아웃바운드 스팸 정책의 값은 위쪽 화살표 아이콘 ![ ](../../media/ITPro-EAC-UpArrowIcon.png) **n(예:** ![ 위쪽 화살표 아이콘 ](../../media/ITPro-EAC-UpArrowIcon.png) **3)입니다.**

   - 사용자 지정 아웃바운드 스팸 정책이 세 개 이상 있는 경우 가장 높은 우선 순위와 가장 낮은 우선 순위 사이의 정책에는 위쪽 화살표 아이콘 아래쪽 화살표 아이콘 n(예: 위쪽 화살표 아이콘 아래쪽 화살표 아이콘 ![ ](../../media/ITPro-EAC-UpArrowIcon.png)![ ](../../media/ITPro-EAC-DownArrowIcon.png)  ![ ](../../media/ITPro-EAC-UpArrowIcon.png)![ ](../../media/ITPro-EAC-DownArrowIcon.png) **2)이** 있습니다.

3. 이 ![위쪽 화살표 아이콘](../../media/ITPro-EAC-UpArrowIcon.png) 또는 ![아래쪽 화살표 아이콘](../../media/ITPro-EAC-DownArrowIcon.png) 을 선택합니다.

## <a name="use-the-security--compliance-center-to-remove-outbound-spam-policies"></a>보안 및 & 센터를 사용하여 아웃바운드 스팸 정책 제거

1. 보안 및 준수 센터에서 **위협 관리** \> **정책** \> **스팸 방지** 로 이동합니다.

2. 스팸 **방지** 설정 페이지에서 확장 아이콘을 클릭하여 삭제할 사용자 지정 정책을 확장합니다(유형 열은 사용자 지정 아웃바운드 ![ 스팸 ](../../media/scc-expand-icon.png)  **정책).**

3. 표시되는 확장된 정책 세부 정보에서 **정책 삭제** 를 클릭합니다.

4. 표시되는 경고 대화 상자에서 **예** 를 클릭합니다.

기본 정책은 제거할 수 없습니다.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Exchange Online PowerShell 또는 독립 실행형 EOP PowerShell을 사용하여 아웃바운드 스팸 정책 구성

앞서 설명한 바와 같이 아웃바운드 스팸 정책은 아웃바운드 스팸 필터 정책과 아웃바운드 스팸 필터 규칙으로 구성됩니다.

Exchange Online PowerShell 또는 독립 실행형 EOP PowerShell에서는 아웃바운드 스팸 필터 정책과 아웃바운드 스팸 필터 규칙의 차이점이 분명합니다. **\* -HostedOutboundSpamFilterPolicy** cmdlet을 사용하여 아웃바운드 스팸 필터 정책을 관리하고 **\* -HostedOutboundSpamFilterRule** cmdlet을 사용하여 아웃바운드 스팸 필터 규칙을 관리합니다.

- PowerShell에서 먼저 아웃바운드 스팸 필터 정책을 만든 다음 규칙이 적용되는 정책을 식별하는 아웃바운드 스팸 필터 규칙을 생성합니다.
- PowerShell에서는 아웃바운드 스팸 필터 정책 및 아웃바운드 스팸 필터 규칙의 설정을 별도로 수정합니다.
- PowerShell에서 아웃바운드 스팸 필터 정책을 제거하면 해당 아웃바운드 스팸 필터 규칙이 자동으로 제거되지는 않습니다.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>PowerShell을 사용하여 아웃바운드 스팸 정책 만들기

PowerShell에서 아웃바운드 스팸 정책을 만드는 과정은 다음 두 단계로 진행됩니다.

1. 아웃바운드 스팸 필터 정책을 만들 수 있습니다.
2. 규칙이 적용되는 아웃바운드 스팸 필터 정책을 지정하는 아웃바운드 스팸 필터 규칙을 생성합니다.

 **참고:**

- 새 아웃바운드 스팸 필터 규칙을 만들고 기존의 통합되지 않은 아웃바운드 스팸 필터 정책을 할당할 수 있습니다. 아웃바운드 스팸 필터 규칙은 두 개 이상의 아웃바운드 스팸 필터 정책과 연결될 수 없습니다.

- 정책을 만든 후 보안 및 준수 센터에서 사용할 수 없는 PowerShell의 새 아웃바운드 스팸 필터 정책에 대해 다음 설정을 구성할 & 있습니다.

  - 새 정책을 사용할 수 `$false` **없습니다(New-HostedOutboundSpamFilterRule** cmdlet에서 사용).
  -  _\<Number\>_ **New-HostedOutboundSpamFilterRule** cmdlet에서 만들기 중 정책의 우선 순위(우선 순위)를 설정합니다.

- PowerShell에서 만든 새 아웃바운드 스팸 필터 정책은 스팸 필터 규칙에 정책을 할당할 때까지 보안 & 준수 센터에 표시되지 않습니다.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>1단계: PowerShell을 사용하여 아웃바운드 스팸 필터 정책 만들기

아웃바운드 스팸 필터 정책을 만들 경우 다음 구문을 사용 합니다.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

이 예에서는 다음 설정을 사용하여 Contoso Executives라는 새 아웃바운드 스팸 필터 정책을 만듭니다.

- 받는 사람 비율 제한은 기본값인 더 작은 값으로 제한됩니다. 자세한 내용은 [Microsoft 365 옵션 전반에 걸쳐 전송 제한을 참조하세요.](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options)

- 제한 중 하나에 도달하면 사용자가 메시지를 보낼 수 없습니다.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

구문과 매개 변수에 대한 자세한 내용은 [New-HostedOutboundSpamFilterPolicy를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/new-hostedoutboundspamfilterpolicy)

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>2단계: PowerShell을 사용하여 아웃바운드 스팸 필터 규칙 만들기

아웃바운드 스팸 필터 규칙을 만들 경우 다음 구문을 사용 합니다.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

이 예에서는 다음 설정을 사용하여 Contoso Executives라는 새 아웃바운드 스팸 필터 규칙을 만듭니다.

- Contoso Executives라는 아웃바운드 스팸 필터 정책은 규칙과 연결됩니다.

- 이 규칙은 Contoso Executives라는 그룹의 구성원에게 적용됩니다.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

구문과 매개 변수에 대한 자세한 내용은 [New-HostedOutboundSpamFilterRule을 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/new-hostedoutboundspamfilterrule)

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 정책 보기

모든 아웃바운드 스팸 필터 정책의 요약 목록을 반환하기 위해 다음 명령을 실행합니다.

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

특정 아웃바운드 스팸 필터 정책에 대한 자세한 정보를 반환하기 위해 다음 구문을 사용하세요.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

이 예에서는 Executives라는 아웃바운드 스팸 필터 정책의 모든 속성 값을 반환합니다.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

구문과 매개 변수에 대한 자세한 내용은 [Get-HostedOutboundSpamFilterPolicy를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/get-hostedoutboundspamfilterpolicy)

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 규칙 보기

기존 아웃바운드 스팸 필터 규칙을 표시하기 위해 다음 구문을 사용 합니다.

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

모든 아웃바운드 스팸 필터 규칙의 요약 목록을 반환하기 위해 다음 명령을 실행합니다.

```PowerShell
Get-HostedOutboundSpamFilterRule
```

활성화된 또는 비활성화된 규칙을 기준으로 목록을 필터링하려면 다음 명령을 실행합니다.

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

특정 아웃바운드 스팸 필터 규칙에 대한 자세한 정보를 반환하기 위해 다음 구문을 사용하세요.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

이 예에서는 Contoso Executives라는 아웃바운드 스팸 필터 규칙의 모든 속성 값을 반환합니다.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

구문과 매개 변수에 대한 자세한 내용은 [Get-HostedOutboundSpamFilterRule을 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/get-hostedoutboundspamfilterrule)

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 정책 수정

PowerShell에서 맬웨어 필터 정책을 수정할 때와 이 문서 앞부분의 [1단계: PowerShell을](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) 사용하여 아웃바운드 스팸 필터 정책 섹션을 만들 때와 동일한 설정을 사용할 수 있습니다.

> [!NOTE]
> 아웃바운드 스팸 필터 정책의 이름을 바울 수 **없습니다(Set-HostedOutboundSpamFilterPolicy** cmdlet에는 _Name_ 매개 변수가 없음). 보안 및 준수 센터에서 아웃바운드 스팸 정책의 이름을 & 아웃바운드 스팸 필터 규칙의 이름만 _바)_

아웃바운드 스팸 필터 정책을 수정하려면 다음 구문을 사용 합니다.

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

구문과 매개 변수에 대한 자세한 내용은 [Set-HostedOutboundSpamFilterPolicy를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/set-hostedoutboundspamfilterpolicy)

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 규칙 수정

PowerShell에서 아웃바운드 스팸 필터 규칙을 수정할 때 사용할 수 없는 설정은 _사용되지_ 않는 규칙을 만들 수 있는 Enabled 매개 변수뿐입니다. 기존 아웃바운드 스팸 필터 규칙을 사용하도록 설정하거나 사용하지 않도록 설정하려면 다음 섹션을 참조하세요.

그렇지 않으면 PowerShell에서 아웃바운드 스팸 필터 규칙을 수정할 때 추가 설정을 사용할 수 없습니다. [2단계: PowerShell을](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) 사용하여 이 문서 앞부분의 아웃바운드 스팸 필터 규칙 섹션을 만드는 2단계에서 설명한 대로 규칙을 만들 때도 동일한 설정을 사용할 수 있습니다.

아웃바운드 스팸 필터 규칙을 수정하려면 다음 구문을 사용 합니다.

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

구문과 매개 변수에 대한 자세한 내용은 [Set-HostedOutboundSpamFilterRule을 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/set-hostedoutboundspamfilterrule)

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 규칙을 활성화 또는 비활성화

PowerShell에서 아웃바운드 스팸 필터 규칙을 사용하도록 설정하거나 사용하지 않도록 설정하면 전체 아웃바운드 스팸 정책(아웃바운드 스팸 필터 규칙 및 할당된 아웃바운드 스팸 필터 정책)이 사용 또는 사용되지 않도록 설정됩니다. 기본 아웃바운드 스팸 정책은 활성화하거나 사용하지 않도록 설정할 수 없습니다(항상 모든 받는 사람에게 적용).

PowerShell에서 아웃바운드 스팸 필터 규칙을 사용하도록 설정하거나 사용하지 않도록 설정하려면 다음 구문을 사용 합니다.

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

이 예에서는 Marketing Department라는 아웃바운드 스팸 필터 규칙을 사용하지 않도록 설정합니다.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

다음은 동일한 규칙을 사용하도록 설정하는 예제입니다.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

구문과 매개 변수에 대한 자세한 내용은 [Enable-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/enable-hostedoutboundspamfilterrule) 및 [Disable-HostedOutboundSpamFilterRule을 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/disable-hostedoutboundspamfilterrule)

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 규칙의 우선 순위 설정

규칙에 설정 가능한 가장 높은 우선 순위 값은 0입니다. 설정할 수 있는 가장 낮은 값은 규칙 수에 따라 달라집니다. 예를 들어 규칙이 5개 있는 경우, 우선순위 값 0~4를 사용할 수 있습니다. 기존 규칙의 우선순위를 변경하면 다른 규칙에 계단식 효과를 줄 수 있습니다. 예를 들어 사용자 지정 규칙 5개(우선순위: 0~4)가 있고 규칙의 우선순위를 2로 변경하면, 우선순위 2인 기존 규칙이 우선순위 3으로 변경되고, 우선순위 3인 규칙이 우선순위 4로 변경됩니다.

PowerShell에서 아웃바운드 스팸 필터 규칙의 우선 순위를 설정하기 위해 다음 구문을 사용 합니다.

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

다음은 Marketing Department라는 규칙의 우선순위를 2로 설정하는 예제입니다. 우선순위가 2 이하인 모든 기존 규칙은 1씩 감소합니다(우선순위 번호는 1씩 증가함).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
>
> - 새 규칙을 만들 때 새 규칙의 우선  순위를 설정하기 위해 **New-HostedOutboundSpamFilterRule** cmdlet에서 Priority 매개 변수를 대신 사용합니다.
>
> - 아웃바운드 기본 스팸 필터 정책에는 해당하는 스팸 필터 규칙이 없습니다. 항상 이 정책의 우선 순위 값이 **가장 낮습니다.**

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 정책 제거

PowerShell을 사용하여 아웃바운드 스팸 필터 정책을 제거하면 해당 아웃바운드 스팸 필터 규칙이 제거되지 않습니다.

PowerShell에서 아웃바운드 스팸 필터 정책을 제거하려면 다음 구문을 사용 합니다.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

이 예에서는 Marketing Department라는 아웃바운드 스팸 필터 정책을 제거합니다.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

구문과 매개 변수에 대한 자세한 내용은 [Remove-HostedOutboundSpamFilterPolicy를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy)

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>PowerShell을 사용하여 아웃바운드 스팸 필터 규칙 제거

PowerShell을 사용하여 아웃바운드 스팸 필터 규칙을 제거하면 해당 아웃바운드 스팸 필터 정책이 제거되지 않습니다.

PowerShell에서 아웃바운드 스팸 필터 규칙을 제거하려면 다음 구문을 사용 합니다.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

이 예에서는 Marketing Department라는 아웃바운드 스팸 필터 규칙을 제거합니다.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

구문과 매개 변수에 대한 자세한 내용은 [Remove-HostedOutboundSpamFilterRule을 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/remove-hostedoutboundspamfilterrule)

## <a name="for-more-information"></a>자세한 내용

[제한된 사용자 포털에서 차단된 사용자 제거](removing-user-from-restricted-users-portal-after-spam.md)

[아웃바운드 메시지용 높은 위험 배달 풀](high-risk-delivery-pool-for-outbound-messages.md)

[스팸 방지 및 보호 FAQ](anti-spam-protection-faq.md)

[자동 전달 메시지 보고서](mfi-auto-forwarded-messages-report.md)
