---
title: Office 365용 Defender에서 안전한 링크 설정에 대한 전역 설정 구성
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 관리자는 Office 365용 Microsoft Defender에서 안전한 링크에 대한 전역 설정(Office 365 앱에 대한 '다음 URL 차단' 목록 및 보호)을 보고 구성하는 방법을 배울 수 있습니다.
ms.openlocfilehash: bc44432d4d9478e4c6a2414a70acc785c5b2c005
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682909"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Office 365용 Microsoft Defender에서 안전한 링크에 대한 전역 설정 구성

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> 이 문서는 [Office 365용 Microsoft Defender](office-365-atp.md)가 있는 비즈니스 고객을 대상으로 합니다. Outlook의 Safelinks에 대한 정보를 찾고 있는 가정용 사용자인 경우 고급 보안 [Outlook.com.](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2)

안전한 링크는 메일 흐름에서 인바운드 전자 메일 메시지의 URL 검색을 제공하는 [Office 365용 Microsoft Defender의](office-365-atp.md) 기능으로, 전자 메일 메시지 및 다른 위치에서 URL 및 링크의 클릭 확인 시간을 제공합니다. 자세한 내용은 [Office 365용 Microsoft Defender의 안전한 링크를 참조하세요.](atp-safe-links.md)

안전한 링크 정책에서 대부분의 안전 링크 설정을 구성합니다. 자세한 내용은 [Office 365용 Microsoft Defender에서 안전한](set-up-atp-safe-links-policies.md)링크 정책 설정을 참조하세요.

그러나 안전한 링크는 모든 활성 안전 링크 정책에 포함된 모든 사용자에게 적용되는 전역 설정도 사용합니다. 이러한 전역 설정 영역:

- 다음 **URL 차단 목록** 자세한 내용은 안전한 링크에 [대한 "다음 URL 차단" 목록을 참조하세요.](atp-safe-links.md#block-the-following-urls-list-for-safe-links)
- Office 365 앱에 대한 안전한 링크 보호입니다. 자세한 내용은 [Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps)앱에 대한 안전한 링크 설정을 참조하세요.

보안 & 준수 센터 또는 PowerShell에서 전역 안전 링크 설정을 구성할 수 있습니다(Exchange Online에 사서함이 있는 적격 Microsoft 365 조직, Exchange Online 사서함이 없지만 Office 365 추가 기능 구독용 Microsoft Defender를 사용하여 조직의 독립 실행형 EOP PowerShell).

## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용은 무엇인가요?

- 안전 링크에 대한 전역 설정에서 제공하는 기능은 활성 안전 링크 정책에 포함된 사용자에게만 적용됩니다. 기본 제공 또는 기본 안전 링크 정책이 있으므로 이러한 전역 설정이 활성화될 수 있도록 안전 링크 정책을 하나 이상 만들어야 합니다. 자세한 내용은 [Office 365용 Microsoft Defender에서 안전한](set-up-atp-safe-links-policies.md)링크 정책 설정을 참조하세요.

- <https://protection.office.com/>에서 보안 및 준수 센터를 엽니다. 안전한 링크 페이지로 직접 **이동하기** 위해 다음을 <https://protection.office.com/safelinksv2> 사용하세요.

- Exchange Online PowerShell에 연결하려면 [Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)을 참조하세요. 독립 실행형 EOP PowerShell에 연결하려면 [Exchange Online Protection PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell)을 참조하세요.

- 이 문서의 절차를 수행하려면 먼저 보안 및 준수 센터에서 사용 권한을 받아야 합니다.
  - 안전한 링크에 대한 전역 설정을 구성하려면 조직 관리  또는 보안 관리자 역할 그룹의 **구성원이** 되거나,
  - 안전 링크에 대한 전역 설정에 대한 읽기 전용 액세스 권한을  사용하려면 전역 읽기 사용자 또는 보안 읽기 권한이 있는 역할 그룹의 **구성원이** 되거나,

  자세한 내용은 [보안 및 준수 센터의 사용 권한](permissions-in-the-security-and-compliance-center.md)을 참조하세요.

  **참고**:

  - Microsoft 365 관리 센터의 해당 Azure Active Directory 역할에 사용자를 추가하면 사용자에게 보안 및 준수 센터에서 필요한 권한 _및_ Microsoft 365의 다른 기능에 대한 권한이 부여됩니다. 자세한 내용은 [관리자 역할 정보](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)를 참조하세요.
  - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups)의 **보기 전용 조직 관리** 역할 그룹에도 기능에 대한 읽기 전용 권한을 부여합니다.

- 안전한 링크에 대한 전역 설정에 대한 권장 값은 안전한 링크 설정을 [참조하세요.](recommended-settings-for-eop-and-office365-atp.md#safe-links-settings)

- 새 정책 또는 업데이트된 정책을 적용하는 데 최대 30분을 허용합니다.

- [Office 365용 Microsoft Defender에](office-365-atp.md#new-features-in-microsoft-defender-for-office-365)새로운 기능이 지속적으로 추가되고 있습니다. 새 기능이 추가될 때 기존 안전 링크 정책을 조정해야 할 수 있습니다.

## <a name="configure-the-block-the-following-urls-list-in-the-security--compliance-center"></a>보안 및 준수 센터에서 "다음 URL 차단" & 구성

다음 URL 차단 **목록은** 지원되는 앱에서 안전한 링크 검색을 통해 항상 차단해야 하는 링크를 식별합니다. 자세한 내용은 안전한 링크에 [대한 "다음 URL 차단" 목록을 참조하세요.](atp-safe-links.md#block-the-following-urls-list-for-safe-links)

1. 보안 & 준수 센터에서 **위협** 관리 \>  \> **정책 ATP** 안전한 링크로 이동한 다음 전역 설정을 **클릭합니다.**

2. 조직의 **안전 링크** 정책에 나타나는 플라이아웃에서 다음 URL 차단 **상자로 이동하십시오.**

3. "다음 URL 차단" 목록에 대한 항목 구문에 설명된 하나 이상의 항목을 [구성합니다.](atp-safe-links.md#entry-syntax-for-the-block-the-following-urls-list)

   작업을 마쳤으면 **저장** 을 클릭합니다.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>PowerShell에서 "다음 URL 차단" 목록 구성

항목 구문에 대한 자세한 내용은 ["다음 URL 차단"](atp-safe-links.md#entry-syntax-for-the-block-the-following-urls-list)목록의 항목 구문을 참조하세요.

**Get-AtpPolicyForO365** cmdlet을 사용하여 _BlockURLs_ 속성의 기존 항목을 볼 수 있습니다.

- 기존 항목을 대체할 값을 추가하기 위해 Exchange Online PowerShell 또는 Exchange Online Protection PowerShell에서 다음 구문을 사용합니다.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  다음은 목록에 다음 항목을 추가하는 예제입니다.

  - 도메인, 하위 도메인 및 도메인에 대한 경로를 fabrikam.com.
  - 하위 도메인 연구를 차단하지만 하위 도메인의 상위 도메인이나 다른 하위 도메인은 tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- 다른 기존 항목에 영향을 주지 않고 값을 추가하거나 제거하려면 다음 구문을 사용합니다.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  이 예제에서는 새 adatum.com 항목을 추가하고 새 fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-security--compliance-center"></a>보안 및 준수 센터에서 Office 365 앱에 대한 안전한 & 구성

Office 365 앱의 안전한 링크 보호는 지원되는 Office 데스크톱, 모바일 및 웹앱의 문서에 적용됩니다. 자세한 내용은 [Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps)앱에 대한 안전한 링크 설정을 참조하세요.

1. 보안 & 준수 센터에서 **위협** 관리 \>  \> **정책 ATP** 안전한 링크로 이동한 다음 전역 설정을 **클릭합니다.**

2. 조직의 **안전 링크** 정책이 표시되면 플라이아웃이 나타나면 전자 메일 섹션을 제외한 콘텐츠에 적용되는 설정에서 다음 설정을 **구성합니다.**

   - **Office 365 응용 프로그램:** 지원되는 Office 365 앱에 대해 안전한 링크를 사용하도록 설정하려면 토글이 오른쪽에 있는지 ![ 확인: 설정/설정/ 설정 ](../../media/scc-toggle-on.png)

   - **사용자가 안전한** 링크를 클릭하는 경우를 추적하지 않습니다. 토글을 왼쪽으로 이동하여 지원되는 Office 365 앱에서 차단된 URL과 관련된 사용자 클릭을 추적합니다. ![ 토글 끄기. ](../../media/scc-toggle-off.png)

   - **사용자가 원래 URL에** 대한 안전한 링크를 클릭할 수 없습니다. 사용자가 지원되는 Office 365 앱에서 원래 차단된 URL을 클릭하지 못하게 설정하려면 토글이 오른쪽에 있는지 확인합니다. ![ ](../../media/scc-toggle-on.png)

   작업을 마쳤으면 **저장** 을 클릭합니다.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>PowerShell에서 Office 365 앱에 대한 안전한 링크 보호 구성

PowerShell을 사용하여 Office 365 앱에 대해 안전한 링크 보호를 구성하는 경우 Exchange Online PowerShell 또는 Exchange Online Protection PowerShell에서 다음 구문을 사용하세요.

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

이 예에서는 Office 365 앱에서 안전한 링크 보호에 대한 다음 설정을 구성합니다.

- Office 365 앱에 대한 안전한 링크가 켜져 _있습니다(EnableSafeLinksForO365Clients_ 매개 변수를 사용하지 않습니다. 기본값은 $true.
- 지원되는 Office 365 앱에서 차단된 URL과 관련된 사용자 클릭이 추적됩니다.
- 사용자는 지원되는 Office 365 앱에서 원래 차단된 URL을 클릭할 수 _없습니다(AllowClickThrough_ 매개 변수를 사용하지 않습니다. 기본값은 $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

구문과 매개 변수에 대한 자세한 내용은 [Set-AtpPolicyForO365를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365)

## <a name="how-do-you-know-these-procedures-worked"></a>이 절차가 제대로 수행되었는지 어떻게 확인하나요?

안전한 링크에 대한 전역 설정(다음 **URL** 목록 차단 및 Office 365 앱 보호 설정)을 성공적으로 구성한지 확인하려면 다음 단계를 수행합니다.

- 보안 & 준수 센터에서 **위협** 관리 \>  \> **정책 ATP 안전한** 링크로 이동하여 전역 설정을 클릭하고 플라이아웃에 나타나는 설정을 확인합니다.

- Exchange Online PowerShell 또는 Exchange Online Protection PowerShell에서 다음 명령을 실행하고 설정을 확인합니다.

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  구문과 매개 변수에 대한 자세한 내용은 [Get-AtpPolicyForO365를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/get-atppolicyforo365)
