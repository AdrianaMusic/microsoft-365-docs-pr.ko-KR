---
title: 게스트 및 외부 B2B 액세스를 허용하기 위한 ID 및 장치 액세스 정책 - 엔터프라이즈용 Microsoft 365 | Microsoft Docs
description: 게스트 및 외부 사용자의 액세스를 보호하기 위한 권장 조건부 액세스 및 관련 정책에 대해 설명
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.openlocfilehash: 376845d8e3657b91b9efe0357e94f4bec3a84078
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688288"
---
# <a name="policies-for-allowing-guest-and-external-b2b-access"></a>게스트 및 외부 B2B 액세스를 허용하는 정책

이 문서에서는 Azure AD(Azure Active Directory) B2B(Business-to-Business) 계정이 있는 게스트 및 외부 사용자에 대한 액세스를 허용하도록 권장되는 일반 ID 및 장치 액세스 정책을 조정하는 방법을 설명합니다. 이 지침은 공통 ID 및 장치 액세스 [정책을 빌드합니다.](identity-access-policies.md)

이러한 권장 사항은 보호의 기준 **계층에** 적용하도록 디자인됩니다. 그러나 중요하고 높은 규제 대상 보호에 대한 요구의 세분성에 따라 권장 **사항을** **조정할 수도** 있습니다.

B2B 계정이 Azure AD 테넌트에 인증하는 경로를 제공해도 이러한 계정에 전체 환경에 대한 액세스 권한이 부여되지는 않습니다. B2B 사용자 및 해당 계정은 조건부 액세스 정책에 부여된 서비스 내에서 공유되는 리소스(예: 파일)에만 액세스할 수 있습니다.

## <a name="updating-the-common-policies-to-allow-and-protect-guest-and-external-access"></a>게스트 및 외부 액세스를 허용하고 보호하기 위한 일반 정책 업데이트

다음 다이어그램은 Azure AD B2B 계정으로 게스트 및 외부 액세스를 보호하기 위해 공통 ID 및 장치 액세스 정책에서 추가하거나 업데이트할 정책을 보여 주며,

[![게스트 액세스 보호를 위한 정책 업데이트 요약](../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)

[이 이미지의 더 큰 버전 보기](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)

다음 표에는 만들고 업데이트해야 하는 정책이 나열되어 있습니다. 일반 정책은 일반 ID 및 장치 액세스 정책 문서의 관련 구성 [지침에 연결됩니다.](identity-access-policies.md)

|보호 수준|정책|추가 정보|
|---|---|---|
|**기준**|[게스트 및 외부 사용자에 대해 MFA가 항상 필요](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|이 새 정책을 만들고 구성합니다. <ul><li>Assignments > 사용자 및 > **포함,** 사용자 및 그룹 **선택,** 모든 게스트 및 외부 **사용자를 선택합니다.**</li><li>배정 **> 조건>** 로그인의 경우 항상 MFA(다단계 인증)를 적용하도록 모든 옵션을 선택하지 않은 상태로 하세요.</li></ul>|
||[로그인 위험이 중간 또는 높음인 경우 MFA *필요*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|게스트 및 외부 사용자를 제외하도록 이 정책을 수정합니다.|
||[호환 PC 필요](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|게스트 및 외부 사용자를 제외하도록 이 정책을 수정합니다.|

조건부 액세스 정책에서 게스트 및 외부 사용자를 포함하거나 제외하기 위해 **Assignments** > 사용자 및 그룹에 대해 포함 또는 제외> 모든 게스트 및 외부 사용자를 **검사합니다.**

![게스트 및 외부 사용자를 제외하는 컨트롤의 화면 캡처](../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png)

## <a name="more-information"></a>추가 정보

### <a name="guest-and-external-access-with-microsoft-teams"></a>Microsoft Teams를 통해 게스트 및 외부 액세스

Microsoft Teams는 다음을 정의합니다.

- **게스트 액세스는** 팀 구성원으로 추가할 수 있는 Azure AD B2B 계정을 사용하며 팀의 통신 및 리소스에 대한 모든 사용 권한이 부여됩니다.

- **외부 액세스는** B2B 계정이 없는 외부 사용자에 대한 것입니다. 외부 액세스에는 초대 및 통화, 채팅 및 모임 참가가 포함할 수 있지만 팀 구성원 자격 및 팀 리소스에 대한 액세스는 포함하지 않습니다.

자세한 내용은 팀에 대한 게스트와 외부 액세스 [간 비교를 참조하세요.](https://docs.microsoft.com/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access)

Teams의 ID 및 장치 액세스 정책 보안에 대한 자세한 내용은 [Teams 채팅,](teams-access-policies.md) 그룹 및 파일을 보호하기 위한 정책 권장 사항을 참조하세요.

### <a name="require-mfa-always-for-guest-and-external-users"></a>게스트 및 외부 사용자에 대해 MFA가 항상 필요

이 정책은 게스트가 홈 테넌트에 MFA에 등록되어 있는지 여부에 관계없이 테넌트에 MFA를 등록하라는 메시지를 제공합니다. 테넌트의 리소스에 액세스할 때 게스트 및 외부 사용자는 모든 요청에 대해 MFA를 사용해야 합니다.

### <a name="excluding-guest-and-external-users-from-risk-based-mfa"></a>위험 기반 MFA에서 게스트 및 외부 사용자 제외

조직에서는 Azure AD ID 보호를 사용하여 B2B 사용자에 대해 위험 기반 정책을 적용할 수 있는 반면, 홈 디렉터리에 기존 ID로 인해 리소스 디렉터리의 B2B 공동 작업 사용자에 대한 Azure AD ID 보호를 구현하는 데 제한이 있습니다. 이러한 제한으로 인해 Microsoft는 위험 기반 MFA 정책에서 게스트 사용자를 제외하고 이러한 사용자에게 항상 MFA를 사용하게 하는 것이 좋습니다.

자세한 내용은 B2B 공동 작업 사용자에 대한 ID 보호 제한 [사항을 참조하세요.](https://docs.microsoft.com/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users)

### <a name="excluding-guest-and-external-users-from-device-management"></a>장치 관리에서 게스트 및 외부 사용자 제외

한 조직만 장치를 관리할 수 있습니다. 게스트 및 외부 사용자를 장치 준수가 필요한 정책에서 제외하지 않는 경우 이러한 정책은 이러한 사용자를 차단합니다.

## <a name="next-step"></a>다음 단계

![4단계: Microsoft 365 클라우드 앱에 대한 정책](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

조건부 액세스 정책 구성:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
