---
title: 도메인이 Google에서 관리되는 경우 DNS 레코드 만들기(eNom)
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
ms.assetid: 3c490fbf-7833-4e43-be34-ed0dc3cce5e3
description: ENom에 액세스하고 Google 도메인 페이지를 통해 DNS를 만드는 방법을 배워야 합니다.
ms.openlocfilehash: 3294be667653c568fbbd1a911bcfab9b6ea7788b
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49656858"
---
# <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>도메인이 Google에서 관리되는 경우 DNS 레코드 만들기(eNom)

 원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요. 
  
메일 계정을 Microsoft로 마이그레이션하려면 도메인 등록 기관에 DNS 레코드를 만들어야 합니다.
  
Google Apps for Work 계정에 등록하는 동안 **Google을** 통해 도메인을 구입한 경우 DNS 레코드는 Google에서 관리되지만 eNom으로 등록됩니다. 
  
Google **Domains** 페이지를 통해 eNom에 액세스하고 DNS를 만들 수 있습니다. 이 문서의 단계를 수행하면 됩니다. 
  
## <a name="create-the-dns-record"></a>DNS 레코드 만들기

1. Google [관리 콘솔에서](https://www.google.com/work/apps/business) **로그인을 선택합니다.**
    
    ![Google-Apps-Configure-1-1-0](../../media/37a6e9f6-319e-4c02-aa18-d8d06df7953d.png)
  
2. 도메인 이름을 입력하고 이동을 **선택합니다.**
    
    ![Google-Apps-Configure-1-1-1](../../media/2caf8dcb-4d40-4cfa-bc40-d634e454e699.png)
  
3. At the bottom of the page, select **More controls.**
    
    ![Google-Apps-Configure-1-2-0](../../media/1518ff78-035b-423e-85a3-c16d7faa0968.png)
  
4. **도메인** 을 선택합니다.
    
    ![Google-Apps-Configure-1-2-1](../../media/c2972c06-9bca-43bd-9876-2cee63043bf1.png)
  
5. 도메인 **페이지에서** 도메인 **추가/제거를 선택합니다.**
    
    ![Google-Apps-Configure-1-2-2](../../media/07b8068f-9a05-40aa-a041-fc495c729a18.png)
  
6. 도메인 **페이지에서** **고급 DNS 설정을 선택합니다.**
    
    > [!NOTE]
    > **Google Apps for Work** 계정에 등록하는 동안 Google을 통해 도메인 이름을 구입하지 않은 경우 **도메인** 페이지에 **고급 DNS 설정** 이 없습니다. 대신 도메인 호스트 웹 사이트로 바로 이동하여 DNS 설정에 액세스한 다음 이 작업과 다음 단계를 수행해야 합니다. 자세한 [내용은 G Suite 도메인 설정 액세스를](https://support.google.com/a/answer/54693?hl=en) 참조하세요. 
  
    ![Google-Apps-eNom-Configure-1-3](../../media/b244b29c-e479-40be-b380-4ffa0f74b421.png)
  
7. 고급 **DNS 설정 페이지에서** **DNS 콘솔에 로그인을 선택합니다.** **로그인 이름** 및 **암호** 정보를 확인합니다. 이 정보는 다음 단계에서 필요합니다. 
    
    ![Google-Apps-eNom-Configure-1-4](../../media/056a2767-462f-4847-acee-d01e3f773add.png)
  
8. **고급 DNS 설정** 페이지에서 **로그인 이름** 및 **암호** 를 사용하여 Google **도메인 관리자** 에 로그인합니다. 
    
    ![Google-Apps-eNom-Configure-1-5](../../media/08b74652-8cdb-4560-a5fd-0899f86deee8.png)
  
9. **_domain_name_ _ 페이지의 _ 호스트 레코드 *섹션에서*** 편집을 **선택합니다.**
    
    ![Google-Apps-eNom-Configure-1-6](../../media/d54fec18-b9d1-4796-8397-0393c964eade.png)
  
10. 호스트 레코드 **섹션에서** 새로 **추가를 선택합니다.**
    
    ![Google-Apps-eNom-Configure-1-7](../../media/3562806a-4328-4e60-a717-0566841204cf.png)
  
11. 새 레코드의 상자에서 다음 표의 값을 입력하거나 복사하여 붙여넣습니다.
    
    |**호스트**|**TXT VALUE**|**레코드 종류**|
    |:-----|:-----|:-----|
    |@  <br/> ||TXT  <br/> |

    > [!NOTE]
    > This is an example. 여기에는 표에 있는 특정 **대상 또는 주소 가리키기** 값을 사용합니다. 
  
    [이 값을 찾는 방법](../get-help-with-domains/information-for-dns-records.md)
  
12. **저장** 을 선택합니다.
    
    ![Google-Apps-eNom-Configure-1-9](../../media/7a6f7b45-8f79-487b-afe4-05949c2c04e8.png)
  
13. 변경 **내용 저장을 선택합니다.**
    
    ![Google-Apps-Configure-1-11](../../media/7f321236-33fb-4a7d-9d03-26605e9e558c.png)
  
> [!NOTE]
>  일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요. 
  
