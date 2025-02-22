---
title: 중요한 데이터를 보호하는 팀 구성하기
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
description: 중요한 데이터를 보호하는 팀을 배치하는 방법에 대해 알아봅니다.
ms.openlocfilehash: ad1cf437bdbe3bd7b25347bb49698314097462ab
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49612955"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>중요한 데이터를 보호하는 팀 구성하기

이 문서에서는 중요한 수준의 보호를 위해 팀을 설정하는 방법을 살펴보겠습니다. 이 문서의 단계를 수행하기 전에 [기준 보호를 사용하여 팀 배치하기](configure-teams-baseline-protection.md) 단계를 완료해야 합니다. 중요 계층에서는 초기 계층에 대한 다음과 같은 추가 보호를 제공합니다.

- 게스트 공유를 설정하거나 해제하고 관리되지 않는 장치의 SharePoint 콘텐츠에 대한 액세스를 웹 전용으로 제한하는 팀의 민감도 레이블입니다. 이 레이블은 파일을 분류하는 데도 사용할 수 있습니다.
- 더욱 제한적인 기본 공유 링크 유형
- 팀 소유자만 비공개 채널을 만들 수 있습니다.

## <a name="guest-sharing"></a>게스트 공유

업무 특성에 따라 중요한 데이터를 포함하는 팀에서 게스트 공유 기능을 사용하거나 사용하지 않을 수 있습니다. 팀에서 조직 외부의 사용자와 공동 작업을 수행하려는 경우에는 게스트 공유를 사용하는 것이 좋습니다. Microsoft 365에는 중요한 콘텐츠를 안전하게 공유하는 데 도움이 되는 다양한 보안 및 규정 준수 기능이 포함되어 있습니다. 이는 일반적으로 콘텐츠를 직접 조직 외부의 사용자에게 전자 메일로 보내는 것보다 안전합니다.

게스트와 안전하게 공유하는 방법에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [파일을 조직 외부의 사람들과 공유할 때 실수로 발생하는 정보 노출 제한하기](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure)
- [보안 게스트 공유 환경 만들기](https://docs.microsoft.com/microsoft-365/solutions/create-secure-guest-sharing-environment)

게스트 공유를 허용하거나 차단하기 위해 나중에 설명할 팀의 민감도 레이블과 연결된 SharePoint 사이트의 사이트 수준 공유 제어를 조합해서 사용합니다.

## <a name="sensitivity-labels"></a>민감도 레이블

중요한 수준의 보호를 위해서는 팀을 분류하는 데 민감도 레이블을 사용합니다. 이 레이블은 이 파일이나 다른 팀 또는 SharePoint나 OneDrive와 같은 다른 파일 위치의 개별 파일을 분류하는 데도 사용할 수 있습니다. 

첫 번째 단계로 Teams에서 민감도 레이블을 사용하도록 설정해야 합니다. 자세한 내용은 [Microsoft Teams, Office 365 그룹 및 SharePoint 사이트에서 민감도 레이블 사용하여 콘텐츠 보호하기](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)를 참조하세요.

조직에 이미 민감도 레이블을 배포한 경우 이 레이블이 전체 레이블 전략에 어떻게 적합한지 고려하세요. 조직의 요구 사항을 충족하는 데 필요한 경우 이름이나 설정을 변경할 수 있습니다.

Teams에서 민감도 레이블을 사용하도록 설정한 후 다음 단계는 레이블을 만드는 것입니다.

민감도 레이블을 만들려면
1. [Microsoft 365 규정 준수 센터](https://compliance.microsoft.com)를 엽니다.
2. **솔루션** 에서 **정보 보호** 를 클릭합니다.
3. **레이블 만들기** 를 클릭합니다.
4. 레이블에 이름을 지정합니다. **중요** 로 설정하는 것이 좋지만, 이미 사용 중인 다른 이름을 선택할 수도 있습니다.
5. 도구 설명을 추가한 다음 **다음** 을 클릭합니다.
6. **암호화** 페이지에서 **다음** 을 클릭합니다.
7. 이 레이블로 분류된 파일에 머리글, 바닥글 또는 워터마크를 자동으로 추가하려는 경우 콘텐츠 표시 페이지에서 **콘텐츠 표시** 를 설정합니다.
8. **사이트 및 그룹 설정** 페이지에서 **사이트 및 그룹 설정** 을 **켜짐** 으로 설정합니다.
9. **Office 365 그룹에 연결된 팀 사이트의 개인 정보 보호** 드롭다운에서 **비공개 - 구성원만 사이트에 액세스할 수 있음** 을 선택합니다.
10. 게스트 액세스를 허용하려면 **Office 365 그룹 소유자가 조직 외부의 사용자를 그룹에 추가할 수 있도록 허용** 확인란을 선택합니다. 
11. **관리 되지 않는 장치** 에서 **제한된 웹 전용 액세스를 허용** 을 선택합니다.
12. **다음** 을 클릭합니다.
13. **Office 앱에 대한 자동 레이블 지정** 페이지에서 **다음** 을 클릭합니다.
14. **제출** 을 클릭한 다음 **완료** 를 클릭합니다.

레이블을 만든 후에는 레이블을 사용할 사용자에게 게시해야 합니다. 민감한 보호를 위해 모든 사용자가 레이블을 사용할 수 있도록 합니다. Microsoft 365 규정 준수 센터에서 **정보 보호** 페이지의 **레이블 정책** 탭에서 레이블을 게시합니다. 모든 사용자에게 적용되는 기존 정책이 있다면 해당 정책에 이 레이블을 추가합니다. 새 정책을 만들어야 한다면 [레이블 정책을 만들어 민감도 레이블 게시하기](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy)를 참조하세요.

## <a name="create-a-team"></a>팀 만들기

중요한 시나리오의 추가 구성은 팀과 연결된 SharePoint 사이트에서 수행되므로 다음 단계는 팀을 만드는 것입니다.

중요한 정보를 위해 팀을 만들려면
1. Teams에서 앱 왼쪽에 있는 **Teams** 를 클릭한 다음, 팀 목록 아래에서 **팀 참가 또는 만들기** 를 클릭합니다.
2. **팀 만들기** 를 클릭합니다(첫 번째 카드, 왼쪽 위 모서리).
3. **처음부터 팀 만들기** 를 선택합니다.
4. **민감도** 목록에서 방금 만든 **중요** 레이블을 선택합니다.
5. **개인 정보 보호** 에서 **비공개** 를 클릭합니다.
6. 팀 이름을 입력한 다음 **만들기** 를 클릭합니다.
7. 팀에 사용자를 추가한 다음 **닫기** 를 클릭합니다.

## <a name="private-channel-settings"></a>비공개 채널 설정

이 계층에서는 비공개 채널 만들기를 팀 소유자로 제한합니다.

비공개 채널 만들기를 제한하려면
1. 팀에서 **추가 옵션** 을 클릭한 다음 **팀 관리** 를 클릭합니다.
2. **설정** 탭에서 **구성원 사용 권한** 을 확장합니다.
3. **구성원이 비공개 채널을 만들 수 있도록 허용** 확인란을 선택 취소합니다.

[팀 정책](https://docs.microsoft.com/MicrosoftTeams/teams-policies)을 사용하여 비공개 채널을 만들 수 있는 사용자를 제어할 수도 있습니다.

## <a name="sharepoint-settings"></a>SharePoint 설정

중요 레이블을 사용하여 새 팀을 만들 때마다 SharePoint에서 다음 두 단계를 수행해야 합니다.

- SharePoint 관리 센터에서 사이트에 대한 게스트 공유 설정을 업데이트하여 레이블을 만들 때 선택한 내용과 맞게 설정하고, 기본 공유 링크를 *특정 사용자* 로 업데이트합니다.
- 구성원이 사이트를 공유하지 못하도록 사이트의 사이트 공유 설정을 업데이트합니다.

### <a name="site-guest-sharing-settings"></a>사이트 게스트 공유 설정

레이블을 만들 때 선택한 게스트 공유 설정(팀 구성원에게만 영향을 미침)은 다음과 같이 연결된 SharePoint 사이트의 게스트 공유 설정과 일치해야 합니다.

|레이블 설정|SharePoint 사이트 설정|
|:------------|:----------------------|
|**Office 365 그룹 소유자가 조직 외부의 사용자를 그룹에 추가할 수 있도록 허용** 선택됨|**신규 및 기존 게스트**(새 팀의 기본값)|
|**Office 365 그룹 소유자가 조직 외부의 사용자를 그룹에 추가할 수 있도록 허용** 선택 안 됨|**조직 내부 사용자만**|

사이트 설정을 업데이트하려면
1. [SharePoint 관리 센터](https://admin.microsoft.com/sharepoint)를 엽니다.
2. **사이트** 에서 **활성 사이트** 를 클릭합니다.
3. 팀과 연결된 사이트를 클릭합니다.
4. **정책** 탭의 **외부 공유** 에서 **편집** 을 클릭합니다.
5. 중요 레이블을 만들 때 게스트 공유를 허용한 경우 **신규 및 기존 게스트** 가 선택되어 있는지 확인합니다. 레이블을 만들 때 공유를 허용하지 않은 경우 **조직 내부 사용자만** 을 선택합니다.
6. 기본 공유 링크 유형사람만 **조직 수준 설정과 동일** 확인란을 선택 취소하고 **특정 사특정(사용자가 지정하는 사람만)** 를 선택합니다.
7. **저장** 을 클릭합니다.

팀 만들기 프로세스의 일부로 이를 스크립팅하려면 다음 매개 변수와 함께 [Set-Get-sposite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite)를 사용할 수 있습니다.

- 게스트 공유를 해제하려면 `-SharingCapability Disabled`(기본적으로 켜져 있음)
- 기본 공유 링크를 *특정 사용자* 로 변경하려면 `-DefaultSharingLinkType Internal`

#### <a name="private-channels"></a>비공개 채널

팀에 비공개 채널을 추가하면 각 비공개 채널이 기본 공유 설정을 포함하는 새 SharePoint 사이트를 만듭니다. 이러한 사이트는 SharePoint 관리 센터에 표시되지 않으므로 Set-SPOSite PowerShell cmdlet을 사용하여 게스트 공유 설정을 업데이트해야 합니다.

### <a name="site-sharing-settings"></a>사이트 공유 설정

팀 구성원이 아닌 사용자와 SharePoint 사이트를 공유하지 못하게 하도록 이러한 공유는 소유자로 제한합니다.

소유자 전용 사이트 공유를 구성하려면
1. Teams에서 업데이트하려는 팀의 **일반** 탭으로 이동합니다.
2. 팀의 도구 막대에서 **파일** 을 클릭합니다.
3. 줄임표를 클릭한 다음 **SharePoint에서 열기** 를 클릭합니다.
4. 기본 SharePoint 사이트의 도구 막대에서 설정 아이콘을 클릭한 다음 **사이트 사용 권한** 을 클릭합니다.
5. 사이트 사용 권한 창에 있는 **공유 설정** 에서 **공유 설정 변경** 을 클릭합니다.
6. **권한 공유** 에서 **사이트 소유자 및 회원을 선택하고 편집 권한이 있는 사용자는 파일 및 폴더를 공유할 수 있지만 사이트 소유자 만 사이트를 공유할 수 있습니다** 를 선택한 다음 **저장** 을 클릭합니다.


## <a name="see-also"></a>참고 항목

[민감도 레이블과 해당 정책 생성 및 구성](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels)


