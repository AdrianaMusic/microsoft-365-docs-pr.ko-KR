---
title: 콘텐츠의 처리
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 처리 검토를 사용하든 콘텐츠가 구성한 설정에 따라 자동으로 삭제되는지, 콘텐츠의 처리를 모니터링하고 관리합니다.
ms.openlocfilehash: 9c2e9055d0468270df4e46fe39115708762052f3
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682671"
---
# <a name="disposition-of-content"></a><span data-ttu-id="e56d6-103">콘텐츠의 처리</span><span class="sxs-lookup"><span data-stu-id="e56d6-103">Disposition of content</span></span>

><span data-ttu-id="e56d6-104">*[보안 및 규정 준수를 위한 Microsoft 365 라이선싱 지침](https://aka.ms/ComplianceSD).*</span><span class="sxs-lookup"><span data-stu-id="e56d6-104">*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*</span></span>

<span data-ttu-id="e56d6-105">Microsoft 365 준수 센터의 **레코드 관리** 에서 **처리** 탭을 사용하여 처리 검토를 관리하고 보존 기간이 끝날 때 자동으로 삭제된 [레코드](records-management.md#records)를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-105">Use the **Disposition** tab from **Records Management** in the Microsoft 365 compliance center to manage disposition reviews and view [records](records-management.md#records) that have been automatically deleted at the end of their retention period.</span></span> 

## <a name="prerequisites-for-viewing-content-dispositions"></a><span data-ttu-id="e56d6-106">콘텐츠 처리를 보기 위한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e56d6-106">Prerequisites for viewing content dispositions</span></span>

<span data-ttu-id="e56d6-107">처리 검토를 관리하고 레코드가 삭제되었는지 확인하려면 충분한 권한이 필요하고 감사를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-107">To manage disposition reviews and confirm that records have been deleted, you must have sufficient permissions and auditing must be enabled.</span></span>

### <a name="permissions-for-disposition"></a><span data-ttu-id="e56d6-108">처리 권한</span><span class="sxs-lookup"><span data-stu-id="e56d6-108">Permissions for disposition</span></span>

<span data-ttu-id="e56d6-109">Microsoft 365 준수 센터의 **처리** 탭에 액세스하려면 사용자에게 **처리 관리** 관리자 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-109">To successfully access the **Disposition** tab in the Microsoft 365 compliance center, users must have the **Disposition Management** admin role.</span></span> <span data-ttu-id="e56d6-110">2020년 12월부터 이 역할은 이제 **레코드 관리** 기본 관리자 역할 그룹에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-110">From December 2020, this role is now included in the **Records Management** default admin role group.</span></span>

> [!NOTE]
> <span data-ttu-id="e56d6-111">기본적으로 전역 관리자에게 **처리 관리** 역할이 부여되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-111">By default, a global admin isn't granted the **Disposition Management** role.</span></span> 

<span data-ttu-id="e56d6-112">사용자에게 보존 및 레코드 관리를 위한 다른 기능을 보고 구성할 수 있는 권한을 부여하지 않고 처리 검토에 필요한 권한만 부여하려면 사용자 지정 역할 그룹(예: "처리 검토자")을 만들고 이 그룹에 처분 관리 역할을 부여하세요.</span><span class="sxs-lookup"><span data-stu-id="e56d6-112">To grant users just the permissions they need for disposition reviews without granting them permissions to view and configure other features for retention and records management, create a custom role group (for example, named "Disposition Reviewers") and grant this group the Disposition Management role.</span></span>

<span data-ttu-id="e56d6-113">또한 처리 프로세스 중에 항목의 내용을 보려면 **콘텐츠 탐색기 콘텐츠 뷰어** 와 **콘텐츠 탐색기 목록 뷰어** 의 두 역할 그룹에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-113">Additionally, to view the contents of items during the disposition process, add users to the following two role groups: **Content Explorer Content Viewer** and **Content Explorer List Viewer**.</span></span> <span data-ttu-id="e56d6-114">사용자가 이 역할 그룹의 사용 권한이 없는 경우, 처리 검토 완료를 위해 처리 검토 작업을 여전히 선택할 수 있지만, 준수 센터에서 항목의 내용을 볼 수 없는 상태로 이를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-114">If users don't have the permissions from these role groups, they can still select a disposition review action to complete the disposition review, but must do so without being able to view the item's contents from the compliance center.</span></span>

<span data-ttu-id="e56d6-115">이 권한을 구성할 수 있는 지침은 [사용자에게 Office 365 보안 및 준수 센터의 액세스 권한 부여하기](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e56d6-115">For instructions to configure these permissions, see [Give users access to the Office 365 Security & Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).</span></span>

### <a name="enable-auditing"></a><span data-ttu-id="e56d6-116">감사 사용</span><span class="sxs-lookup"><span data-stu-id="e56d6-116">Enable auditing</span></span>

<span data-ttu-id="e56d6-117">첫 처리 작업 최소 하루 이전에 감사를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-117">Make sure that auditing is enabled at least one day before the first disposition action.</span></span> <span data-ttu-id="e56d6-118">자세한 내용은 [Office 365 보안 &amp; 준수 센터에서 감사 로그 검색](search-the-audit-log-in-security-and-compliance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e56d6-118">For more information, see [Search the audit log in the Office 365 Security &amp; Compliance Center](search-the-audit-log-in-security-and-compliance.md).</span></span> 

## <a name="disposition-reviews"></a><span data-ttu-id="e56d6-119">처리 검토</span><span class="sxs-lookup"><span data-stu-id="e56d6-119">Disposition reviews</span></span>

<span data-ttu-id="e56d6-120">콘텐츠가 보존 기간 끝에 도달하면 해당 콘텐츠를 검토하여 안전하게 삭제할 수 있는지 여부를 결정하는 몇 가지 이유가 있습니다("처분").</span><span class="sxs-lookup"><span data-stu-id="e56d6-120">When content reaches the end of its retention period, there are several reasons why you might want to review that content to decide whether it can be safely deleted ("disposed").</span></span> <span data-ttu-id="e56d6-121">예를 들어 다음을 수행해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-121">For example, you might need to:</span></span>
  
- <span data-ttu-id="e56d6-122">소송 또는 감사의 경우에 관련 콘텐츠의 삭제를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-122">Suspend the deletion of relevant content in the event of litigation or an audit.</span></span>
    
- <span data-ttu-id="e56d6-123">해당 콘텐츠에 연구 또는 기록적 가치가 있는 경우 처리 목록에서 콘텐츠를 제거하여 보관함에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-123">Remove content from the disposition list to store in an archive, if that content has research or historical value.</span></span>
    
- <span data-ttu-id="e56d6-124">원래 보존 설정이 임시 혹은 잠정적 솔루션이어서 콘텐츠에 다른 보존 기간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-124">Assign a different retention period to the content, perhaps because the original retention settings were a temporary or provisional solution.</span></span>
    
- <span data-ttu-id="e56d6-125">콘텐츠를 클라이언트에게 반환하거나 다른 조직으로 이전합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-125">Return the content to clients or transfer it to another organization.</span></span>

<span data-ttu-id="e56d6-126">보존 기간이 끝날 때 처리 검토가 트리거되는 경우:</span><span class="sxs-lookup"><span data-stu-id="e56d6-126">When a disposition review is triggered at the end of the retention period:</span></span>
  
- <span data-ttu-id="e56d6-127">선택하는 사용자는 검토할 콘텐츠가 있다는 전자 메일 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-127">The people you choose receive an email notification that they have content to review.</span></span> <span data-ttu-id="e56d6-128">이러한 검토자는 개별 사용자 또는 메일 사용이 가능한 보안 그룹이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-128">These reviewers can be individual users or mail-enabled security groups.</span></span> <span data-ttu-id="e56d6-129">알림은 주 단위로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-129">Note that notifications are sent on a weekly basis.</span></span>
    
- <span data-ttu-id="e56d6-130">검토자는 Microsoft 365 준수 센터의 **처리** 탭으로 이동하여 콘텐츠를 검토하고 영구적으로 삭제하거나, 보존 기간을 연장하거나, 다른 보존 레이블을 적용할 것인지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-130">The reviewers go to the **Disposition** tab in the Microsoft 365 compliance center to review the content and decide whether to permanently delete it, extend its retention period, or apply a different retention label.</span></span>

<span data-ttu-id="e56d6-131">처리 검토에는 Exchange 사서함, SharePoint 사이트, OneDrive 계정 및 Microsoft 365 그룹의 콘텐츠가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-131">A disposition review can include content in Exchange mailboxes, SharePoint sites, OneDrive accounts, and Microsoft 365 groups.</span></span> <span data-ttu-id="e56d6-132">해당 위치에서 처리 검토를 기다리는 콘텐츠는 검토자가 콘텐츠를 영구적으로 삭제하도록 선택한 후에만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-132">Content awaiting a disposition review in those locations is deleted only after a reviewer chooses to permanently delete the content.</span></span>

> [!NOTE]
> <span data-ttu-id="e56d6-133">처리 검토를 지원하려면 사서함에 10MB 이상의 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-133">A mailbox must have at least 10 MB data to support disposition reviews.</span></span>

<span data-ttu-id="e56d6-134">**개요** 탭에서 보류 중인 모든 처리의 개요를 볼 수 있습니다. 예를 들면:</span><span class="sxs-lookup"><span data-stu-id="e56d6-134">You can see an overview of all pending dispositions in the **Overview** tab. For example:</span></span>

![레코드 관리에서 보류 중인 처리 개요](../media/dispositions-overview.png)

<span data-ttu-id="e56d6-136">**보류 중인 모든 처리 보기** 를 선택하면 **처리** 페이지로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-136">When you select the **View all pending dispositions**, you're taken to the **Disposition** page.</span></span> <span data-ttu-id="e56d6-137">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-137">For example:</span></span>

![Microsoft 365 규정 준수 센터의 처리 페이지](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a><span data-ttu-id="e56d6-139">처리 검토를 위한 워크플로</span><span class="sxs-lookup"><span data-stu-id="e56d6-139">Workflow for a disposition review</span></span>

<span data-ttu-id="e56d6-140">다음 다이어그램에서는 보존 레이블을 게시한 다음 사용자가 수동으로 적용하는 경우 처리 검토에 대한 기본 워크플로를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-140">The following diagram shows the basic workflow for a disposition review when a retention label is published and then manually applied by a user.</span></span> <span data-ttu-id="e56d6-141">또는 처리 검토를 위해 구성한 보존 레이블을 콘텐츠에 자동으로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-141">Alternatively, a retention label configured for a disposition review can be auto-applied to content.</span></span>
  
![처리 작업 진행 방식의 흐름을 보여 주는 차트](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)
  
<span data-ttu-id="e56d6-143">보존 기간이 끝날 때 처리 검토를 트리거하는 것은 보존 레이블과만 함께 제공되는 구성 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-143">Triggering a disposition review at the end of the retention period is a configuration option that's available only with a retention label.</span></span> <span data-ttu-id="e56d6-144">보존 정책에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-144">This option is not available for a retention policy.</span></span> <span data-ttu-id="e56d6-145">이 두 가지 보존 솔루션에 대한 자세한 내용은 [보존 정책과 보존 레이블에 대해 알아보기](retention.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e56d6-145">For more information about these two retention solutions, see [Learn about retention policies and retention labels](retention.md).</span></span>

<span data-ttu-id="e56d6-146">보존 레이블을 위한 **보존 설정 정의** 페이지에서:</span><span class="sxs-lookup"><span data-stu-id="e56d6-146">From the **Define retention settings** page for a retention label:</span></span>

![레이블에 대한 보존 설정](../media/disposition-review-option.png)
 
<span data-ttu-id="e56d6-148">이 **처리 검토 트리거** 옵션을 선택한 후, 마법사의 다음 페이지에서 처리 검토자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-148">After you select this **Trigger a disposition review** option, you specify the disposition reviewers on the next page of the wizard:</span></span>

![처리 검토자 지정](../media/disposition-reviewers.png)

<span data-ttu-id="e56d6-150">검토자의 경우 사용자 또는 메일 사용이 가능한 보안 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-150">For the reviewers, specify a user or mail-enabled security group.</span></span> <span data-ttu-id="e56d6-151">이 옵션에 대해 Microsoft 365 그룹([이전 Office 365 그룹](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601))은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-151">Microsoft 365 groups ([formerly Office 365 groups](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) are not supported for this option.</span></span>

### <a name="viewing-and-disposing-of-content"></a><span data-ttu-id="e56d6-152">콘텐츠 보기 및 처리</span><span class="sxs-lookup"><span data-stu-id="e56d6-152">Viewing and disposing of content</span></span>

<span data-ttu-id="e56d6-153">콘텐츠를 검토할 준비가 되었음을 검토자가 전자 메일로 알림을 받는 경우, Microsoft 365 준수 센터의 **레코드 관리** 에서 **처리** 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-153">When a reviewer is notified by email that content is ready to review, they go to the **Disposition** tab from **Records Management** in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="e56d6-154">검토자는 각 보존 레이블에 대해 얼마나 많은 항목이 처리를 대기 중인지 확인할 수 있고, 보존 레이블을 선택하여 해당 레이블이 있는 모든 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-154">The reviewers can see how many items for each retention label are awaiting disposition, and then select a retention label to see all content with that label.</span></span>

<span data-ttu-id="e56d6-155">보존 레이블을 선택한 후, **보류 중인 처리** 탭에서 해당 레이블에 대해 보류 중인 모든 처리를 보게됩니다. 한 개 이상의 항목을 선택하여 작업을 선택하고 사유 메모를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-155">After you select a retention label, you then see all pending dispositions for that label from the **Pending disposition** tab. Select one or more items where you can then choose an action and enter a justification comment:</span></span>

![처리 옵션](../media/retention-disposition-options.png)

<span data-ttu-id="e56d6-157">그림에서 볼 수 있듯이 지원되는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-157">As you can see from the picture, the actions supported are:</span></span> 
  
- <span data-ttu-id="e56d6-158">항목을 영구적으로 삭제</span><span class="sxs-lookup"><span data-stu-id="e56d6-158">Permanently delete the item</span></span>
- <span data-ttu-id="e56d6-159">보존 기간 연장</span><span class="sxs-lookup"><span data-stu-id="e56d6-159">Extend the retention period</span></span>
- <span data-ttu-id="e56d6-160">다른 보존 레이블 적용</span><span class="sxs-lookup"><span data-stu-id="e56d6-160">Apply a different retention label</span></span>

<span data-ttu-id="e56d6-161">위치와 콘텐츠에 대한 사용 권한을 보유하면 **위치** 열에 있는 링크를 사용하여 원래 위치에 있는 문서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-161">Providing you have permissions to the location and the content, you can use the link in the **Location** column to view documents in their original location.</span></span> <span data-ttu-id="e56d6-162">처리 검토를 진행하는 동안 콘텐츠는 원래 위치에서 이동할 수 없으며, 검토자가 그렇게 하도록 선택하기 전에는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-162">During a disposition review, the content never moves from its original location, and it's never deleted until the reviewer chooses to do so.</span></span>

<span data-ttu-id="e56d6-163">전자 메일 알림은 주 단위로 자동으로 검토자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-163">The email notifications are sent automatically to reviewers on a weekly basis.</span></span> <span data-ttu-id="e56d6-164">이 예약된 프로세스는 콘텐츠가 보존 기간의 끝에 도달하는 경우, 검토자자 콘텐츠가 처리를 기다리고 있다는 전자 메일 알림을 받는 데 최대 7일이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-164">This scheduled process means that when content reaches the end of its retention period, it might take up to seven days for reviewers to receive the email notification that content is awaiting disposition.</span></span>
  
<span data-ttu-id="e56d6-165">모든 처리 작업은 감사되고 검토자가 입력한 사유 텍스트는 저장되어 **처리된 항목** 페이지의 **메모** 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-165">All disposition actions can be audited and the justification text entered by the reviewer is saved and displayed in the **Comment** column on the **Disposed items** page.</span></span>
  
### <a name="how-long-until-disposed-content-is-permanently-deleted"></a><span data-ttu-id="e56d6-166">처리된 콘텐츠가 영구적으로 삭제될 때까지 걸리는 시간</span><span class="sxs-lookup"><span data-stu-id="e56d6-166">How long until disposed content is permanently deleted</span></span>

<span data-ttu-id="e56d6-167">처리 검토를 기다리는 콘텐츠는 검토자가 콘텐츠를 영구적으로 삭제하도록 선택한 후에만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-167">Content awaiting a disposition review is deleted only after a reviewer chooses to permanently delete the content.</span></span> <span data-ttu-id="e56d6-168">검토자가 이 옵션을 선택하는 경우, SharePoint 사이트 또는 OneDrive 계정의 콘텐츠가 [보존 설정이 적소에 있는 콘텐츠와 작동하는 방법](retention.md#how-retention-settings-work-with-content-in-place)에 설명된 표준 정리 프로세스를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-168">When the reviewer chooses this option, the content in the SharePoint site or OneDrive account becomes eligible for the standard cleanup process described in [How retention settings work with content in place](retention.md#how-retention-settings-work-with-content-in-place).</span></span>

## <a name="disposition-of-records"></a><span data-ttu-id="e56d6-169">레코드 처리</span><span class="sxs-lookup"><span data-stu-id="e56d6-169">Disposition of records</span></span>

<span data-ttu-id="e56d6-170">**레코드 관리** 페이지의 **처리** 탭을 사용하여 자동으로 또는 처리 검토 후에 현재 삭제된 레코드를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-170">Use the **Disposition** tab from the **Records Management** page to identify records that are now deleted, either automatically or after a disposition review.</span></span> <span data-ttu-id="e56d6-171">이러한 항목에는 **유형** 열에 **처리된 레코드** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-171">These items display **Records Disposed** in the **Type** column.</span></span> <span data-ttu-id="e56d6-172">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-172">For example:</span></span>

![처리 검토가 없이 처리된 항목](../media/records-disposed2.png)

<span data-ttu-id="e56d6-174">레코드 레이블을 위해 **처리된 항목** 탭에 표시되는 항목은 항목이 처리된 후 최대 7년간 유지되고, 해당 기간에 대한 레코드 당 100만 항목의 제한을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-174">Items that are shown in the **Disposed Items** tab for record labels are kept for up to seven years after the item was disposed, with a limit of one million items per record for that period.</span></span> <span data-ttu-id="e56d6-175">**계산** 수가 이 100만의 제한에 근접하고 레코드에 대한 처리 증거가 필요한 경우, [Microsoft 지원](https://docs.microsoft.com/office365/admin/contact-support-for-business-products)에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="e56d6-175">If you see the **Count** number nearing this limit of one million, and you need proof of disposition for your records, contact [Microsoft Support](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).</span></span>

> [!NOTE]
> <span data-ttu-id="e56d6-176">이 기능은 [통합 감사 로그](search-the-audit-log-in-security-and-compliance.md)의 정보를 기초로 하며, 따라서 해당 이벤트를 캡처할 수 있도록 감사를 [사용하도록 설정하고 검색 가능하도록](turn-audit-log-search-on-or-off.md) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-176">This functionality is based on information from the [unified audit log](search-the-audit-log-in-security-and-compliance.md) and therefore requires auditing to be [enabled and searchable](turn-audit-log-search-on-or-off.md) so the corresponding events are captured.</span></span>

<span data-ttu-id="e56d6-177">감사를 위해 **파일 및 페이지 활동** 범주에서 **레코드로 표시된 삭제된 파일** 을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-177">For auditing, search for **Deleted file marked as a record** in the **File and page activities** category.</span></span> <span data-ttu-id="e56d6-178">이 감사 이벤트는 문서 및 이일에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-178">This audit event is applicable to documents and emails.</span></span>

## <a name="filter-and-export-the-views"></a><span data-ttu-id="e56d6-179">보기 필터링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="e56d6-179">Filter and export the views</span></span>

<span data-ttu-id="e56d6-180">**처리** 페이지에서 보존 레이블을 선택하는 경우, **보류 중인 처리** 탭(해당 하는 경우)과 **처리된 항목** 탭을 사용하여 보기를 필터링하여 항목을 보다 쉽게 찾을 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-180">When you select a retention label from the **Disposition** page, the **Pending disposition** tab (if applicable) and the **Disposed items** tab let you filter the views to help you more easily find items.</span></span> 

<span data-ttu-id="e56d6-181">보류 중인 처리의 경우에는 시간 범위가 만료 날짜를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-181">For pending dispositions, the time range is based on the expiration date.</span></span> <span data-ttu-id="e56d6-182">처리된 항목의 경우에는 시간 범위가 삭제 날짜를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-182">For disposed items, the time range is based on the deletion date.</span></span>
  
<span data-ttu-id="e56d6-183">아래의 항목에 대한 정보를 .csv 파일로 내보낼 수 있습니다. 그런 다음 Excel을 사용하여 정렬을 하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e56d6-183">You can export information about the items in either view as a .csv file that you can then sort and manage using Excel:</span></span>

![처리에 대한 내보내기 옵션](../media/retention-export-option.png)

