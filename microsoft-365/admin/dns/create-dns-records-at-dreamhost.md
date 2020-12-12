---
title: Microsoft용 에코스트에서 DNS 레코드 만들기
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
ms.assetid: 9c0812e0-908b-4b41-a64b-77f0dbd3db7a
description: 전자 메일, 비즈니스용 Skype Online 및 기타 서비스에 대한 DNS 레코드를 Microsoft에 대해 도메인을 확인하고 이 서비스에 대한 DNS 레코드를 설정하는 방법을 배워야 합니다.
ms.openlocfilehash: 2faf7cae1fd9a0f9308e303c0588958e56b223e1
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658126"
---
# <a name="create-dns-records-at-dreamhost-for-microsoft"></a><span data-ttu-id="ff470-103">Microsoft용 에코스트에서 DNS 레코드 만들기</span><span class="sxs-lookup"><span data-stu-id="ff470-103">Create DNS records at Dreamhost for Microsoft</span></span>

 <span data-ttu-id="ff470-104">원하는 정보를 찾지 못한 경우 **[도메인 FAQ를 확인](../setup/domains-faq.yml)** 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-104">**[Check the Domains FAQ](../setup/domains-faq.yml)** if you don't find what you're looking for.</span></span> 
  
<span data-ttu-id="ff470-105">Dns 호스팅 공급자로인 경우 이 문서의 단계에 따라 도메인을 확인하고 전자 메일, Lync에 대한 DNS 레코드를 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-105">If DreamHost is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Lync, and so on.</span></span>
 
<span data-ttu-id="ff470-106">TheseHost에서 이러한 레코드를 추가하고 나면 도메인이 Microsoft 서비스에서 작동할 수 있도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-106">After you add these records at DreamHost, your domain will be set up to work with Microsoft services.</span></span>
  
  
> [!NOTE]
> <span data-ttu-id="ff470-p101">일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-p101">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  
## <a name="add-a-txt-record-for-verification"></a><span data-ttu-id="ff470-110">확인을 위해 TXT 레코드 추가</span><span class="sxs-lookup"><span data-stu-id="ff470-110">Add a TXT record for verification</span></span>
<span data-ttu-id="ff470-111"><a name="BKMK_verify"> </a></span><span class="sxs-lookup"><span data-stu-id="ff470-111"><a name="BKMK_verify"> </a></span></span>

<span data-ttu-id="ff470-p102">Microsoft에서 사용자 도메인을 사용하려면 먼저 도메인을 소유하고 있어야 합니다. 도메인 등록 기관에서 사용자의 계정으로 로그인하고 DNS 레코드를 만들 수 있으면 Microsoft에 도메인을 소유하고 있음을 증명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-p102">Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ff470-p103">이 레코드는 사용자가 도메인을 소유하고 있는지 확인하는 데만 사용되며 그 밖에 아무런 영향도 주지 않습니다. 원하는 경우 나중에 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-p103">This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.</span></span> 
  
1. <span data-ttu-id="ff470-116">To get started, go to your domains page at호st by using [this link.](https://panel.dreamhost.com/)</span><span class="sxs-lookup"><span data-stu-id="ff470-116">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="ff470-117">로그인하라는 메시지가 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-117">You'll be prompted to Sign in.</span></span>
    
    ![연산 고스트-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="ff470-119">대시보드 **페이지에서** 도메인을 선택한 다음 **도메인을 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-119">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![연산 고스트-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="ff470-121">도메인 **관리** 페이지의 **도메인** 섹션에서 편집할 도메인의 **DNS를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-121">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![연산 고스트-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="ff470-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span><span class="sxs-lookup"><span data-stu-id="ff470-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span></span> 
    
    <span data-ttu-id="ff470-124">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="ff470-124">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="ff470-125">(드롭다운 목록에서 **Type(종류)** 값을 선택합니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-125">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="ff470-126">**이름**</span><span class="sxs-lookup"><span data-stu-id="ff470-126">**Name**</span></span>|<span data-ttu-id="ff470-127">**Type(종류)**</span><span class="sxs-lookup"><span data-stu-id="ff470-127">**Type**</span></span>|<span data-ttu-id="ff470-128">**값**</span><span class="sxs-lookup"><span data-stu-id="ff470-128">**Value**</span></span>|<span data-ttu-id="ff470-129">**설명**</span><span class="sxs-lookup"><span data-stu-id="ff470-129">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="ff470-130">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="ff470-130">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="ff470-131">TXT</span><span class="sxs-lookup"><span data-stu-id="ff470-131">TXT</span></span>  <br/> |<span data-ttu-id="ff470-132">MS=ms *XXXXXXXX*</span><span class="sxs-lookup"><span data-stu-id="ff470-132">MS=ms *XXXXXXXX*</span></span>  <br/> <span data-ttu-id="ff470-133">**참고:** 이 값은 예시입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-133">**Note:** This is an example.</span></span> <span data-ttu-id="ff470-134">여기에는 표에 있는 특정 **대상 또는 주소 가리키기** 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-134">Use your specific **Destination or Points to Address** value here, from the table.</span></span>           [<span data-ttu-id="ff470-135">이 값을 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="ff470-135">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |<span data-ttu-id="ff470-136">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-136">(This field is optional.)</span></span>  <br/> |
   
   ![연산 고스트-BP-Verify-1-1](../../media/ed4a7d43-eeeb-4ec8-849c-37f81315dc69.png)
  
5. <span data-ttu-id="ff470-138">지금 **레코드 추가를 선택합니다!**</span><span class="sxs-lookup"><span data-stu-id="ff470-138">Select **Add Record Now!**</span></span>
    
    ![연산 고스트-BP-Verify-1-2](../../media/5b89c89b-3a8e-4624-895a-86f3cc4638f6.png)
  
6. <span data-ttu-id="ff470-140">방금 만든 레코드가 인터넷에서 업데이트될 수 있도록 몇 분 정도 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-140">Wait a few minutes before you continue, so that the record you just created can update across the Internet.</span></span>
    
<span data-ttu-id="ff470-141">이제 도메인 등록 기관에 레코드가 추가되었습니다. Microsoft로 돌아가서 레코드를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-141">Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record.</span></span>
  
<span data-ttu-id="ff470-142">Microsoft에서 올바른 TXT 레코드를 찾으면 도메인이 확인된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-142">When Microsoft finds the correct TXT record, your domain is verified.</span></span>
  
1. <span data-ttu-id="ff470-143">Microsoft 관리 센터에서 **설정** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">도메인</a> 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-143">In the Microsoft admin center, go to the **Settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.</span></span>

    
2. <span data-ttu-id="ff470-144">**도메인** 페이지에서 확인 중인 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-144">On the **Domains** page, select the domain that you are verifying.</span></span> 
    
    
  
3. <span data-ttu-id="ff470-145">**설정** 페이지에서 **설정 시작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-145">On the **Setup** page, select **Start setup**.</span></span>
    
    
  
4. <span data-ttu-id="ff470-146">**도메인 확인** 페이지에서 **확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-146">On the **Verify domain** page, select **Verify**.</span></span>
    
    
  
> [!NOTE]
>  <span data-ttu-id="ff470-p106">일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-p106">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="ff470-150">사용자 도메인의 전자 메일이 Microsoft로 전송되도록 MX 레코드 추가하기</span><span class="sxs-lookup"><span data-stu-id="ff470-150">Add an MX record so email for your domain will come to Microsoft</span></span>
<span data-ttu-id="ff470-151"><a name="BKMK_add_MX"> </a></span><span class="sxs-lookup"><span data-stu-id="ff470-151"><a name="BKMK_add_MX"> </a></span></span>

<span data-ttu-id="ff470-152">아래 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-152">Follow the steps below.</span></span>
  
1. <span data-ttu-id="ff470-153">To get started, go to your domains page at호st by using [this link.](https://panel.dreamhost.com/)</span><span class="sxs-lookup"><span data-stu-id="ff470-153">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="ff470-154">로그인하라는 메시지가 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-154">You'll be prompted to Sign in.</span></span>
    
    ![연산 고스트-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="ff470-156">대시보드 **페이지에서** 메일을 **선택한** 다음 사용자 지정 **MX를 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-156">On the **Dashboard** page, select **Mail**, and then **Custom MX**.</span></span>
    
    ![연산 고스트-BP-Configure-2-1](../../media/58478679-4018-49cc-9d83-371dc5fa4a22.png)
  
3. <span data-ttu-id="ff470-158">메일 배달 **관리 섹션의** **작업** 열에서  편집할 도메인에 대해 편집을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-158">In the **Manage Mail Delivery** section, in the **Actions** column, select **Edit** for the domain that you want to edit.</span></span> 
    
    ![연산 고스트-BP-Configure-2-2](../../media/6eed0be2-6477-4f49-9f90-39e190499a53.png)
  
4. <span data-ttu-id="ff470-160">사용자 지정 **MX 레코드** 섹션의 새 레코드용 상자에 다음 표의 다음 값을 입력하거나 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-160">In the **Custom MX Record** section, in the boxes for the new record, type or copy and paste the following values from the following table.</span></span> 
    
    <span data-ttu-id="ff470-161">(아래로 스크롤해야 할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-161">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="ff470-162">(다른 기존 MX 레코드가 있는 경우 삭제될 레코드를 표시하십시오.)</span><span class="sxs-lookup"><span data-stu-id="ff470-162">(If there are any other existing MX records, mark those records to be deleted.)</span></span>
    
    |<span data-ttu-id="ff470-163">**MX 레코드(필수)**</span><span class="sxs-lookup"><span data-stu-id="ff470-163">**MX Record (required)**</span></span>|
    |:-----|
    |<span data-ttu-id="ff470-164">0  *\<domain-key\>*  .mail.protection.outlook.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-164">0  *\<domain-key\>*  .mail.protection.outlook.com.</span></span>  <br/> <span data-ttu-id="ff470-165">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-165">**This value MUST end with a period (.)**</span></span> <br/> <span data-ttu-id="ff470-p108">0은 MX 우선 순위 값입니다. 이 값을 MX 값 시작 부분에 추가하고 나머지 값과 공백으로 구분합니다.  </span><span class="sxs-lookup"><span data-stu-id="ff470-p108">The 0 is the MX priority value. Add it to the beginning of the MX value, separated from the remainder of the value by a space.  </span></span><br/> <span data-ttu-id="ff470-168">**참고:** Microsoft  *\<domain-key\>*  계정에서 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-168">**Note:** Get your  *\<domain-key\>*  from your Microsoft account.</span></span>           [<span data-ttu-id="ff470-169">이 값을 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="ff470-169">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![연산 고스트-BP-Configure-2-3](../../media/90da1816-e186-4016-ab22-7962f8b86add.png)
  
5. <span data-ttu-id="ff470-171">지금 **사용자 지정 MX 레코드를 사용하려면 이 도메인 변경을 선택합니다!**</span><span class="sxs-lookup"><span data-stu-id="ff470-171">Select **Change this domain to use custom MX records now!**</span></span>
    
    ![연산 고스트-BP-Configure-2-4](../../media/3221c767-83d3-4f30-9d08-dc998772d2a3.png)
  
6. <span data-ttu-id="ff470-173">다른 기존 MX 레코드가 있는 경우 항목을 선택한 다음 키보드에서 **Delete** 키를 눌러 각 레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-173">If there are any other existing MX records, delete each record by selecting the entry and then pressing the **Delete** key on your keyboard.</span></span> 
    
    ![연산 고스트-BP-Configure-2-5](../../media/1827733c-3609-4b0f-bba1-531ab090da91.png)
  
7. <span data-ttu-id="ff470-175">레코드를 삭제한 경우 지금 사용자 지정 MX 레코드 **업데이트를 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-175">If you have deleted any records, select **Update your custom MX records now!**</span></span>
    
    ![연산 고스트-BP-Configure-2-6](../../media/177462be-0686-47b7-a389-025dfc8d6526.png)

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a><span data-ttu-id="ff470-177">Microsoft에 필요한 6개의 CNAME 레코드 추가</span><span class="sxs-lookup"><span data-stu-id="ff470-177">Add the six CNAME records that are required for Microsoft</span></span>
<span data-ttu-id="ff470-178"><a name="BKMK_add_CNAME"> </a></span><span class="sxs-lookup"><span data-stu-id="ff470-178"><a name="BKMK_add_CNAME"> </a></span></span>

<span data-ttu-id="ff470-179">아래 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-179">Follow the steps below.</span></span>
  
1. <span data-ttu-id="ff470-180">To get started, go to your domains page at호st by using [this link.](https://panel.dreamhost.com/)</span><span class="sxs-lookup"><span data-stu-id="ff470-180">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="ff470-181">로그인하라는 메시지가 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-181">You'll be prompted to Sign in.</span></span>
    
    ![연산 고스트-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="ff470-183">대시보드 **페이지에서** 도메인을 선택한 다음 **도메인을 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-183">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![연산 고스트-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="ff470-185">도메인 **관리** 페이지의 **도메인** 섹션에서 편집할 도메인의 **DNS를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-185">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![연산 고스트-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="ff470-187">사용자 지정 **DNS** 레코드 추가 섹션의 새 레코드용 상자에 다음 표의 첫 번째 행 값을 입력하거나 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-187">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="ff470-188">(아래로 스크롤해야 할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-188">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="ff470-189">(드롭다운 목록에서 **Type(종류)** 값을 선택합니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-189">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="ff470-190">**이름**</span><span class="sxs-lookup"><span data-stu-id="ff470-190">**Name**</span></span>|<span data-ttu-id="ff470-191">**Type(종류)**</span><span class="sxs-lookup"><span data-stu-id="ff470-191">**Type**</span></span>|<span data-ttu-id="ff470-192">**값**</span><span class="sxs-lookup"><span data-stu-id="ff470-192">**Value**</span></span>|<span data-ttu-id="ff470-193">**설명**</span><span class="sxs-lookup"><span data-stu-id="ff470-193">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="ff470-194">autodiscover</span><span class="sxs-lookup"><span data-stu-id="ff470-194">autodiscover</span></span>  <br/> |<span data-ttu-id="ff470-195">CNAME</span><span class="sxs-lookup"><span data-stu-id="ff470-195">CNAME</span></span>  <br/> |<span data-ttu-id="ff470-196">autodiscover.outlook.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-196">autodiscover.outlook.com.</span></span>  <br/> <span data-ttu-id="ff470-197">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-197">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-198">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-198">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="ff470-199">sip</span><span class="sxs-lookup"><span data-stu-id="ff470-199">sip</span></span>  <br/> |<span data-ttu-id="ff470-200">CNAME</span><span class="sxs-lookup"><span data-stu-id="ff470-200">CNAME</span></span>  <br/> |<span data-ttu-id="ff470-201">sipdir.online.lync.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-201">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="ff470-202">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-202">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-203">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-203">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="ff470-204">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="ff470-204">lyncdiscover</span></span>  <br/> |<span data-ttu-id="ff470-205">CNAME</span><span class="sxs-lookup"><span data-stu-id="ff470-205">CNAME</span></span>  <br/> |<span data-ttu-id="ff470-206">webdir.online.lync.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-206">webdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="ff470-207">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-207">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-208">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-208">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="ff470-209">enterpriseregistration</span><span class="sxs-lookup"><span data-stu-id="ff470-209">enterpriseregistration</span></span>  <br/> |<span data-ttu-id="ff470-210">CNAME</span><span class="sxs-lookup"><span data-stu-id="ff470-210">CNAME</span></span>  <br/> |<span data-ttu-id="ff470-211">enterpriseregistration.windows.net.</span><span class="sxs-lookup"><span data-stu-id="ff470-211">enterpriseregistration.windows.net.</span></span>  <br/> <span data-ttu-id="ff470-212">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-212">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-213">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-213">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="ff470-214">enterpriseenrollment</span><span class="sxs-lookup"><span data-stu-id="ff470-214">enterpriseenrollment</span></span>  <br/> |<span data-ttu-id="ff470-215">CNAME</span><span class="sxs-lookup"><span data-stu-id="ff470-215">CNAME</span></span>  <br/> |<span data-ttu-id="ff470-216">enterpriseenrollment-s.manage.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-216">enterpriseenrollment-s.manage.microsoft.com.</span></span>  <br/> <span data-ttu-id="ff470-217">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-217">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-218">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-218">(This field is optional.)</span></span>  <br/> |
   
    ![연산 고스트-BP-Configure-3-1](../../media/0c4cc587-ea24-47f2-8dc6-a35735b250e6.png)
  
5. <span data-ttu-id="ff470-220">지금 **레코드 추가를 선택합니다!**</span><span class="sxs-lookup"><span data-stu-id="ff470-220">Select **Add Record Now!**</span></span>
    
    ![연산 고스트-BP-Configure-3-2](../../media/b5d4f939-de6d-4d1f-a20a-4eb5fe715281.png)
  
6. <span data-ttu-id="ff470-222">앞의 두 단계와 표에 있는 다른 다섯 행의 값을 사용하여 다른 5개의 CNAME 레코드를 각각 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-222">Using the preceding two steps and the values from the other five rows in the table, add each of the other five CNAME records.</span></span>

  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a><span data-ttu-id="ff470-223">전자 메일 스팸 방지에 유용한 SPF용 TXT 레코드 추가</span><span class="sxs-lookup"><span data-stu-id="ff470-223">Add a TXT record for SPF to help prevent email spam</span></span>
<span data-ttu-id="ff470-224"><a name="BKMK_add_TXT"> </a></span><span class="sxs-lookup"><span data-stu-id="ff470-224"><a name="BKMK_add_TXT"> </a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff470-225">도메인 한 개의 SPF에 둘 이상의 TXT 레코드가 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-225">You cannot have more than one TXT record for SPF for a domain.</span></span> <span data-ttu-id="ff470-226">도메인에 둘 이상의 SPF 레코드가 있는 경우 전자 메일 오류를 비롯하여 배달 및 스팸 분류 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-226">If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues.</span></span> <span data-ttu-id="ff470-227">도메인에 이미 SPF 레코드가 있는 경우 Microsoft의 새 SPF 레코드를 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-227">If you already have an SPF record for your domain, don't create a new one for Microsoft.</span></span> <span data-ttu-id="ff470-228">대신 두 값 집합을 모두 포함하는  *단일*  SPF 레코드가 있도록 현재 레코드에 필요한 Microsoft 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-228">Instead, add the required Microsoft values to the current record so that you have a  *single*  SPF record that includes both sets of values.</span></span>
  
<span data-ttu-id="ff470-229">아래 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-229">Follow the steps below.</span></span>
  
1. <span data-ttu-id="ff470-230">To get started, go to your domains page at호st by using [this link.](https://panel.dreamhost.com/)</span><span class="sxs-lookup"><span data-stu-id="ff470-230">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="ff470-231">로그인하라는 메시지가 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-231">You'll be prompted to Sign in.</span></span>
    
    ![연산 고스트-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="ff470-233">대시보드 **페이지에서** 도메인을 선택한 다음 **도메인을 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-233">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![연산 고스트-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="ff470-235">도메인 **관리** 페이지의 **도메인** 섹션에서 편집할 도메인의 **DNS를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-235">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![연산 고스트-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="ff470-237">사용자 지정 **DNS** 레코드 추가 섹션의 새 레코드용 상자에 다음 표의 첫 번째 행 값을 입력하거나 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-237">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="ff470-238">(아래로 스크롤해야 할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-238">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="ff470-239">(드롭다운 목록에서 **Type(종류)** 값을 선택합니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-239">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="ff470-240">**이름**</span><span class="sxs-lookup"><span data-stu-id="ff470-240">**Name**</span></span>|<span data-ttu-id="ff470-241">**Type(종류)**</span><span class="sxs-lookup"><span data-stu-id="ff470-241">**Type**</span></span>|<span data-ttu-id="ff470-242">**값**</span><span class="sxs-lookup"><span data-stu-id="ff470-242">**Value**</span></span>|<span data-ttu-id="ff470-243">**설명**</span><span class="sxs-lookup"><span data-stu-id="ff470-243">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="ff470-244">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="ff470-244">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="ff470-245">TXT</span><span class="sxs-lookup"><span data-stu-id="ff470-245">TXT</span></span>  <br/> |<span data-ttu-id="ff470-246">v=spf1 include:spf.protection.outlook.com -all</span><span class="sxs-lookup"><span data-stu-id="ff470-246">v=spf1 include:spf.protection.outlook.com -all</span></span>  <br/> <span data-ttu-id="ff470-247">**참고:** 모든 공백이 올바르게 유지되도록 이 항목을 복사하여 붙여 넣는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-247">**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct.</span></span>           |<span data-ttu-id="ff470-248">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-248">(This field is optional.)</span></span>  <br/> |
   
   ![연산 고스트-BP-Configure-4-1](../../media/cbc4bbca-bdbc-4dc9-b1b7-b55491eb1e53.png)
  
5. <span data-ttu-id="ff470-250">지금 **레코드 추가를 선택합니다!**</span><span class="sxs-lookup"><span data-stu-id="ff470-250">Select **Add Record Now!**</span></span>
    
    ![연산 고스트-BP-Configure-4-2](../../media/2bd7cae8-1fbc-4407-8dfa-06ce37c586c0.png)
  
6. <span data-ttu-id="ff470-252">앞의 두 단계와 표의 두 번째 행 값을 사용하여 다른 SRV 레코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-252">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a><span data-ttu-id="ff470-253">Microsoft 필요한 2개의 SRV 레코드 추가하기</span><span class="sxs-lookup"><span data-stu-id="ff470-253">Add the two SRV records that are required for Microsoft</span></span>
<span data-ttu-id="ff470-254"><a name="BKMK_add_SRV"> </a></span><span class="sxs-lookup"><span data-stu-id="ff470-254"><a name="BKMK_add_SRV"> </a></span></span>

<span data-ttu-id="ff470-255">아래 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-255">Follow the steps below.</span></span>
  
1. <span data-ttu-id="ff470-256">To get started, go to your domains page at호st by using [this link.](https://panel.dreamhost.com/)</span><span class="sxs-lookup"><span data-stu-id="ff470-256">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="ff470-257">로그인하라는 메시지가 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-257">You'll be prompted to Sign in.</span></span>
    
    ![연산 고스트-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="ff470-259">대시보드 **페이지에서** 도메인을 선택한 다음 **도메인을 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-259">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![연산 고스트-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="ff470-261">도메인 **관리** 페이지의 **도메인** 섹션에서 편집할 도메인의 **DNS를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-261">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![연산 고스트-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="ff470-263">사용자 지정 **DNS** 레코드 추가 섹션의 새 레코드용 상자에 다음 표의 첫 번째 행 값을 입력하거나 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-263">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="ff470-264">(아래로 스크롤해야 할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-264">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="ff470-265">(드롭다운 목록에서 **Type(종류)** 값을 선택합니다.)</span><span class="sxs-lookup"><span data-stu-id="ff470-265">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="ff470-266">**이름**</span><span class="sxs-lookup"><span data-stu-id="ff470-266">**Name**</span></span>|<span data-ttu-id="ff470-267">**Type(종류)**</span><span class="sxs-lookup"><span data-stu-id="ff470-267">**Type**</span></span>|<span data-ttu-id="ff470-268">**값**</span><span class="sxs-lookup"><span data-stu-id="ff470-268">**Value**</span></span>|<span data-ttu-id="ff470-269">**설명**</span><span class="sxs-lookup"><span data-stu-id="ff470-269">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="ff470-270">_sip._tls</span><span class="sxs-lookup"><span data-stu-id="ff470-270">_sip._tls</span></span>  <br/> |<span data-ttu-id="ff470-271">SRV</span><span class="sxs-lookup"><span data-stu-id="ff470-271">SRV</span></span>  <br/> |<span data-ttu-id="ff470-272">100 1 443</span><span class="sxs-lookup"><span data-stu-id="ff470-272">100 1 443</span></span>  <br/> <span data-ttu-id="ff470-273">sipdir.online.lync.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-273">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="ff470-274">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-274">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-275">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-275">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="ff470-276">_sipfederationtls._tcp</span><span class="sxs-lookup"><span data-stu-id="ff470-276">_sipfederationtls._tcp</span></span>  <br/> |<span data-ttu-id="ff470-277">SRV</span><span class="sxs-lookup"><span data-stu-id="ff470-277">SRV</span></span>  <br/> |<span data-ttu-id="ff470-278">100 1 5061</span><span class="sxs-lookup"><span data-stu-id="ff470-278">100 1 5061</span></span>  <br/> <span data-ttu-id="ff470-279">sipfed.online.lync.com.</span><span class="sxs-lookup"><span data-stu-id="ff470-279">sipfed.online.lync.com.</span></span>  <br/> <span data-ttu-id="ff470-280">**이 값은 마침표(.)로 끝나야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ff470-280">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="ff470-281">이 필드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-281">(This field is optional.)</span></span>  <br/> |
   
    ![연산 고스트-BP-Configure-5-1](../../media/934eb79f-3617-4b72-802c-c42c7d165283.png)
  
5. <span data-ttu-id="ff470-283">Select **Add Record Now!**.</span><span class="sxs-lookup"><span data-stu-id="ff470-283">Select **Add Record Now!**.</span></span>
    
    ![연산 고스트-BP-Configure-5-2](../../media/015bc73c-8f88-49ce-87f9-e5a6ea3e10a8.png)
  
6. <span data-ttu-id="ff470-285">앞의 두 단계와 표의 두 번째 행 값을 사용하여 다른 SRV 레코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ff470-285">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="ff470-p114">일반적으로 DNS 변경 내용을 적용하는 데 15분 정도 걸립니다. 그러나 변경한 내용이 인터넷의 DNS 시스템 전체에 업데이트되는 데에는 시간이 오래 걸릴 수 있습니다. DNS 레코드를 추가한 후 메일 흐름이나 기타 문제가 있는 경우 [도메인 이름 또는 DNS 레코드 변경 후 발생한 문제 해결](../get-help-with-domains/find-and-fix-issues.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff470-p114">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 

  
