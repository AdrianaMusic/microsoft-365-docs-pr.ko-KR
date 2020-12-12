---
title: MyDomain에서 이름 서퍼를 변경하여 Microsoft 설정
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
ms.assetid: c5f6140a-4a12-401b-9bbd-7dfb0d6b0ba3
description: MyDomain에서 사용자 지정 도메인의 DNS 레코드를 관리하기 위해 Microsoft를 설정하는 방법에 대해 자세히 알아보습니다.
ms.openlocfilehash: fbfa3c495f54a9890be6d9c9e31a7878b21f12fe
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658419"
---
# <a name="change-nameservers-to-set-up-microsoft-with-mydomain"></a>MyDomain에서 이름 서퍼를 변경하여 Microsoft 설정

 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요.
  
Microsoft에서 DNS 레코드를 관리하게 하려는 경우 다음 지침을 따릅니다. 원하는 경우 [MyDomain에서 모든 Microsoft DNS 레코드를 관리할 수 있습니다.](create-dns-records-at-mydomain.md)
  
## <a name="add-a-txt-record-for-verification"></a>확인을 위해 TXT 레코드 추가

Microsoft에서 사용자 도메인을 사용하려면 먼저 도메인을 소유하고 있어야 합니다. 도메인 등록 기관에서 사용자의 계정으로 로그인하고 DNS 레코드를 만들 수 있으면 Microsoft에 도메인을 소유하고 있음을 증명할 수 있습니다.
  
> [!NOTE]
> 이 레코드는 사용자가 도메인을 소유하고 있는지 확인하는 데만 사용되며 그 밖에 아무런 영향도 주지 않습니다. 원하는 경우 나중에 삭제할 수 있습니다. 
  
1. 시작하려면 [이 링크](https://www.mydomain.com/controlpanel)를 사용하여 MyDomain의 도메인 페이지로 이동합니다. 먼저 로그인하라는 메시지가 표시됩니다.
    
2. **내 즐겨 찾기** 섹션에서 **도메인 센터** 를 선택합니다.
    
3. **도메인** 에서 편집할 도메인 이름을 선택합니다.
    
4. **개요** 행에서 **DNS** 를 선택합니다.
    
5. **수정** 드롭다운 목록에서 **TXT/SPF 레코드** 를 선택합니다.
    
6. 
            **콘텐츠** 아래의 새 레코드에 대한 상자에 다음 표의 값을 입력하거나 복사하여 붙여넣습니다.
    
||
|:-----|
|**콘텐츠** <br/> |
|MS=ms *XXXXXXXX*  <br/> **참고**: 예시입니다. 여기에는 표에 있는 특정 **대상 또는 주소 가리키기** 값을 사용합니다. [이 값을 찾는 방법](../get-help-with-domains/information-for-dns-records.md)          |
   
7. **추가** 를 선택합니다.
    
8. 방금 만든 레코드가 인터넷에서 업데이트될 수 있도록 몇 분 정도 기다립니다.
    
이제 도메인 등록 기관에 레코드가 추가되었습니다. Microsoft 365로 돌아가서 Microsoft 365에 레코드를 찾을 것을 요청합니다.
  
Microsoft에서 올바른 TXT 레코드를 찾으면 도메인이 확인된 것입니다.
  
1. Microsoft 관리 센터에서 **설정** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">도메인</a> 페이지로 이동합니다.

    
2. **도메인** 페이지에서 확인 중인 도메인을 선택합니다. 
    
3. **설정** 페이지에서 **설정 시작** 을 선택합니다.
    
4. **도메인 확인** 페이지에서 **확인** 을 선택합니다.
    
> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름 또는 기타 문제가 발생하는 경우 [도메인 또는 DNS 레코드를 추가한 후 문제 찾기 및 해결하기](../get-help-with-domains/find-and-fix-issues.md)를 참조하세요. 
  
## <a name="change-your-domains-nameserver-ns-records"></a>도메인의 NS(이름 서버) 레코드 변경

Microsoft에서 도메인 설정을 완료하려면 도메인 등록 기관에서 Microsoft 기본 및 보조 이름 서버를 설정하기 위해 도메인의 NS 레코드를 변경합니다. 이렇게 하면 도메인의 DNS 레코드가 자동으로 업데이트됩니다. 전자 메일, 비즈니스용 Skype Online, 공개 웹 사이트가 사용자의 도메인을 사용하도록 모든 레코드가 자동으로 추가되고 모든 설정이 완료됩니다.
  
> [!CAUTION]
> Microsoft 이름 서버를 설정하기 위해 도메인의 NS 레코드를 변경하면 현재 도메인과 연결된 모든 서비스가 영향을 받는 것입니다. 예를 들어 도메인으로 전송된 모든 전자 메일(예: rob@ *your_domain.* com) 이 변경을 한 후 Microsoft에 다가오기 시작할 것입니다. 
  
> [!IMPORTANT]
> The following procedure will show you how to delete any other, unwanted nameservers from the list, and also how to add the correct nameservers if they are not already in the list. <br/> When you have completed the steps in this section, the only nameservers that should be listed are these four:
  
1. 시작하려면 [이 링크](https://www.mydomain.com/controlpanel)를 사용하여 MyDomain의 도메인 페이지로 이동합니다. 먼저 로그인하라는 메시지가 표시됩니다.
    
2. **내 즐겨 찾기** 섹션에서 **도메인 센터** 를 선택합니다.
    
3. **도메인** 에서 편집할 도메인 이름을 선택합니다.
    
4. 개요 **행에서** **Nameservers를 선택합니다.**
    
    ![MyDomain-BP-Redelegate-1-1](../../media/49e91235-44b5-46d6-a82e-8f11329db3d6.png)
  
5. **Update Name Servers(이름 서버 업데이트)** 구역에서 **Use different name servers(다른 이름 서버 사용)** 을 선택합니다.
    
    ![MyDomain-BP-Redelegate-1-2-1](../../media/f869fb26-54dc-4b66-8378-a78a79b582bd.png)
  
6. 현재 표시된 페이지에 이름Servers가 이미 나열되어 있는지 여부에 따라 다음 두 절차 중 하나를 계속 진행합니다.
    
### <a name="if-the-correct-nameservers-are-already-listed"></a>올바른 이름 서버가 이미 나열되어 있으면

- 올바른 이름 서버가 이미 나열되어 있으면 이 단계를 건너뛸 수 있습니다.
    
    ![MyDomain-BP-Redelegate-1-2-2](../../media/601f6a46-15bd-4a92-b792-ac628ff86628.png)
  
### <a name="if-the-correct-nameservers-are-not-already-listed"></a>올바른 이름 서버가 나열되어 있지 않은 경우

> [!CAUTION]
> Follow these steps only if you have existing nameservers other than the four correct nameservers. 즉, 이름이 **ns1.bdm.microsoftonline.com,** ns2.bdm.microsoftonline.com, ns3.bdm.microsoftonline.com  또는 ns4.bdm.microsoftonline.com **이름** 없는 모든 현재 이름 ns4.bdm.microsoftonline.com 삭제합니다. 
  
1. **Nameserver:**(이름 서버:) 필드에서 각 항목을 선택한 다음 키보드에서 **Delete** 키를 눌러 기존 이름 서버를 삭제합니다. 
    
    ![MyDomain-BP-Redelegate-1-3-1](../../media/5024cd27-a2b1-42a2-99e4-5ceb5e6eddb9.png)
  
2. 두 **번 더 추가를** 선택하여 두 개의 새 이름 서비스 행을 추가합니다. 
    
    ![MyDomain-BP-Redelegate-1-3-2](../../media/19307893-2f73-4e4d-9221-a5870e09ab48.png)
  
3. 레코드의 상자에 다음 표의 이름 서버 값을 입력하거나 복사하여 붙여넣습니다.
    
|||
|:-----|:-----|
|**이름 서버 1** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**이름 서버 2** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**이름 서버 3** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**이름 서버 4** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![MyDomain-BP-Redelegate-1-4](../../media/7427e99c-49c7-4a2e-a5bf-66fc46900cd1.png)
  
4. **저장** 을 선택합니다.
    
    ![MyDomain-BP-Redelegate-1-5](../../media/48473816-b881-47f0-9344-74622efa3bf8.png)
  
> [!NOTE]
> 이름 서버 레코드 업데이트가 인터넷의 DNS 시스템 전체에 업데이트되기까지 몇 시간이 걸릴 수 있습니다. 그런 다음 Microsoft 전자 메일 및 기타 서비스가 모두 도메인에서 작동하게 설정됩니다. 
