---
title: Advanced eDiscovery를 위한 데이터 준비
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
ms.assetid: 2fb94c23-1846-4a0e-994d-da6d02445f15
description: 보안 준수 센터를 사용하여 Advanced eDiscovery를 사용하여 분석을 위해 &amp; 데이터를 준비하는 방법을 학습합니다.
ms.openlocfilehash: 43253a3908925bc188568f020f48c62a94552403
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49662883"
---
# <a name="prepare-data-for-advanced-ediscovery-classic"></a>Advanced eDiscovery(클래식)에 대한 데이터 준비

이 항목에서는 Advanced eDiscovery(클래식)의 사례에 콘텐츠 검색 결과를 로드하는 방법을 설명합니다. 
  
> [!IMPORTANT]
> 최신 버전의 Advanced eDiscovery에 계속 투자함에 따라, Advanced eDiscovery(*Advanced eDiscovery(클래식)* 또는 *Advanced eDiscovery v1.0* 이라고도 함)를 발표합니다. Advanced eDiscovery v1.0을 계속 사용하고 있는 경우 [Advanced eDiscovery v2.0](overview-ediscovery-20.md)(*Advanced eDiscovery solution in Microsoft 365* 라고도 함)으로 전환하세요. Advanced eDiscovery 2.0에는 Advanced eDiscovery v1.0에 있는 유사한 기능이 포함되어 있습니다. 또한 보유자 관리, 통신 관리, 검토 집합 등의 새로운 기능도 제공합니다. Advanced eDiscovery v1.0의 사용 중지에 대한 자세한 내용은 [레거시 eDiscovery 도구의 사용 중지](legacy-ediscovery-retirement.md#advanced-ediscovery-v10)를 참조하세요.  
  
## <a name="step-1-prepare-data-for-advanced-ediscovery"></a>1단계: Advanced eDiscovery에 대한 데이터 준비

Advanced eDiscovery를 사용하여 데이터를 분석하려면 Microsoft 365 보안 &amp; 규정 준수 센터(Microsoft 365 보안 &amp; 규정 준수 센터의 **콘텐츠 검색** 페이지에 나열됨)에서 실행하는 콘텐츠 검색 또는 eDiscovery 케이스(보안 &amp; 규정 준수 센터의 **eDiscovery** 페이지에 나열됨)와 관련된 검색의 결과를 사용할 수 있습니다. 
  
Advanced eDiscovery에서 분석을 위해 검색 결과를 준비하는 자세한 단계는 [Advanced eDiscovery에](prepare-search-results-for-advanced-ediscovery.md)대한 검색 결과 준비를 참조하세요.
  
> [!NOTE]
> Microsoft 365 외부에 데이터가 있으며 Advanced eDiscovery에서 준비하고 분석할 수 있도록 Microsoft 365로 가져오고 싶은 경우 PST 파일을 [Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/importing-pst-files-to-office-365) 및 타사 데이터 보관으로 가져오는 개요를 참조하세요. [](https://www.microsoft.com/?ref=go) 
  
## <a name="step-2-load-search-result-data-in-to-a-case-in-advanced-ediscovery"></a>2단계: Advanced eDiscovery에서 사례에 검색 결과 데이터 로드

분석을 위해 보안 &amp; 규정 준수 센터의 검색 결과를 준비한 후, 다음 단계는 Advanced eDiscovery에서 케이스에 검색 결과를 로드하는 것입니다. 자세한 내용은 [프로세스 모듈 실행](run-the-process-module-in-advanced-ediscovery.md)을 참조하세요.
  
1. [https://protection.office.com](https://protection.office.com)으로 이동합니다.
    
2. 회사 또는 학교 계정을 사용하여 로그인합니다.
    
3. 보안 및 준수 센터에서 **검색 &amp; 조사** \> **eDiscovery** 를 클릭하여 조직의 사례 목록을 표시합니다. 
    
4. Advanced eDiscovery에서 데이터를 로드할 사례 옆에 있는 **열기** 를 클릭합니다. 
    
5. 사례에 대한 **홈** 페이지에서 **Advanced eDiscovery로 전환** 을 클릭합니다. 
    
    ![Advanced eDiscovery로 전환을 클릭하여 Advanced eDiscovery에서 케이스를 엽니다.](../media/8e34ba23-62e3-4e68-a530-b6ece39b54be.png)
  
    **Advanced eDiscovery에 연결하는 중** 진행률 표시줄이 표시됩니다. Advanced eDiscovery에 연결되면 컨테이너 목록이 해당 케이스의 설정 페이지에 표시됩니다. 
    
    ![케이스가 Advanced eDiscovery에 표시됩니다.](../media/8036e152-70dc-4bb7-9379-61c1ed8326b4.png)
  
     이러한 컨테이너는 1단계 동안 Advanced eDiscovery에서 분석을 위해 준비한 검색 결과를 나타냅니다. 컨테이너의 이름에는 보안 &amp; 규정 준수 센터의 사례에 있는 콘텐츠 검색과 동일한 이름이 사용됩니다. 목록에서 컨테이너는 사용자가 준비한 컨테이너입니다. 다른 사용자가 Advanced eDiscovery에 사용하도록 검색 결과를 준비한 경우, 해당 컨테이너가 목록에 포함되지 않습니다. 
    
6. Advanced eDiscovery에서 컨테이너에 있는 검색 결과 데이터를 사례에 로드하려면 컨테이너를 선택한 다음 **처리** 를 클릭합니다.
    
Advanced eDiscovery에서 보안 &amp; 규정 준수 센터의 검색 결과를 사례에 추가한 후, 다음 단계는 Advanced eDiscovery의 도구를 사용하여 사례와 관련된 데이터를 분석하고 선별하는 것입니다. 
  
## <a name="see-also"></a>참고 항목

[고급 eDiscovery (클래식)](office-365-advanced-ediscovery.md)
  
[사용자 및 사례 설정](set-up-users-and-cases-in-advanced-ediscovery.md)
  
[사례 데이터 분석](analyze-case-data-with-advanced-ediscovery.md)
  
[관련성 설정 관리](manage-relevance-setup-in-advanced-ediscovery.md)
  
[관련성 모듈 사용](use-relevance-in-advanced-ediscovery.md)
  
[사례 데이터 내보내기](export-case-data-in-advanced-ediscovery.md)

