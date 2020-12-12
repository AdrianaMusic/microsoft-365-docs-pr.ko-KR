---
title: Hostgator에서 이름 서퍼를 변경하여 Microsoft 설정
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
ms.assetid: f3bd3c62-0477-48e4-b2b5-21e329d67985
description: Hostgator에서 사용자 지정 도메인의 DNS 레코드를 관리하기 위해 Microsoft를 설정하는 방법에 대해 자세히 알아보습니다.
ms.openlocfilehash: 34e7bbe3abc084185f72f4fef004ad891492ef3c
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658023"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-hostgator"></a>Hostgator에서 이름 서퍼를 변경하여 Microsoft 365 설정

 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요.
  
Microsoft에서 DNS 레코드를 관리하게 하려는 경우 다음 지침을 따릅니다. 원하는 경우 [Hostgator에서 모든 Microsoft DNS 레코드를 관리할 수 있습니다.](create-dns-records-at-hostgator.md)
  
    
## <a name="point-your-domain-to-your-hosting-account"></a>도메인을 호스팅 계정에 연결합니다.

> [!IMPORTANT]
> **확인을 위해 TXT 레코드 추가** 구역의 절차를 수행하기 전에 이 절차를 수행해야 합니다.
  
이러한 단계에 따라 도메인 및 호스팅 계정을 연결합니다.
  
1. 시작하려면 [이 링크](https://portal.hostgator.com/domain/manage)를 사용하여 Hostgator의 고객 포털 페이지로 이동합니다. 로그인하라는 메시지가 표시됩니다.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. 도메인 **탭을** 선택합니다.
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. 도메인 관리 **페이지의** **내** 도메인 영역에서 업데이트할 도메인을 선택합니다.
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. 도메인 개요 **페이지의** 이름 서버 **영역에서** 변경을 **선택합니다.**
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. 도메인의 **이름 서버** 페이지의 호스팅 계정  선택 드롭다운 목록에서 도메인과  연결된 호스팅 계정을 선택합니다.
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. 이름 **서버 저장을 선택합니다.**
    
    ![Hostgator-BP-Redelegate-1-9](../../media/b52a825a-6d54-49ba-87c8-52f770fdfa0c.png)
  
## <a name="add-a-txt-record-for-verification"></a>확인을 위해 TXT 레코드 추가

> [!IMPORTANT]
> 이 절차를 수행하기 전에 먼저 이 문서의 첫 번째 섹션에 있는 절차를 수행해야 합니다. 도메인을 호스팅 계정을 [지정합니다.](#point-your-domain-to-your-hosting-account)
  
Microsoft에서 사용자 도메인을 사용하려면 먼저 도메인을 소유하고 있어야 합니다. 도메인 등록 기관에서 사용자의 계정으로 로그인하고 DNS 레코드를 만들 수 있으면 Microsoft에 도메인을 소유하고 있음을 증명할 수 있습니다.
  
> [!NOTE]
> 이 레코드는 사용자가 도메인을 소유하고 있는지 확인하는 데만 사용되며 그 밖에 아무런 영향도 주지 않습니다. 원하는 경우 나중에 삭제할 수 있습니다.
  
1. 시작하려면 Hostgator의 cPanel 페이지로 이동합니다. 먼저 로그인하라는 메시지가 표시됩니다.
    
    (Hostgator에서 호스팅되는 각 계정에는 고유 cPanel 주소가 할당되어 있습니다. cPanel 주소의 형식은 https://YourSiteAddress:secure-port-number와 같습니다. Hostgator에서 보낸 등록 전자 메일에 이 주소가 명시되어 있습니다.)
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. 시작하려면 Hostgator에서 호스팅 계정을 구입하거나 Microsoft를 지점으로 하는 [도메인의 NS(이름 서비스)](#change-your-domains-nameserver-ns-records) 레코드를 변경할 수 있습니다. 
  
2. 제어판 **페이지의** **도메인** 영역에서 고급 DNS 영역 **편집기를 선택합니다.**
    
    (아래로 스크롤해야 할 수 있습니다.) 
    
3. On the **Advanced DNS Zone Editor** page, in the **Add a Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (드롭다운 목록에서 **Type(종류)** 값을 선택합니다.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**이름** <br/> |**TTL** <br/> |**종류** <br/> |**TXT 데이터** <br/> |
|사용자의  *domain_name*  (예: fourthcoffee.com)을 사용합니다.<br/> **이 값은 마침표(.)로 끝나야 합니다.** <br/> |1   <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **참고:** 이 값은 예시입니다. 여기에는 표에 있는 특정 **대상 또는 주소 가리키기** 값을 사용합니다. [이 값을 찾는 방법](../get-help-with-domains/information-for-dns-records.md)     <br/>  |
   
4. 레코드 **추가를 선택합니다.**
    
5. 방금 만든 레코드가 인터넷에서 업데이트될 수 있도록 몇 분 정도 기다립니다.
    
이제 도메인 등록 기관의 사이트에 레코드를 추가한 후 Microsoft로 돌아가서 레코드에 대한 검색을 요청합니다.
  
Microsoft에서 올바른 TXT 레코드를 찾으면 도메인이 확인된 것입니다.
  
1. I관리 센터에서 **설정** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"> 도메인</a> 페이지로 이동하십시오.

    
2. **도메인** 페이지에서 확인 중인 도메인을 선택합니다. 
    
3. **설정** 페이지에서 **설정 시작** 을 선택합니다.
    
4. **도메인 확인** 페이지에서 **확인** 을 선택합니다.
    
> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름 또는 기타 문제가 발생하는 경우 [도메인 또는 DNS 레코드를 추가한 후 문제 찾기 및 해결하기](../get-help-with-domains/find-and-fix-issues.md)를 참조하세요. 
  
## <a name="change-your-domains-nameserver-ns-records"></a>도메인의 NS(이름 서버) 레코드 변경

Microsoft에서 도메인 설정을 완료하려면 도메인 등록 기관에서 Microsoft 기본 및 보조 이름 서버를 설정하기 위해 도메인의 NS 레코드를 변경합니다. 이렇게 하면 도메인의 DNS 레코드가 자동으로 업데이트됩니다. 전자 메일, 비즈니스용 Skype Online, 공개 웹 사이트가 사용자의 도메인을 사용하도록 모든 레코드가 자동으로 추가되고 모든 설정이 완료됩니다.
  
> [!CAUTION]
> Microsoft 이름 서버를 설정하기 위해 도메인의 NS 레코드를 변경하면 현재 도메인과 연결된 모든 서비스가 영향을 받는 것입니다. 예를 들어 도메인으로 전송된 모든 전자 메일(예: rob@ *your_domain*  .com)은 이 변경 후에 Microsoft로 전송됩니다.
  
> [!IMPORTANT]
> 다음 절차에서는 원치 않는 다른 이름 서스터를 목록에서 삭제하는 방법과 올바른 이름 서비스(아직 나열되지 않은 경우)를 추가하는 방법을 보여 합니다. 이 섹션의 단계를 완료하면 나열해야 하는 이름 ns1.bdm.microsoftonline.com, ns2.bdm.microsoftonline.com, ns3.bdm.microsoftonline.com 및 **ns4.bdm.microsoftonline.com.**  
  
1. 시작하려면 [이 링크](https://portal.hostgator.com/domain/manage)를 사용하여 Hostgator의 고객 포털 페이지로 이동합니다. 로그인하라는 메시지가 표시됩니다.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. 도메인 **탭을** 선택합니다. 
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. 도메인 관리 **페이지의** **내** 도메인 영역에서 업데이트할 도메인을 선택합니다. 
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. 도메인 개요 **페이지의** 이름 서버 **영역에서** 변경을 **선택합니다.**
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. 도메인의 **이름 서버** 페이지의 호스팅 계정  선택 드롭다운 목록에서 도메인과  연결된 호스팅 계정을 선택합니다. 
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. 내 **이름 서버를 수동으로 설정하십시오.**
    
    ![Hostgator-BP-Redelegate-1-5](../../media/5b73ae32-f26e-48aa-b5ad-6da20f1c491a.png)
  
7.   **주의:** 네 개의 올바른 이름 서비스 외의 기존 이름 서포터가 있는 경우 다음 단계를 수행합니다. 즉, 이름이 **ns1.bdm.microsoftonline.com,** ns2.bdm.microsoftonline.com, ns3.bdm.microsoftonline.com  또는 ns4.bdm.microsoftonline.com **이름** 없는 모든 현재 이름 ns4.bdm.microsoftonline.com 삭제합니다.
  
        계속 도메인에 대한 **이름 서버** 페이지의 이름 서버 목록에서 각 이름 서버를 선택하고 키보드에서 **Delete** 키를 눌러 삭제합니다. 
    
   ![Hostgator-BP-Redelegate-1-6](../../media/fa9820e7-28bb-4792-b16c-51e54d83feb1.png)
  
8. 계속 이름 서버 목록에서 다음 표의 처음 두 개의 값을 입력하거나 복사하여 붙여넣습니다.
    
|||
|:-----|:-----|
|**이름 서버 1:** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**이름 서버 2:** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**이름 서버 3:** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**이름 서버 4:** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Hostgator-BP-Redelegate-1-7-1](../../media/a8c10aa7-30b0-4bc8-9596-20256d396274.png)
  
9. 다른 이름 서버 값을 추가합니다.
    
    Select **(+)** add, and then type or copy and paste the value from the next row of the table into the box for the record. 
    
    4개의 이름 서버 레코드를 모두 만들 때까지 이 과정을 반복합니다.
    
    ![Hostgator-BP-Redelegate-1-7-2](../../media/92159a39-e498-4220-9b0d-ae2e718c7fb9.png)
  
10. 이름 **서버 저장을 선택합니다.**
    
    ![Hostgator-BP-Redelegate-1-8](../../media/bd6b0dfa-5d39-4805-970d-7ab153cff117.png)
  
> [!NOTE]
> 이름 서버 레코드 업데이트가 인터넷의 DNS 시스템 전체에 업데이트되기까지 몇 시간이 걸릴 수 있습니다. 그런 다음 Microsoft 전자 메일 및 기타 서비스가 모두 도메인에서 작동하게 설정됩니다.
