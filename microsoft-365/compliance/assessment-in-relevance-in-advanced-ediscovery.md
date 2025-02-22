---
title: Advanced eDiscovery의 위험성 평가 이해
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: 09/14/2017
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Microsoft 365 Advanced eDiscovery의 관련성 교육 중에 다양한 문제를 파악하는 데 필요한 평가 단계 및 해당 역할에 대한 개요를 얻습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 28bbe15a6e3f5611041cf446bd053f59de395d54
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663083"
---
# <a name="understand-assessment-in-relevance-in-advanced-ediscovery-classic"></a>Advanced eDiscovery(클래식)의와의관성 평가 이해

> [!NOTE]
> Advanced eDiscovery를 사용하려면 Office 365 E3의 고급 준수 추가 기능이나 조직을 위한 E5 구독이 필요합니다. 이 요금제가 없는 상태에서 Advanced eDiscovery를 사용하려는 경우에는 [Office 365 Enterprise E5 평가판을 등록](https://go.microsoft.com/fwlink/p/?LinkID=698279)할 수 있습니다. 
  
Advanced eDiscovery를 사용하면 정의된 문제 및 사례에 대해 가져온 데이터에 대한 초기 평가를 사용할 수 있습니다. Advanced eDiscovery를 사용하면 전문가가 채택된 방식에 대한 의사 결정을 내릴 수 있으며 이러한 결정을 문서 검토 프로젝트에 적용할 수 있습니다.
  
## <a name="understanding-assessment"></a>평가 이해

평가에서 전문가는 500개 이상의 파일 집합을 임의로 검토합니다. 이 집합은 문제의 풍부한 정보를 파악하고 교육 결과를 반영하는 통계를 생성하는 데 사용됩니다. Advanced eDiscovery 관련성이 정확한 통계를 제공하고 교육 프로세스의 안정화 지점을 효과적으로 결정하는 데 도움이 되는 통계 수준에 도달하기에 충분한 관련 파일이 발견되면 평가에 성공합니다. 
  
평가 집합의 관련 파일 수가 높을수록 안정성 알고리즘의 통계와 효율성이 더 정확합니다. 평가 파일 내의 관련 파일 수는 문제의 풍부도에 따라 달라 습니다. 풍부한성은 문제와 관련된 집합의 예상 관련 파일 비율입니다. 풍부한 문제가 있는 경우 관련 파일 수가 낮은 문제보다 관련 파일 수가 더 빨라야 합니다. 매우 낮은 풍부한 문제(예: 2% 이하)에는 상당한 수의 관련 파일에 도달하기 위해 매우 큰 평가 집합이 필요할 수 있습니다.
  
교육 중 및 일괄 계산 후 트랙 및 결정 탭에 있는 통계에는 다양한 검토 집합에 대한 회수 예상이 포함됩니다. 통계에서 샘플 집합(이 경우 평가 파일)을 기반으로 하는 예측에는 오차 여백과 해당 오류 여백의 신뢰 수준이 포함됩니다. 예를 들어 예상 회수율 80%에는 신뢰 수준이 95%인 오차의 여백이 있을 수 있습니다. 즉, 예상 회수율은 실제로 75%-85%이고 이 예측의 신뢰도는 95%입니다. 평가 집합이 클수록 오차 여백이 더 작아지고 통계가 더 정확해집니다. 
  
전문가가 초기 평가 집합을 500개 파일로 검토한 후, 해당 관계에 따라 회수 값의 현재 오차 여백을 확인할 수 있습니다. 또한 평가 집합을 최적화하기 위해 기본 오차 여백에 도달하는 것이 좋습니다. 그 예는 다음과 같습니다.
  
- 평가 집합에서 이미 10% 이상의 오차를 산출한 경우 교육으로 이동하는 것이 좋습니다(추가 평가 검토가 필요하지 않습니다). 
    
- 평가 집합에서 13% 또는 13%의 오차를 산출한 경우 다른 평가 파일 집합을 검토하여 더 작은 여백에 도달하는 것이 좋습니다. 
    
- 유용성 수준이 매우 낮은 경우 유용한 오류 여백에 도달하는 데 필요한 평가 집합이 너무 크기 때문에 오차의 여백이 크지만(통계를 비실용적으로 만들) 관련성으로 평가를 중지하는 것이 좋습니다.
    
각 문제마다 자체적으로 풍부한 오류 여백과 예상되는 추가 평가 파일 수가 있습니다. 다음 평가 집합은 최대 파일 수(단일 집합에서 최대 1,000개)에 따라 만들어집니다.
  
관련성 권장 사항을 수락하거나 요구에 따라 현재 오류 여백을 조정할 수 있습니다. 기본 현재 오류 여백은 회수율이 75% 이상인 것으로 결정됩니다.
  
> [!NOTE]
> 평가 단계는 문제에 대한 확장된 보기의 관련성 트랙 탭에서 문제당 평가 확인란의  선택을 취소한 다음 "모든 문제"에 대해 무시할 수 있습니다. **\>** 그러나 이 문제의 통계는 없습니다. > 확인란 선택을 취소하는 것은 평가가 수행되기 전에만 수행할 수 있습니다.  여러 문제가 있는 경우 각 문제에 대해 확인란이 선택 취소된 경우 평가가 무시됩니다. 
  
## <a name="related-topics"></a>관련 항목

[고급 eDiscovery (클래식)](office-365-advanced-ediscovery.md)
  
[태그 지정 및 평가](tagging-and-assessment-in-advanced-ediscovery.md)
  
[태그 지정 및관련성 교육](tagging-and-relevance-training-in-advanced-ediscovery.md)
  
[추적과정성 분석](track-relevance-analysis-in-advanced-ediscovery.md)
  
[결과에 따라 결정](decision-based-on-the-results-in-advanced-ediscovery.md)
  
[테스트와의관성 분석](test-relevance-analysis-in-advanced-ediscovery.md)

