---
title: 게스트가 특정 그룹에 추가되지 않도록 방지
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: 게스트가 특정 그룹에 추가되지 않도록 하는 방법에 대해 자세히 알아보기
ms.openlocfilehash: 8bee26bf5ec323536ca1ac6f25ce96927634cee7
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49660051"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>게스트가 특정 Microsoft 365 그룹 또는 Microsoft Teams 팀에 추가되지 않도록 방지

대부분의 그룹 및 팀에 대한 게스트 액세스를 허용하지만 게스트 액세스를 차단하려는 경우 개별 그룹 및 팀에 대한 게스트 액세스를 차단할 수 있습니다. (팀에 대한 게스트 액세스 차단은 연결된 그룹에 대한 게스트 액세스를 차단하여 수행됩니다.) 이렇게 하면 새 게스트가 추가되지 않지만 그룹 또는 팀에 이미 있는 게스트는 제거되지 않습니다.

조직에서 민감도 레이블을 사용하는 경우 이를 사용하여 그룹 기준으로 게스트 액세스를 제어하는 것이 좋습니다. 이 작업을 하는 방법에 대한 자세한 내용은 민감도 레이블을 사용하여 [Microsoft Teams, Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)그룹 및 SharePoint 사이트의 콘텐츠를 보호합니다. 가능한 한 이 방법을 사용하는 것이 좋습니다.

## <a name="change-group-settings-using-microsoft-powershell"></a>Microsoft PowerShell을 사용하여 그룹 설정 변경

PowerShell을 사용하여 개별 그룹에 새 게스트를 추가하지 못하게 할 수도 있습니다. 팀의 연결된 SharePoint 사이트에는 별도의 게스트 공유 [컨트롤이 있습니다.](https://docs.microsoft.com/sharepoint/change-external-sharing-site)

Azure [Active Directory PowerShell for Graph(모듈](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) 이름 **AzureADPreview)의** 미리 보기 버전을 사용하여 그룹 수준 게스트 액세스 설정을 변경해야 합니다.

- 이전에 Azure AD PowerShell 모듈의 어떠한 버전도 설치하지 않은 경우 [Azure AD 모듈 설치](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview&preserve-view=true)를 참조하고 지침에 따라 공개 미리 보기 릴리스를 설치합니다.

- AzureAD(Azure AD PowerShell 모듈)의 2.0 일반 가용성 버전을 설치한 경우에는 PowerShell 세션에서 `Uninstall-Module AzureAD`를 실행하여 제거를 하고 `Install-Module AzureADPreview`를 실행하여 미리 보기 버전을 설치해야 합니다.

- 미리 보기 버전을 이미 설치한 경우에는 `Install-Module AzureADPreview`를 실행하여 이 모듈의 최신 버전인지 확인합니다.

> [!NOTE]
> 이러한 명령을 실행하려면 전역 관리자 권한이 있어야 합니다. 

다음 스크립트를 실행하여 게스트 액세스를 차단할 그룹의 이름으로 */<GroupName/>* 변경합니다.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

설정을 확인하려면 다음 명령을 실행합니다.

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

확인은 다음과 같습니다.
    
![게스트 그룹 액세스가 false로 설정되어 있는 PowerShell 창의 스크린샷.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)
  
## <a name="allow-or-block-guest-access-based-on-their-domain"></a>도메인에 따라 게스트 액세스 허용 또는 차단

특정 도메인을 사용하는 게스트를 허용하거나 차단할 수 있습니다. 예를 들어 비즈니스(Contoso)가 다른 비즈니스(Fabrikam)와 파트너 관계가 있는 경우 사용자가 그룹에 해당 게스트를 추가할 수 있도록 허용 목록에 Fabrikam을 추가할 수 있습니다.

자세한 내용은 특정 조직의 B2B 사용자에 대한 초대 허용 또는 [차단을 참조하세요.](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)

## <a name="add-guests-to-the-global-address-list"></a>전체 주소 목록에 게스트 추가

기본적으로 게스트는 Exchange 전체 주소 목록에 표시되지 않습니다. 아래에 나열된 단계를 사용하여 게스트를 전체 주소 목록에 표시

다음을 실행하여 게스트의 ObjectID를 찾을 수 있습니다.

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

그런 다음 ObjectID, GivenName, Surname, DisplayName 및 TelephoneNumber에 대한 적절한 값을 사용하여 다음을 실행합니다.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>관련 항목

[공동 작업 거버넌스 계획 단계별](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[공동 작업 거버넌스 계획 만들기](collaboration-governance-first.md)

[Microsoft 365 관리 센터에서 그룹 구성원 관리](https://docs.microsoft.com/microsoft-365/admin/create-groups/add-or-remove-members-from-groups)
  
[Azure Active Directory 액세스 검토](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser)
