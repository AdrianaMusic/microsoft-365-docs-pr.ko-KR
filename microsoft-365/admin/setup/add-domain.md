---
title: Microsoft 365에 도메인 추가
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
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: DNS 호스트에 DNS 레코드를 추가하여 Microsoft 365 관리 센터의 Microsoft 365에 도메인을 추가합니다. 설치 마법사가 프로세스를 안내합니다.
ms.openlocfilehash: 3e7463bd4cf6b7836a9770421e0b8ce597524a67
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658054"
---
# <a name="add-a-domain-to-microsoft-365"></a>Microsoft 365에 도메인 추가

::: moniker range="o365-21vianet"

> [!NOTE]
> 관리 센터가 변경되고 있습니다. 사용자의 환경이 여기에 설명된 세부 정보와 맞지 않는 경우에는 [새 Microsoft 365 관리 센터 정보](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet)를 참조하세요.

::: moniker-end

 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](domains-faq.yml)** 하세요. 
  
 *도메인을 추가, 수정 또는  제거하려면  비즈니스 또는 엔터프라이즈 계획의 전역 관리자 [되어야 합니다.](https://products.office.com/business/office) 이러한 변경 내용은 전체 테넌트,   사용자 지정된 관리자 또는 일반 사용자에게 영향을 미치며 이러한 변경을 할 수 없습니다.*  

 다음 단계에 따라 도메인을 추가, 설정 또는 계속합니다. 

::: moniker range="o365-worldwide"
  
::: moniker-end

::: moniker range="o365-germany"

> [!VIDEO https://www.microsoft.com/videoplayer/embed/dda6df6d-37b0-41ff-905b-089448355a31?autoplay=false]
  
::: moniker-end

::: moniker range="o365-worldwide"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> 의 관리 센터로 이동합니다.

::: moniker-end
::: moniker range="o365-germany"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a> 의 관리 센터로 이동합니다.

::: moniker-end

::: moniker range="o365-21vianet"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a> 의 관리 센터로 이동합니다.

::: moniker-end
    
2. 설정 도메인   >  **페이지로** 이동합니다. 

3. 도메인 **추가를 선택합니다.**
    
4. 추가할 도메인의 이름을 입력하고 다음을 **선택합니다.**
    
5. 도메인을 소유하고 있는지 확인하는 방법을 선택 합니다.
    
    1. 도메인 등록 기관에서 [Domain Connect를](#domain-connect-registrars-integrating-with-microsoft-365)사용하는 경우 [Microsoft는](../get-help-with-domains/domain-connect.md) 사용자가 등록 기관에 로그인하고 Microsoft 365에 대한 연결을 확인하여 레코드를 자동으로 설정합니다. You'll be returned to the admin center and Microsoft will automatically verify your domain.
    2. TXT 레코드를 사용하여 도메인을 확인할 수 있습니다. 이 옵션을 선택하고 **다음을** 선택하여 등록 기관의 웹 사이트에 이 DNS 레코드를 추가하는 방법에 대한 지침을 참조하세요. 레코드를 추가한 후 확인하는 데 최대 30분이 걸릴 수 있습니다. 
    3. 텍스트 파일을 도메인의 웹 사이트에 추가할 수 있습니다. 설치 마법사에서 .txt 파일을 선택하고 다운로드한 다음 웹 사이트의 최상위 폴더에 파일을 업로드합니다. 파일의 경로는 다음과 `http://mydomain.com/ms39978200.txt` 같습니다. 웹 사이트에서 파일을 찾아 도메인을 소유하고 있는 것을 확인할 것입니다.
    
6. Microsoft에서 도메인을 사용하는 데 필요한 DNS를 변경하는 방법을 선택하십시오.
    
    1. 등록 **기관에서** [Domain Connect를](#domain-connect-registrars-integrating-with-microsoft-365)지원하고 [Microsoft에서](../get-help-with-domains/domain-connect.md) 등록 기관에 로그인하고 Microsoft 365에 대한 연결을 확인하여 자동으로 레코드를 설정하는 경우 DNS 레코드 추가를 선택하십시오.
    2. 도메인에 특정 Microsoft 365 서비스만 연결하려는 경우 또는 지금 건너뛰고 나중에 이 작업을 진행하려면 **DNS** 레코드를 추가합니다. **무엇을 할지 정확히 아는 경우에만 이 옵션을 선택하세요.**

7. *DNS* 레코드를 직접 추가하기로  선택한 경우 다음을 선택하면 도메인을 설정하기 위해 등록 기관 웹 사이트에 추가해야 하는 모든 레코드가 있는 페이지가 표시됩니다. 

    포털에서 등록 기관을 인식하지 못하는 경우에는 [이러한 일반 지침을 따르면](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) 됩니다.
    
    호스트를 찾으려면 [호스트 별 지침](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions) 목록을 확인하고 다음 단계에 따라 필요한 모든 레코드를 추가합니다. 
    
    사용 중인 도메인의 DNS 호스팅 공급자 또는 도메인 등록 기관을 모르는 경우 [도메인 등록자 또는 DNS 호스팅 공급자 찾기](../get-help-with-domains/find-your-domain-registrar.md)를 참조하세요.
    
    나중에 기다리려면 모든 서비스를 선택하지 않고 계속을 클릭하거나 **이전** 도메인 연결 단계에서 다른  옵션을 선택하고 지금 **건너뛰기를 선택합니다.**
    
8. Select **Finish** - you're done!

## <a name="add-or-edit-custom-dns-records"></a>사용자 지정 DNS 레코드 추가 또는 편집

아래 단계에 따라 웹 사이트 또는 제3자 서비스에 대한 사용자 지정 레코드를 추가합니다.

1. .에서 Microsoft 관리 센터에 <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> 로그인합니다.

2. 설정 도메인    >  **페이지로** 이동합니다.

3. **도메인** 페이지에서 도메인을 선택합니다. 
    
4. **DNS 설정에서** 사용자 지정 **레코드를 선택합니다.** 그런 다음 **새 사용자 지정 레코드를 선택합니다.**

5. 추가할 DNS 레코드 유형을 선택하고 새 레코드에 대한 정보를 입력합니다.
    
6. **저장** 을 선택합니다.

## <a name="registrars-with-domain-connect"></a>도메인 연결을 사용하여 등록자

[도메인 연결](https://www.domainconnect.org/) 사용 등록 기관을 사용하면 몇 분 정도 걸리는 3단계 프로세스에서 도메인을 Microsoft 365에 추가할 수 있습니다. 
  
마법사에서 도메인을 소유하고 있는 것을 확인한 다음 도메인의 레코드를 자동으로 설정하게 되며, 전자 메일이 Microsoft 365 및 Teams와 같은 기타 Microsoft 365 서비스로 전송되어 도메인과 함께 작업합니다.
  
> [!NOTE]
> 설정 마법사를 시작하기 전에 브라우저의 팝업 차단 기능을 해제하세요.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Microsoft 365와 통합하는 도메인 연결 등록자

- [1 &amp; 1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer 또는 WildWestDomains(SecureServer DNS 호스팅을 사용하는 GoDaddy 리셀러)
    - 예제:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>전자 메일 및 웹 사이트는 어떻게 하나요?

설치를 마친 후 도메인의 MX 레코드가 Microsoft 365를 지점으로 업데이트하고 도메인의 모든 전자 메일이 Microsoft 365로 전송됩니다. 도메인에서 전자 메일을 받는 모든 사용자에 대해 Microsoft 365에서 사용자를 추가하고 사서함을 설정해야 합니다.
  
업무에 사용하는 웹 사이트가 있는 경우 어디에 있든 작동이 유지됩니다. 도메인 연결 설정 단계는 웹 사이트에 영향을 주지 않습니다.

## <a name="related-articles"></a>관련 문서

[도메인 FAQ](domains-faq.yml)

[도메인이 무엇인가요?](../get-help-with-domains/what-is-a-domain.md)

[Microsoft 365에서 도메인 이름 구입하기](../get-help-with-domains/buy-a-domain-name.md)

[도메인 설정(호스트별 지침)](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md)
