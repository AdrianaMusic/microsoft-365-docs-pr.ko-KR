---
title: 도메인 제거
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Microsoft 365에서 이전 도메인을 제거하고 사용자 및 그룹을 다른 도메인으로 이동하는 방법을 배워야 합니다.
ms.openlocfilehash: 02ec704e400af76c25c0eb54de10291e2ef3caa2
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688264"
---
# <a name="remove-a-domain"></a>도메인 제거

::: moniker range="o365-21vianet"

> [!NOTE]
> 관리 센터가 변경되고 있습니다. 사용자의 환경이 여기에 설명된 세부 정보와 맞지 않는 경우에는 [새 Microsoft 365 관리 센터 정보](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet)를 참조하세요.

::: moniker-end
  
 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요. 
  
다른 Microsoft 365 구독 요금제에 도메인을 추가하려는 경우 도메인을 제거하고 있습니까? 아니면 단지 구독을 취소하고 싶으신가요? [ 또는 구독을 변경 ](../../commerce/subscriptions/switch-to-a-different-plan.md)하거나 [구독을 취소](../../commerce/subscriptions/cancel-your-subscription.md)할 수 있습니다.
  
### <a name="step-1-move-users-to-another-domain"></a>1단계: 사용자를 다른 도메인으로 이동

#### <a name="move-users"></a>사용자 이동

::: moniker range="o365-worldwide"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">관리 센터</a>로 이동합니다.

2. 사용자 **활성 사용자를** > **선택합니다.**

3. 이동할 모든 사용자의 이름 옆에 있는 상자를 선택합니다.

4. Select **More options** (**...**), at the top of the page, and then choose **Change domains**.

5. 도메인 **변경 창에서** 다른 도메인을 선택합니다.

현재 제거 중인 도메인에 있는 경우 직접 이 작업을 해야 합니다. 사용자 계정의 도메인을 편집하는 경우 계속하려면 로그아웃한 후 선택한 새 도메인을 사용하여 다시 로그인해야 합니다.

::: moniker-end

::: moniker range="o365-germany"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">관리 센터</a>로 이동합니다.  

2. 사용자 **활성 사용자를** > **선택합니다.**

3. 이동할 모든 사용자의 이름 옆에 있는 상자를 선택합니다.

4. At the top of the page, choose **More** > **Edit domains.**

5. 도메인 **편집 창에서** 다른 도메인을 선택합니다.
  
현재 제거 중인 도메인에 있는 경우 직접 이 작업을 해야 합니다. 사용자 계정의 도메인을 편집하는 경우 계속하려면 로그아웃한 후 선택한 새 도메인을 사용하여 다시 로그인해야 합니다.

::: moniker-end

::: moniker range="o365-21vianet"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">관리 센터</a>로 이동합니다.  

2. 사용자 **활성 사용자를** > **선택합니다.**

3. 이동할 모든 사용자의 이름 옆에 있는 상자를 선택합니다.

4. At the top of the page, choose **More** > **Edit domains.**

5. 도메인 **편집 창에서** 다른 도메인을 선택합니다.
  
현재 제거 중인 도메인에 있는 경우 직접 이 작업을 해야 합니다. 사용자 계정의 도메인을 편집하는 경우 계속하려면 로그아웃한 후 선택한 새 도메인을 사용하여 다시 로그인해야 합니다.

::: moniker-end

#### <a name="move-yourself"></a>직접 이동

::: moniker range="o365-worldwide"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">관리 센터</a>로 이동합니다.

2. 사용자  활성 \> **사용자로 이동한** 다음 목록에서 계정을 선택합니다.

3. 계정 **탭에서** **사용자** 이름 관리를 선택한 다음 다른 도메인을 선택합니다.
  
4. At the top, select your account name, then select **Sign Out**.

5. 새 도메인과 동일한 암호로 로그인합니다.

PowerShell을 사용하여 사용자를 다른 도메인으로 이동할 수도 있습니다. 자세한 내용은 [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0)을 참조하세요. 기본 도메인을 설정하려면 [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0)을 사용하세요.

::: moniker-end

::: moniker range="o365-germany"

1. 사용자  활성 \> **사용자로 이동한** 다음 목록에서 이름을 선택합니다.

2. 사용자 **이름/전자 메일 섹션에서** 편집을 선택한 다음 다른 도메인을 선택합니다. 

3. 기본 **저장 닫기로** > **설정 선택** > 
  
4. At the top, select your account name, then select **Sign Out**.

5. 새 도메인과 동일한 암호로 로그인합니다.

PowerShell을 사용하여 사용자를 다른 도메인으로 이동할 수도 있습니다. 자세한 내용은 [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0)을 참조하세요. 기본 도메인을 설정하려면 [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0)을 사용하세요.

::: moniker-end

::: moniker range="o365-21vianet"

1. 사용자  활성 \> **사용자로 이동한** 다음 목록에서 이름을 선택합니다.

2. 사용자 **이름/전자 메일 섹션에서** 편집을 선택한 다음 다른 도메인을 선택합니다. 

3. 기본 **저장 닫기로** > **설정 선택** > 
  
4. At the top, select your account name, then select **Sign Out**.

5. 새 도메인과 동일한 암호로 로그인합니다.

PowerShell을 사용하여 사용자를 다른 도메인으로 이동할 수도 있습니다. 자세한 내용은 [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0)을 참조하세요. 기본 도메인을 설정하려면 [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0)을 사용하세요.

::: moniker-end

### <a name="step-2-move-groups-to-another-domain"></a>2단계: 다른 도메인으로 그룹 이동

::: moniker range="o365-worldwide"

1. 관리 센터에서 그룹 **그룹 페이지로** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> 이동합니다.
  
2. 그룹 이름을 선택한 다음 전자 메일 주소 기본 아래에 있는 일반 **탭에서** **편집을** **선택합니다.**

3. 드롭다운 목록을 사용하여 다른 도메인을 선택합니다.

4. **저장** 을 선택한 다음 **닫기** 를 선택합니다. 제거하려는 도메인과 연관된 그룹 또는 분배 목록에 대해 이 단계를 반복합니다.

::: moniker-end

::: moniker range="o365-germany"

1. 관리 <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">센터에서</a>그룹 **그룹 페이지로** >  이동합니다.

2. 그룹 이름을 선택하고 이름 옆에 **있는** 편집을 **선택합니다.**

3. 드롭다운 목록을 사용하여 다른 도메인을 선택합니다.

4. **저장** 을 선택한 다음 **닫기** 를 선택합니다. 제거하려는 도메인과 연관된 그룹 또는 분배 목록에 대해 이 단계를 반복합니다.

::: moniker-end

::: moniker range="o365-21vianet"

1. 관리 <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">센터에서</a>그룹 **그룹 페이지로** >  이동합니다.

2. 그룹 이름을 선택하고 이름 옆에 **있는** 편집을 **선택합니다.**

3. 드롭다운 목록을 사용하여 다른 도메인을 선택합니다.

4. **저장** 을 선택한 다음 **닫기** 를 선택합니다. 제거하려는 도메인과 연관된 그룹 또는 분배 목록에 대해 이 단계를 반복합니다.

::: moniker-end

### <a name="step-3-remove-the-old-domain"></a>3단계: 이전 도메인 제거

::: moniker range="o365-worldwide"

1. I관리 센터에서 **설정** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"> 도메인</a> 페이지로 이동하십시오.

::: moniker-end

::: moniker range="o365-germany"

1. 관리 센터에서 설치  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">도메인 페이지로</a> 이동합니다.

::: moniker-end

::: moniker range="o365-21vianet"

1. 관리 센터에서 설치  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">도메인 페이지로</a> 이동합니다.

::: moniker-end
  
2. 도메인 **페이지에서** 제거할 도메인을 선택합니다.

3. 오른쪽 창에서 제거를 **선택합니다.**

4. 추가 프롬프트에 따라 닫기 를 **선택합니다.**

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>도메인을 제거하는 데 걸리는 시간은 얼마인가요?

보안 그룹, 메일 그룹, 사용자 및 Microsoft 365 그룹과 같은 많은 곳에서 참조되지 않는 경우 Microsoft 365에서 도메인을 제거하는 데 5분 정도 걸릴 수 있습니다. 도메인을 사용하는 참조가 많으면 도메인을 제거하는 데 몇 시간(하루)이 걸릴 수 있습니다.
  
수백 또는 수천 명의 사용자가 있는 경우 PowerShell을 사용하여 모든 사용자에 대해 쿼리한 다음 사용자를 다른 도메인으로 이동합니다. 그러지 않으면 UI에서 몇 명의 사용자가 누락될 수 있으며, 이 경우 도메인을 제거하기 위해 이동하면 도메인을 제거할 수 없으며 이유를 알지 못하게 됩니다. 자세한 내용은 [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0)을 참조하세요. 기본 도메인을 설정하려면 [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0)을 사용하세요.
  
## <a name="still-need-help"></a>아직 해결되지 않았습니까?

::: moniker range="o365-worldwide"

> [!NOTE]
> 계정에서 [". onmicrosoft.com"](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) 도메인을 제거할 수 없습니다. 도메인을 제거하면 사용자 계정이 기본 SMTP/UserprincipalName onmicrosoft.com ".onmicrosoft.com" 주소로 되돌아가게 됩니다.
  
여전히 작동하지 않나요? 도메인을 수동으로 제거해야 할 수도 있습니다. [전화로 연락주시면](../contact-support-for-business-products.md) 작업을 수행할 수 있도록 지원하겠습니다.
  
::: moniker-end

## <a name="related-articles"></a>관련 문서

[도메인 FAQ](../setup/domains-faq.yml)

[다른 비즈니스용 Microsoft 365 요금제로 전환](../../commerce/subscriptions/switch-to-a-different-plan.md)

[구독 취소](../../commerce/subscriptions/cancel-your-subscription.md)
