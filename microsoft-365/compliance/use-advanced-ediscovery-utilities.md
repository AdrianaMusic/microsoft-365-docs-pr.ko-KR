---
title: Advanced eDiscovery 유틸리티 사용
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: 9/14/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 66ca9993-75f4-4724-aea2-5a0719b660c1
description: 사례 로그, 데이터 지우기, 프로세스 오류, 관련성 수정, 투명성 분석 등 Advanced eDiscovery의 유틸리티에 대해 자세히 알아보습니다.
ms.openlocfilehash: 745b81609d73ec88525c3348cc4d582c7d5d7b30
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663297"
---
# <a name="use-advanced-ediscovery-classic-utilities"></a><span data-ttu-id="30504-103">Advanced eDiscovery(클래식) 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="30504-103">Use Advanced eDiscovery (classic) utilities</span></span>

> [!NOTE]
> <span data-ttu-id="30504-p101">Advanced eDiscovery를 사용하려면 Office 365 E3의 고급 준수 추가 기능이나 조직을 위한 E5 구독이 필요합니다. 이 요금제가 없는 상태에서 Advanced eDiscovery를 사용하려는 경우에는 [Office 365 Enterprise E5 평가판을 등록](https://go.microsoft.com/fwlink/p/?LinkID=698279)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-p101">Advanced eDiscovery requires an Office 365 E3 with the Advanced Compliance add-on or an E5 subscription for your organization. If you don't have that plan and want to try Advanced eDiscovery, you can [sign up for a trial of Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).</span></span> 
  
<span data-ttu-id="30504-106">Advanced eDiscovery에서 표시되고 사용할 수 있는 유틸리티는 컨텍스트 및 사용자 역할에 따라 달라 습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-106">The utilities that are displayed and available in Advanced eDiscovery depend on context and user roles.</span></span>
  
## <a name="case-log"></a><span data-ttu-id="30504-107">사례 로그</span><span class="sxs-lookup"><span data-stu-id="30504-107">Case log</span></span>

<span data-ttu-id="30504-108">사례 로그는 추적, 문제 해결 및 오류 및 경고 처리에 사용할 수 있는 자세한 응용 프로그램 처리 작업 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-108">The Case log provides a detailed list of application processing activities, which can be used for tracking, troubleshooting, and for addressing errors and warnings.</span></span> <span data-ttu-id="30504-109">로그를 생성하여 호스트 또는 서버에 로컬로 저장하거나 전자 메일 주소로 직접 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-109">The log can be generated and stored locally on the host or server, or sent directly to an email address.</span></span>
  
<span data-ttu-id="30504-110">로그 파일은 클라이언트의 컴퓨터에 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-110">The log file can also be downloaded to the client's computer.</span></span> <span data-ttu-id="30504-111">구성 및 사용자 역할에 따라 클라이언트 다운로드 옵션을 활성화하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-111">The client download option may be enabled or disabled according to configuration and user role.</span></span>
  
1. <span data-ttu-id="30504-112">메뉴 표시줄에서 **Cogwheel 아이콘을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-112">In the menu bar, click the **Cogwheel** icon.</span></span> 
    
2. <span data-ttu-id="30504-113">설정 **및 \>** 유틸리티 탭에서 사례 로그 설치를 **\> 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-113">In the **Settings and utilities \> Utilities** tab, select **Case log \> Setup**.</span></span>
    
3. <span data-ttu-id="30504-114">로그 **수준을 다음과** 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-114">Select the **Log level** as follows:</span></span> 
    
  - <span data-ttu-id="30504-115">**표준**: 기본 로그 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-115">**Standard**: Includes the basic log data.</span></span> <span data-ttu-id="30504-116">이 옵션은 일반적으로 모니터링에 필요하며, 권장되지 않는 한 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-116">This option is usually necessary for monitoring, and should be used unless recommended otherwise.</span></span>
    
  - <span data-ttu-id="30504-117">**최소**: 매우 큰 경우에 사용하며 최신 데이터만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-117">**Minimal**: Used for very large cases, and returns only the latest data.</span></span>
    
4. <span data-ttu-id="30504-118">사례 **실행 로그를 클릭합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-118">Click **Run Case log**.</span></span> <span data-ttu-id="30504-119">로그가 생성되고 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-119">The log is generated and path is displayed.</span></span> <span data-ttu-id="30504-120">현재 및 마지막 작업에 대한 작업 진행률 정보가 작업 상태 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-120">The task progress information for the current and last task is displayed in the Task status pane.</span></span>
    
## <a name="clear-data"></a><span data-ttu-id="30504-121">데이터 지우기</span><span class="sxs-lookup"><span data-stu-id="30504-121">Clear data</span></span>

<span data-ttu-id="30504-122">사례 데이터를 삭제하거나 다시 초기화해야 하는 경우 데이터베이스 인스턴스를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-122">If it is necessary to delete or reinitialize case data, the database instance must be initialized.</span></span> <span data-ttu-id="30504-123">데이터 지우기 유틸리티는 사례 데이터베이스, 텍스트 파일, 사례 폴더 및 누적된 결과에서 지정된 모든 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-123">The Clear data utility deletes all specified entries from the case database, text files, case folder, and accumulated results.</span></span> <span data-ttu-id="30504-124">이 함수는 관리자만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-124">The function can only be performed by an administrator.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="30504-125">이 작업은 되버러블 수 없는 작업으로, 전문가가 수행한 모든 관련성 태그 지정 및 분석을 지우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-125">This action is not reversible and will clear all Relevance tagging and analysis performed by the expert.</span></span> <span data-ttu-id="30504-126">필요한 경우 데이터 백업을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-126">Save a backup of data, if necessary.</span></span> <span data-ttu-id="30504-127">이 옵션은 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-127">Use this option with extreme care.</span></span> <span data-ttu-id="30504-128">태그가 지정 및 순위가 지정된 파일을 삭제하면 타당성 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-128">Deleting tagged and ranked files can impact the Relevance results.</span></span> 
  
1. <span data-ttu-id="30504-129">메뉴 표시줄에서 **Cogwheel 아이콘을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-129">In the menu bar, click the **Cogwheel** icon.</span></span> 
    
2. <span data-ttu-id="30504-130">설정 **및 \>** 유틸리티 탭에서 데이터 설정 **지우기를 \> 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-130">In the **Settings and utilities \> Utilities** tab, select **Clear data \> Setup**.</span></span>
    
3. <span data-ttu-id="30504-131">정보를 초기화하기 위한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-131">Select an option for the information to initialize:</span></span>
    
  - <span data-ttu-id="30504-132">**연관성:** 로드 정의 및 로드에 대한 파일 연결 등 연관성에서 수행된 모든 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-132">**Relevance**: Deletes all work done in Relevance, including definition of loads and association of files to loads.</span></span> <span data-ttu-id="30504-133">모든 샘플 및 태그 지정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-133">It deletes all samples and tagging.</span></span>
    
  - <span data-ttu-id="30504-134">**중복에** 가까운 전자 메일 스레드: 중복에 가까운 전자 메일 스레드 및 전자 메일 스레드의 모든 분석 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-134">**Near-duplicates and email threads**: Deletes all analysis information of near-duplicates and email threads.</span></span>
    
  - <span data-ttu-id="30504-135">**테마:** 테마 관련 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-135">**Themes**: Deletes themes-related data.</span></span>
    
  - <span data-ttu-id="30504-136">**내보내기 기록**: 내보내기 일괄 처리의 기록 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-136">**Export history**: Deletes history information of Export batches.</span></span>
    
4. <span data-ttu-id="30504-137">데이터 **지우기 를 클릭합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-137">Click **Clear data**.</span></span> <span data-ttu-id="30504-138">사례 데이터가 지워진 경우</span><span class="sxs-lookup"><span data-stu-id="30504-138">The case data is cleared.</span></span> <span data-ttu-id="30504-139">현재 및 마지막 작업에 대한 작업 진행률  정보가 작업 상태 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-139">The task progress information for the current and last task is displayed in the **Task status** pane.</span></span> 
    
## <a name="modify-relevance"></a><span data-ttu-id="30504-140">Relevance 수정</span><span class="sxs-lookup"><span data-stu-id="30504-140">Modify Relevance</span></span>

<span data-ttu-id="30504-141">이 섹션에서는 관련성 샘플을 건너뛰거나 롤백하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-141">This section describes how to skip or roll back a Relevance sample.</span></span>
  
1. <span data-ttu-id="30504-142">메뉴 표시줄에서 **Cogwheel 아이콘을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-142">In the menu bar, click the **Cogwheel** icon.</span></span> 
    
2. <span data-ttu-id="30504-143">설정 **및 \>** 유틸리티 탭에서 해당 정보 수정을 **선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-143">In the **Settings and utilities \> Utilities** tab, select **Modify relevance**.</span></span>
    
3. <span data-ttu-id="30504-144">옵션에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-144">Select from the options:</span></span> 
    
  - <span data-ttu-id="30504-145">**현재 샘플** 건너뛰기 - 현재 사용자의 경우 : **유틸리티를** 실행하는 사용자의 열린 사례 샘플에서 태그가 지정되지 않은 모든 파일에 Skip으로 태그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-145">**Skip current sample - for current user**: This will tag, as **Skip**, all untagged files in the open case sample of the user running the utility.</span></span> <span data-ttu-id="30504-146">Skip으로 태그가 지정된 파일에는 이러한 파일과의관한 처리가 **수행되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-146">Relevance processing will not be performed on files tagged as **Skip**.</span></span>
    
  - <span data-ttu-id="30504-147">**현재 샘플 건너뛰기 - 열려** 있는 모든 샘플 : 모든 사용자에 대해 열려 있는 모든 샘플에서 태그가 지정됩니다. **건너뛰기로** 태그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-147">**Skip current sample - all open samples**: This will tag, as **Skip**, all untagged files in all open samples for all users.</span></span> <span data-ttu-id="30504-148">사용자가 현재 샘플에 태그를 지정하고 있는 경우 이 옵션은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-148">This option is not recommended if users are currently tagging samples.</span></span>
    
  - <span data-ttu-id="30504-149">**마지막 샘플 롤백:**"계산" 프로세스 전후에 관계없이 마지막으로 완료된 관련성 교육 샘플이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-149">**Roll back last sample**: The last completed Relevance training sample will be rolled back, regardless of whether it is before or after the "Calculate" process.</span></span> <span data-ttu-id="30504-150">Catch-up 샘플의 롤백은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-150">Rollback of a catch-up sample is not allowed.</span></span>
    
4. <span data-ttu-id="30504-151">실행을 **클릭하여** 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-151">Click **Execute** to run.</span></span> 
    
## <a name="transparency-analysis"></a><span data-ttu-id="30504-152">투명성 분석</span><span class="sxs-lookup"><span data-stu-id="30504-152">Transparency analysis</span></span>

<span data-ttu-id="30504-153">투명성 분석 유틸리티를 사용하면 파일에 대한 자세한 보기와 할당된 관련성 점수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-153">The Transparency analysis utility enables a detailed view of files and their assigned Relevance score.</span></span> <span data-ttu-id="30504-154">보고서를 보안 검사로 사용할 수도 있습니다. 또는 고급 eDiscovery에서 할당한와 비교하여 휴먼 검토자가 정의한 파일의 해당성을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-154">The report can be used as a sanity check or to compare the relevance of a file defined by a human reviewer as compared to the relevance assigned by Advanced eDiscovery.</span></span> 
  
<span data-ttu-id="30504-155">관련성 점수 외에도 Advanced eDiscovery는 키워드 컨텍스트를 고려하는 키워드 가중치를 계산하고 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-155">In addition to Relevance scores, Advanced eDiscovery calculates and assigns keyword weights that consider the keyword context.</span></span> <span data-ttu-id="30504-156">파일의 동일한 단어에 컨텍스트 및 위치에 따라 다른 가중치를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-156">The same word in a file can be assigned different weights, depending on context and location.</span></span> <span data-ttu-id="30504-157">각 키워드는 노랑에서 진한 주황 및 다양한 회색 음영에 이르기까지 색상 강도가 증가하는 배율을 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-157">Each keyword is marked using an increasing scale of color intensity ranging from yellow to dark orange and varying shades of gray.</span></span> <span data-ttu-id="30504-158">색 코딩은 단어의 상대적 양성 또는 음의 영향을 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-158">Color coding is used to visually indicate the word's relative positive or negative contribution to the Relevance score.</span></span> 
  
<span data-ttu-id="30504-159">다중 문제 사례 시나리오에서는 각 문제별로 투명성 분석 보고서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30504-159">In a multiple-issue case scenario, a Transparency analysis report can be generated for each issue.</span></span>
  
1. <span data-ttu-id="30504-160">메뉴 표시줄에서 **Cogwheel 아이콘을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-160">In the menu bar, click the **Cogwheel** icon.</span></span> 
    
2. <span data-ttu-id="30504-161">설정 **및 \>** 유틸리티 탭에서 투명성 분석 **설치를 \> 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-161">In the **Settings and utilities \> Utilities** tab, select **Transparency analysis \> Setup**.</span></span>
    
3. <span data-ttu-id="30504-162">In \*\* File ID \*\*, enter the file ID of the file ID of the file to process.</span><span class="sxs-lookup"><span data-stu-id="30504-162">In \*\* File ID \*\*, enter the file ID of the file to process.</span></span>
    
4. <span data-ttu-id="30504-163">문제 **목록에서** 해당 문제를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30504-163">In the **Issue** list, select the pertinent issue.</span></span> 
    
5. <span data-ttu-id="30504-164">투명도 **분석을 클릭합니다.**</span><span class="sxs-lookup"><span data-stu-id="30504-164">Click **Transparency analysis**.</span></span> <span data-ttu-id="30504-165">완료 시 표시된 키워드 색이 전체 관련성 점수와 어떻게 상관 관계가 있는지 보여 주며 파일에 대한 투명성 분석 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30504-165">Upon completion, the Transparency analysis report for the file is displayed, which shows how the marked keyword colors correlate to the overall Relevance score.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="30504-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30504-166">See also</span></span>

[<span data-ttu-id="30504-167">고급 eDiscovery (클래식)</span><span class="sxs-lookup"><span data-stu-id="30504-167">Advanced eDiscovery (classic)</span></span>](office-365-advanced-ediscovery.md)
  
[<span data-ttu-id="30504-168">사례 및 테넌트 설정 정의</span><span class="sxs-lookup"><span data-stu-id="30504-168">Defining case and tenant settings</span></span>](define-case-and-tenant-settings-in-advanced-ediscovery.md)

