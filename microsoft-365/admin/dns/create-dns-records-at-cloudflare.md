---
title: Cloudflare에서 Microsoft용 DNS 레코드 만들기
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
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Microsoft용 Cloudflare에서 도메인을 확인하고 전자 메일, 비즈니스용 Skype Online 및 기타 서비스에 대한 DNS 레코드를 설정하는 방법을 배워야 합니다.
ms.openlocfilehash: 110bd96c0eecf40ae96efe7055d82a8d12dde607
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657963"
---
# <a name="create-dns-records-at-cloudflare-for-microsoft"></a>Cloudflare에서 Microsoft용 DNS 레코드 만들기

 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요. 
  
DNS 호스팅 공급자로 Cloudflare를 사용하고 있는 경우 이 문서의 단계에 따라 도메인을 확인하고 전자 메일, 비즈니스용 Skype Online에 대한 DNS 레코드를 설정하세요.
  
Cloudflare에서 이러한 레코드를 추가하고 나면 도메인이 Microsoft 365 서비스에서 작동하게 설정됩니다.
  
  
> [!NOTE]
>  일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요. 
  
## <a name="change-your-domains-nameserver-ns-records"></a>도메인의 NS(이름 서버) 레코드 변경
<a name="BKMK_Nameservers"> </a>

> [!IMPORTANT]
> 이 절차는 도메인을 구입하고 등록한 도메인 등록 기관에서 수행해야 합니다. 
  
Cloudflare에 등록할 때 Cloudflare 설치 프로세스를 사용하여 도메인을 **추가했습니다.** 
  
추가한 도메인은 Cloudflare 또는 별도의 도메인 등록 기관에서 구입한 것입니다. Microsoft 365에서 도메인에 대한 DNS 레코드를 확인하고 만들하려면 먼저 도메인 등록 기관에서 Cloudflare의 이름 서버를 사용할 수 있도록 이름 서버를 변경해야 합니다.
  
도메인 등록 기관 웹 사이트에서 도메인 이름 서버를 직접 변경하려면 다음 단계를 따릅니다.
  
1. 도메인 등록 기관의 웹 사이트에서 도메인의 이름 서버를 편집할 수 있는 영역을 찾습니다.
    
2. 다음 표의 값을 사용하여 이름 서비스 레코드를 두 개 만들거나 이러한 값과 일치하게 기존 이름 서비스 레코드를 편집합니다.
    
    |||
    |:-----|:-----|
    |첫 번째 이름 서버  <br/> |Cloudflare에서 제공하는 이름 서비스 값을 사용 합니다.  <br/> |
    |두 번째 이름 서버  <br/> |Cloudflare에서 제공하는 이름 서비스 값을 사용 합니다.  <br/> |
   
    > [!TIP]
    > You should use at least two name server records. 다른 이름 서버가 나열되어 있는 경우 해당 서버를 삭제해야 합니다. 
  
3. 변경 내용을 저장합니다.
    
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. 그런 다음 Microsoft 전자 메일 및 기타 서비스가 모두 도메인에서 작동하게 설정됩니다. 
  
## <a name="add-a-txt-record-for-verification"></a>확인을 위해 TXT 레코드 추가
<a name="BKMK_verify"> </a>

Microsoft에서 사용자 도메인을 사용하려면 먼저 도메인을 소유하고 있어야 합니다. 도메인 등록 기관에서 사용자의 계정으로 로그인하고 DNS 레코드를 만들 수 있으면 Microsoft에 도메인을 소유하고 있음을 증명할 수 있습니다.
  
> [!NOTE]
> 이 레코드는 사용자가 도메인을 소유하고 있는지 확인하는 데만 사용되며 그 밖에 아무런 영향도 주지 않습니다. 원하는 경우 나중에 삭제할 수 있습니다. 
  
1. 시작하려면 이 링크를 사용하여 Cloudflare의 도메인 [페이지로 이동합니다.](https://www.cloudflare.com/a/login) 먼저 로그인하라는 메시지가 표시됩니다.
  
2. 홈 **페이지에서** 업데이트할 도메인을 선택합니다. 
  
3. 도메인의 **개요** 페이지에서 **DNS를 선택합니다.**

  
4. DNS 관리 **페이지에서** 레코드 추가를 클릭한 다음 다음 표의 값을 선택합니다. 
    
    |**유형**|**이름**|**자동 TTL**|**콘텐츠**|
    |:-----|:-----|:-----|:----|
    |TXT  <br/> |@  <br/> |30분  <br/> |MS=ms *XXXXXXXX*  <br/> **참고:** 이 값은 예시입니다. 여기에는 표에 있는 특정 **대상 또는 주소 가리키기** 값을 사용합니다.           [이 값을 찾는 방법](../get-help-with-domains/information-for-dns-records.md)    |
  
    
5. **저장** 을 선택합니다.
  
  
9. 방금 만든 레코드가 인터넷에서 업데이트될 수 있도록 몇 분 정도 기다립니다.
    
이제 도메인 등록 기관의 사이트에 레코드를 추가한 후 Microsoft로 돌아가 레코드를 검색합니다.
  
Microsoft에서 올바른 TXT 레코드를 찾으면 도메인이 확인된 것입니다.
  
1. Microsoft 관리 센터에서 **설정** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">도메인</a> 페이지로 이동합니다.

    
2. **도메인** 페이지에서 확인 중인 도메인을 선택합니다. 
    
    
  
3. **설정** 페이지에서 **설정 시작** 을 선택합니다.
    
    
  
4. **도메인 확인** 페이지에서 **확인** 을 선택합니다.
    
    
  
> [!NOTE]
>  일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요. 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>사용자 도메인의 전자 메일이 Microsoft로 전송되도록 MX 레코드 추가하기
<a name="BKMK_add_MX"> </a>

1. 시작하려면 이 링크를 사용하여 Cloudflare의 도메인 [페이지로 이동합니다.](https://www.cloudflare.com/a/login) 먼저 로그인하라는 메시지가 표시됩니다.
  
2. 홈 **페이지에서** 업데이트할 도메인을 선택합니다. 
  
3. 도메인의 **개요** 페이지에서 **DNS를 선택합니다.**

  
4. DNS 관리 **페이지에서** 레코드 추가를 클릭한 다음 다음 표의 값을 선택합니다. 
    
    |**유형**|**이름**|**메일 서버**|**Priority(우선 순위)**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **참고:** Microsoft  *\<domain-key\>*  365 계정에서 다운로드하세요.   [이 값을 찾는 방법](../get-help-with-domains/information-for-dns-records.md) |1   <br/> 우선 순위에 대한 자세한 내용은 [MX 우선 순위란?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq)을 참조하세요. <br/>|30분  <br/> |
   

  
5. **저장** 을 선택합니다.
  
9. MX 레코드 섹션에 나열된 다른 **MX** 레코드가 있는 경우 삭제(X) 아이콘을 선택하여 해당 레코드를 **삭제합니다.** 
  
10. 확인 대화 상자에서 **삭제를** 선택하여 변경 내용을 선택합니다. 

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Microsoft에 필요한 6개의 CNAME 레코드 추가
<a name="BKMK_add_CNAME"> </a>

1. 시작하려면 이 링크를 사용하여 Cloudflare의 도메인 [페이지로 이동합니다.](https://www.cloudflare.com/a/login) 먼저 로그인하라는 메시지가 표시됩니다.
    
  
2. 홈 **페이지에서** 업데이트할 도메인을 선택합니다. 
  
3. 도메인의 **개요** 페이지에서 **DNS를 선택합니다.**

  
4. 5개의 CNAME 레코드 중 첫 번째 레코드를 추가합니다.
    
    DNS 관리 **페이지에서** 레코드 추가를 클릭한 다음 다음 표의 값을 선택합니다.
    
    
    |**유형**|**Name(이름)**|**Target(대상)**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com  <br/> |30분  <br/> |
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com  <br/> |30분  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |30분  <br/> |
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |30분  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |30분  <br/> |
    |CNAME  <br/> |msoid  <br/> |clientconfig.microsoftonline-p.net  <br/> |30분  <br/> |
    
  
5. DNS 트래픽 **아이콘(주황색** 클라우드)을 선택하여 Cloudflare 서버를 무시합니다.
  
6. **저장** 을 선택합니다.
  
7. 나머지 5개의 CNAME 레코드를 각각 추가합니다.

    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>전자 메일 스팸 방지에 유용한 SPF용 TXT 레코드 추가
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> 도메인 한 개의 SPF에 둘 이상의 TXT 레코드가 있을 수 없습니다. 도메인에 둘 이상의 SPF 레코드가 있는 경우 전자 메일 오류를 비롯하여 배달 및 스팸 분류 문제가 발생할 수 있습니다. 도메인에 이미 SPF 레코드가 있는 경우 Microsoft 365의 새 SPF 레코드를 만들지 마세요. 대신, 필수 Microsoft 365 값을 현재 레코드에 추가하여 두 값 집합을 모두 포함하는 *단일* SPF 레코드가 있도록 합니다. 
  
1. 시작하려면 이 링크를 사용하여 Cloudflare의 도메인 [페이지로 이동합니다.](https://www.cloudflare.com/a/login) 먼저 로그인하라는 메시지가 표시됩니다.
    
  
2. 홈 **페이지에서** 업데이트할 도메인을 선택합니다. 
  
3. 도메인의 **개요** 페이지에서 **DNS를 선택합니다.**

  
4. DNS 관리 **페이지에서** 레코드 추가를 클릭한 다음 다음 표의 값을 선택합니다.  
    
    |**유형**|**이름**|**TTL**|**콘텐츠**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |30분  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **참고:** 모든 공백이 올바르게 유지되도록 이 항목을 복사하여 붙여 넣는 것이 좋습니다.   |

 
5. **저장** 을 선택합니다.
    

  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Microsoft 필요한 2개의 SRV 레코드 추가하기
<a name="BKMK_add_SRV"> </a>

> [!IMPORTANT]
> Cloudflare는 이 기능을 사용할 수 있도록 하는 책임이 있습니다. 아래 단계와 현재 Cloudflare GUI(그래픽 사용자 인터페이스) 간에 불일치가 표시될 경우 [Cloudflare 커뮤니티를 활용하세요.](https://community.cloudflare.com/) 

1. 시작하려면 이 링크를 사용하여 Cloudflare의 도메인 [페이지로 이동합니다.](https://www.cloudflare.com/a/login) 먼저 로그인하라는 메시지가 표시됩니다.
      
2. 홈 **페이지에서** 업데이트할 도메인을 선택합니다. 
  
3. 도메인의 **개요** 페이지에서 **DNS를 선택합니다.**
  
4. 처음 2개의 SRV 레코드를 추가합니다.

    DNS 관리 **페이지에서** 레코드 추가를 클릭한 다음 다음 표의 첫 번째 행에서 값을 선택합니다.
        
    |**유형**|**서비스**|**프로토콜**|**이름**|**TTL**|**Priority(우선 순위)**|**Weight(가중치)**|**Port(포트)**|**대상**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV|_sip |TLS |사용자 *domain_name;* 예를 들어 contoso.com  |30분 | 100|1  |443 |sipfed.online.lync.com  |
    |SRV|_sipfederationtls | TCP|사용자 *domain_name;* 예를 들어 contoso.com   |30분 |100 |1  |5061 | sipfed.online.lync.com |

  
5. **저장** 을 선택합니다.

  
6. 표의 두 번째 행에서 값을 선택하여 다른 SRV 레코드를 추가합니다. 

    
> [!NOTE]
>  일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요. 
  
