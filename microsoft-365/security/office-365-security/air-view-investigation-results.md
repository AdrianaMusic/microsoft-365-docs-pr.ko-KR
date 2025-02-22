---
title: Microsoft 365에서 자동화된 조사 결과 보기
keywords: AIR, autoIR, ATP, 자동화된, 조사, 대응, 수정, 위협, 고급, 위협, 보호
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365에서 자동화된 조사가 진행되는 동안 및 이후에 결과 및 주요 결과를 볼 수 있습니다.
ms.date: 11/05/2020
ms.openlocfilehash: 2018f008e043f36cd41047185f305209fcb725d7
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615147"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Microsoft 365의 자동화된 조사 세부 정보 및 결과

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Microsoft [](office-365-air.md) [Defender for Office 365에서](office-365-atp.md)자동화된 조사가 발생하면 자동화된 조사 프로세스 중 및 이후에 조사에 대한 세부 정보를 사용할 수 있습니다. 필요한 권한이 있는 경우 Microsoft 365 보안 센터에서 해당 세부 정보를 볼 수 있습니다. 조사 세부 정보는 최신 상태를 제공하고 보류 중인 작업을 승인할 수 있는 기능을 제공합니다.

## <a name="investigation-status"></a>조사 상태

조사 상태는 분석 및 작업의 진행률을 나타냅니다. 조사가 실행되면 위협이 발견된지 여부와 작업이 승인된지 여부를 나타내기 위해 상태가 변경됩니다.

|상태|설명|
|---|---|
|**시작 중**|조사가 트리거되고 실행을 기다리는 중입니다.|
|**실행 중**|조사 프로세스가 시작된 후 진행 중입니다. 이 상태는 보류 중인 작업이 [승인된](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) 경우도 발생합니다.|
|**위협 없음**|조사가 완료된 후 위협(사용자 계정, 전자 메일 메시지, URL 또는 파일)이 식별되지 않았습니다. <p> **팁**: 누락된 것으로 의심되는 경우(예: 거짓 부정) 위협 탐색기를 사용하여 조치를 [취할 수 있습니다.](threat-explorer.md)|
|**위협 발견**|자동화된 조사에서 문제가 발견되지만 이러한 문제를 해결하기 위한 구체적인 수정 작업은 없습니다. <p> 위협 **발견** 상태는 특정 유형의 사용자 활동을 식별했지만 정리 작업을 사용할 수 없는 경우에 발생할 수 있습니다. 예를 들어 다음과 같은 사용자 활동이 있습니다. <ul><li>[DLP(데이터](https://docs.microsoft.com/Microsoft-365/compliance/data-loss-prevention-policies) 손실 방지) 이벤트</li><li>이상을 보내는 전자 메일</li><li>보낸 맬웨어</li><li>보낸 피싱</li></ul> <p> 조사에서 수정할 악의적인 URL, 파일 또는 전자 메일 메시지가 없음을 발견하고 전달 규칙이나 위임 해제와 같은 수정할 사서함 활동이 없습니다. <p> **팁**: 누락된 것으로 의심되는 경우(예: 거짓 부정) 위협 탐색기를 사용하여 조사하고 조치를 [취할 수 있습니다.](threat-explorer.md)|
|**시스템으로 종료**|조사가 중지되었습니다. 조사는 몇 가지 이유로 중지될 수 있습니다. <ul><li>조사의 보류 중인 작업이 만료되었습니다. 보류 중인 작업은 1주일 동안 승인을 기다린 후 시간적이 지났습니다.</li><li>작업이 너무 많이 있습니다. 예를 들어 악의적인 URL을 클릭하는 사용자가 너무 많은 경우 조사에서 모든 분석기를 실행할 수 있는 기능을 초과할 수 있으므로 조사가 중단됩니다.</li></ul> <p> **팁:** 작업이 수행되기 전에 조사가 중단된 경우 [위협](threat-explorer.md) 탐색기를 사용하여 위협을 찾아 해결해 하세요.|
|**보류 중인 작업**|조사에서 악성 전자 메일, 악의적인 URL 또는 위험한 사서함 설정과 위협이 승인 대기하고 있는 수정 작업을 [발견했습니다.](air-review-approve-pending-completed-actions.md) <p> 보류 **중인 작업** 상태는 해당 작업이 있는 위협이 발견되면 트리거됩니다. 그러나 조사가 실행될 때 보류 중인 작업 목록이 늘어날 수 있습니다. 조사 [로그에서](#playbook-log) 다른 항목이 아직 완료 보류 중인지 확인할 수 있습니다.|
|**수정**|조사가 끝났고 모든 수정 작업이 승인되었습니다(완전히 수정된 것으로 알려됨). <p> **참고:** 승인된 수정 작업에는 작업이 수행되지 않도록 하는 오류가 발생할 수 있습니다. 재구성 작업이 성공적으로 완료된지 여부에 관계없이 조사 상태는 변경되지 않습니다. 조사 [로그에서](#playbook-log) 자세한 결과를 확인할 수 있습니다.|
|**부분적으로 수정**|조사 결과 수정 작업이 수행되었습니다. 일부는 승인 및 완료되었습니다. 다른 작업은 여전히 [보류 중입니다.](air-review-approve-pending-completed-actions.md)|
|**실패**|하나 이상의 조사 분석기가 제대로 완료되지 않는 문제가 발생했습니다. <p> **참고:** 재구성 작업이 승인된 후 조사가 실패하면 수정 작업이 성공할 수 있습니다. 조사 [로그에서](#playbook-log) 자세한 결과를 확인할 수 있습니다.|
|**스로틀링에 의해 대기**|조사가 큐에 대기 중입니다. 다른 조사가 완료되면 대기 중인 조사가 시작됩니다. 스로틀은 서비스 성능이 좋지 않은 것을 방지하는 데 도움이 됩니다.  <p> **팁**: 보류 중인 작업은 새 조사를 실행할 수 있는 수를 제한할 수 있습니다. 보류 중인 [작업을 승인(또는 거부)해야 합니다.](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)|
|**스로틀에 의해 종료**|조사가 너무 긴 큐에 있는 경우 중지됩니다. <p> **팁**: [위협 탐색기에서 조사를 시작할 수 있습니다.](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)|
|

## <a name="view-details-of-an-investigation"></a>조사 세부 정보 보기

1. 보안 & 준수 <https://protection.office.com> 센터()로 이동하여 로그인합니다.

2. 다음 작업 중 하나를 수행하십시오.

    - 위협 관리 **대시보드로** \> **이동** 그러면 보안 [대시보드로 진행됩니다.](security-dashboard.md) AIR 위젯이 보안 대시보드의 맨 [위에 표시됩니다.](security-dashboard.md) 조사 요약과 같은 **위젯을 선택합니다.**

    - 위협  관리 \> **조사로 이동.**

    두 방법 중 하나를 사용하면 조사 목록으로 진행됩니다.

    ![AIR에 대한 기본 조사 페이지](../../media/air-maininvestigationpage.png)

3. 조사 목록에서 ID 열의 **항목을** 선택합니다. 그러면 조사 그래프부터 조사 세부 정보 페이지가 보기로 열립니다.

    ![AIR 조사 그래프 페이지](../../media/air-investigationgraphpage.png)

   다양한 탭을 사용하여 조사에 대해 자세히 알아보습니다.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>조사와 관련된 경고에 대한 세부 정보 보기

특정 종류의 경고는 Microsoft 365에서 자동화된 조사를 트리거합니다. 자세한 내용은 자동화된 [조사를 트리거하는 경고 정책을 참조합니다.](office-365-air.md#which-alert-policies-trigger-automated-investigations)

다음 절차에 따라 자동화된 조사와 연결된 경고에 대한 세부 정보를 볼 수 있습니다.

1. 보안 & 준수 <https://protection.office.com> 센터()로 이동하여 로그인합니다.

2. 위협  관리 \> **조사로 이동.**

3. 조사 목록에서 ID 열의 **항목을** 선택합니다.

4. 조사 세부 정보가 열리면 경고 **탭을** 선택합니다. 조사를 트리거한 모든 알림이 여기에 나열됩니다.

5. 목록에서 항목을 선택합니다. 경고에 대한 세부 정보와 추가 정보 및 작업에 대한 링크가 있는 플라이아웃이 열립니다.

6. 플라이아웃에 대한 정보를 검토하고, 특정 경고에 따라 **해결,** 표시 안 되거나 사용자에게 알림과 같은 작업을 **실행합니다.**

    - **해결은** 경고를 닫는 데 해당합니다.

    - **표시** 안 하여 정책이 지정된 기간 동안 경고를 트리거하지 않습니다.

    - **사용자에게 사용자의** 전자 메일 주소가 이미 입력된 전자 메일을 시작하고 보안 운영 팀에서 해당 사용자에게 메시지를 입력할 수 있도록 합니다. 이 메시지는 위협 탐색기를 사용하여 받는 사람에게 메시지를 보내는 [경우와 비슷합니다.](threat-explorer.md)

## <a name="how-to-use-the-various-tabs"></a>다양한 탭을 사용하는 방법

다음 섹션에서는 자동화된 조사 페이지의 다양한 탭과 정보를 사용하는 방법을 안내합니다.

### <a name="automated-investigations-page"></a>자동화된 조사 페이지

자동화된 조사 페이지에는 조직의 조사와 해당 현재 상태가 표시됩니다.

![AIR에 대한 기본 조사 페이지](../../media/air-maininvestigationpage.png)

다음을 수행할 수 있습니다.

- 조사로 바로 **이동합니다(조사 ID 선택).**

- 필터를 적용합니다. 조사 **유형,** **시간 범위,** **상태** 또는 이들의 조합에서 선택 합니다.

- 데이터를 .csv 파일로 내보낼 수 있습니다.

### <a name="investigation-graph"></a>조사 그래프

특정 조사를 열면 조사 그래프 페이지가 표시됩니다. 이 페이지에는 전자 메일 메시지, 사용자(및 해당 활동) 및 트리거된 경고의 일부로 자동으로 조사된 장치 등 다양한 엔터티가 표시됩니다.

![AIR 조사 그래프 페이지](../../media/air-investigationgraphpage.png)

다음을 수행할 수 있습니다.

- 현재 조사에 대한 시각적 개요를 얻습니다.
- 조사 기간의 요약을 시청합니다.
- 시각화에서 노드를 선택하여 해당 노드에 대한 세부 정보를 볼 수 있습니다.
- 위쪽에서 탭을 선택하여 해당 탭에 대한 세부 정보를 볼 수 있습니다.

### <a name="alert-investigation"></a>경고 조사

조사를 **위한** 알림 탭에서 조사와 관련된 경고를 볼 수 있습니다. 세부 정보에는 조사를 트리거한 경고 및 위험한 로그인, [DLP](https://docs.microsoft.com/Microsoft-365/compliance/data-loss-prevention-policies) 정책 위반 등 조사와 상호 관련이 있는 기타 관련 경고가 포함됩니다. 이 페이지에서 보안 분석가가 개별 경고에 대한 추가 세부 정보를 볼 수도 있습니다.

![AIR 경고 페이지](../../media/air-investigationalertspage.png)

다음을 수행할 수 있습니다.

- 현재 트리거되는 경고 및 모든 관련 경고에 대한 시각적 개요를 확인할 수 있습니다.
- 목록에서 경고를 선택하여 전체 경고 세부 정보를 표시하는 플라이아웃 페이지를 열 수 있습니다.

### <a name="email-investigation"></a>전자 메일 조사

조사를 **위해 전자** 메일 탭에서 조사의 일부로 식별된 유사한 전자 메일의 원본 전자 메일 및 클러스터를 볼 수 있습니다. 또한 **전자 메일** 탭에는 사용자가 보고한 전자 메일 세부 정보, 보고된 원본 전자 메일, 맬웨어/피싱으로 인해 잠기던 전자 메일 메시지 등 조사와 관련된 전자 메일 항목도 표시됩니다.

![AIR 전자 메일 조사 페이지](../../media/air-investigationemailpage.png)

전자 메일 조사를 사용하여 다음을 할 수 있습니다.

- 발견된 현재 클러스터링 결과 및 위협에 대한 시각적 개요를 얻습니다.
- 클러스터 엔터티 또는 위협 목록을 클릭하여 전체 경고 세부 정보를 표시하는 플라이아웃 페이지를 열 수 있습니다.
- 전자 메일 클러스터 세부 정보  탭의 맨 위에 있는 탐색기에서 열기 링크를 클릭하여 전자 메일 클러스터를 추가로 **조사합니다.**

![플라이아웃 세부 정보가 있는 AIR 조사 전자 메일](../../media/air-investigationemailpageflyoutdetails.png)

조직의 사용자가 보내고 받는 전자 메일의 양과 전자 메일 통신 및 공격의 다중 사용자 특성에 따라 다음 프로세스에 많은 시간이 걸릴 수 있습니다.

1. 메시지 헤더, 본문, URL 및 첨부 파일에서 유사한 특성을 기반으로 전자 메일 메시지를 클러스터링합니다.
2. 악성 전자 메일과 좋은 전자 메일 분리
3. 악의적인 전자 메일 메시지에 대한 작업 수행

AIR은 이 프로세스를 자동화하여 조직의 보안 팀과 노력을 절약합니다.

#### <a name="types-of-email-clusters"></a>전자 메일 클러스터 유형

전자 메일 분석 단계에서 유사성 클러스터(모든 조사), 지표 클러스터(모든 조사) 및 사서함/사용자 클러스터의 세 가지 유형의 전자 메일 클러스터를 식별할 수 있습니다. 다음 표에서는 이러한 유형의 전자 메일 클러스터에 대해 설명합니다.

|전자 메일 클러스터|설명|
|---|---|
|유사성 클러스터|보낸 사람 및 콘텐츠 특성이 비슷한 전자 메일을 헌팅하여 식별된 전자 메일 메시지입니다. 이러한 클러스터는 원래 검색 결과를 기반으로 악성 콘텐츠가 평가됩니다. 악의적인 전자 메일 검색을 충분히 포함하는 전자 메일 클러스터는 악의적인 것으로 간주됩니다.|
|표시기 클러스터|원본 전자 메일에서 동일한 표시기 엔터티(파일 해시 또는 URL)를 헌팅하여 식별된 전자 메일 메시지입니다. 원래 파일/URL 엔터티가 악성으로 식별되면 AIR은 해당 엔터티가 포함된 전자 메일 메시지의 전체 클러스터에 표시기 판정을 적용합니다. 맬웨어로 식별된 파일은 해당 파일을 포함하는 전자 메일 메시지 클러스터가 맬웨어 전자 메일 메시지로 처리됩니다.|
|사서함/사용자 클러스터|사용자 손상 조사에 관련된 사용자와 관련된 전자 메일 메시지입니다. 이러한 전자 메일 클러스터는 보안 운영 팀의 추가 분석용으로, 전자 메일 수정 작업을 생성하지 않습니다. <p> 손상된 사용자 보안 플레이북은 사서함에서 전송되는 전자 메일이 미칠 수 있는 영향을 이해하기 위해 분석되는 사용자가 전송하는 전자 메일을 검토합니다.|

> [!NOTE]
> 클러스터링의 목표는 공격 또는 캠페인의 일부로 동일한 보낸 사람이 보낸 다른 관련 전자 메일 메시지를 헌팅하고 찾는 것입니다.  경우에 따라 합법적인 전자 메일이 조사를 트리거할 수 있습니다(예: 사용자가 마케팅 전자 메일을 보고).  이러한 시나리오에서 전자 메일 클러스터링은 전자 메일 클러스터가 악성이 아니라는 것을  식별해야 합니다. 적절한 경우 위협을 나타내지 않으며 전자 메일 제거를 권장하지 않습니다.

#### <a name="email-classifications"></a>전자 메일 분류

전자 메일 메시지를 분석할 때 악의적, 의심스러운 메시지  또는 정리된 메시지로 분류됩니다(위협으로 식별되지는 *않은* 경우).  

- *사서함/사용자가* 보낸 악의적인 전자 메일은 사서함/계정의 잠재적 손상을 나타냅니다. 손상의 일부로 악의적인 전자 메일의 영향을 받는 다른 사용자/사서함이 표시됩니다.

- *사서함/사용자가* 보낸 의심스러운 전자 메일은 손상된 계정 또는 원치 않는 전자 메일 활동이 발생할 수 있는 가능성을 나타냅니다. 이러한 메시지에는 사서함에서 보낸 스팸/대량 전자 메일이 포함됩니다.

- *사서함/사용자가* 보낸 클린 전자 메일(위협이 아닌 것으로 간주되는 전자 메일)은 보안 운영 팀에 전송된 합법적인 사용자 전자 메일 보기를 제공할 수 있습니다. 그러나 이러한 전자 메일은 전자 메일 계정이 손상된 경우 데이터 유출을 포함할 수도 있습니다.

#### <a name="more-about-email-counts"></a>전자 메일 수에 대한 자세한 내용은

전자 메일 탭에 식별된 전자 메일 수는 현재 전자 메일 탭에 표시된 모든 전자 메일 메시지의 합계를 **나타내고** 있습니다. 전자 메일 메시지는 여러 클러스터에 존재하기 때문에 식별된(수정 작업의 영향을 받는) 전자 메일 메시지의 실제 총 수는 모든 클러스터 및 원래 받는 사람의 전자 메일 메시지에 걸쳐 있는 고유한 전자 메일 메시지의 수입니다.

보안 [판정,](threat-explorer.md) 작업 및 배달 위치는 받는 사람별로 다르기 때문에 탐색기 및 AIR 개수 전자 메일 메시지는 받는 사람별로 계산됩니다. 따라서 세 사용자에게 전송된 원래 전자 메일은 전자 메일이 아닌 총 3개의 전자 메일 메시지로 계산됩니다.

전자 메일에 여러 작업이 있는 경우나 모든 작업이 발생할 때 전자 메일 복사본이 여러 개 있는 경우와 같이 전자 메일이 두 번 이상 계산되는 경우도 있습니다.

예를 들어 배달 시 감지된 맬웨어 전자 메일은 차단(고지된) 전자 메일과 대체된 전자 메일(경고 파일로 대체된 위협 파일을 사용자 사서함으로 배달)할 수 있습니다. 시스템에 전자 메일의 복사본이 문자 그대로 두 개 있기 때문에 둘 다 클러스터 수에서 계산될 수 있습니다.

> [!IMPORTANT]
> 다음은 유의해야 할 몇 가지 사항입니다.
>
> - 전자 메일 개수는 조사 시에 계산하며, 일부 개수는 조사 플라이아웃을 열 때(기초 쿼리를 기반으로) 다시 계산됩니다.
>
> - 전자 메일 탭의 전자 메일 클러스터에 대해 표시되는 전자 메일 수와 클러스터 플라이아웃에 표시된 전자 메일 수량 값은 조사 시 계산하며 변경되지 않습니다. 
>
> - 전자 메일 클러스터 플라이아웃의 전자 메일 탭 아래쪽에 표시되는 전자 메일 수와 탐색기에 표시된 전자 메일 메시지 수에는 조사 초기 분석 후 받은 전자 메일 메시지가 반영됩니다. 

따라서 조사 분석 단계 사이에 5개의 전자 메일 메시지가 도착하고 관리자가 조사를 검토할 때 원래 수량인 10개의 전자 메일 메시지를 표시하는 전자 메일 클러스터에는 총 15개의 전자 메일 목록이 표시됩니다. 마찬가지로, Office 365 요금제 2용 Microsoft Defender의 데이터는 평가판을 위해 7일 후에 그리고 유료 라이선스에 대해 30일 후에 만료하기 때문에 이전 조사는 탐색기 쿼리에 표시하는 것보다 더 높은 수를 표시하기 시작할 수 있습니다.

조사 시 전자 메일에 미치는 영향과 수정이 실행될 때까지 현재의 영향을 나타내기 위해 다양한 보기에서 수 기록 및 현재 수를 모두 표시하는 것이 수행됩니다.

> [!NOTE]
> 전자 메일 컨텍스트에서 조사의 일부로 볼륨 이상 위협 표면이 표시될 수 있습니다. 볼륨 이상은 이전 기간과 비교하여 조사 이벤트 시간과 비슷한 전자 메일 메시지의 스파이크를 나타냅니다. 이와 같은 특성이 비슷한 전자 메일 트래픽(예: 제목 및 보낸 사람 도메인, 본문 유사성 및 보낸 사람 IP)이 전자 메일 캠페인 또는 공격 시작의 일반적인 예입니다.
> 그러나 대량, 스팸 및 합법적인 전자 메일 캠페인은 일반적으로 이러한 특성을 공유합니다.
>
> 볼륨 이상은 잠재적인 위협을 나타내며, 그에 따라 바이러스 백신 엔진, 탐지 또는 악의적인 신뢰도로 식별된 맬웨어 또는 피싱 위협에 비해 심각하지 않은 것일 수 있습니다.

### <a name="user-investigation"></a>사용자 조사

사용자 **탭에서** 조사의 일부로 식별된 모든 사용자를 볼 수 있습니다. 사용자 계정은 해당 사용자 계정이 영향을 받거나 손상될 수 있는 이벤트가 있는 경우 조사에 나타납니다.

예를 들어 다음 이미지에서 AIR은 생성된 새 받은 편지함 규칙을 기반으로 손상 및 예외를 식별했습니다. 조사에 대한 추가 세부 정보(증거)는 이 탭 내의 자세한 보기를 통해 사용할 수 있습니다. 손상 표시기 및 이상은 [Microsoft Cloud App Security의](https://docs.microsoft.com/cloud-app-security)이상 검색도 포함할 수 있습니다.

![AIR 조사 사용자 페이지](../../media/air-investigationuserspage.png)

다음을 수행할 수 있습니다.

- 식별된 사용자 결과 및 위험 발견에 대한 시각적 개요를 얻습니다.

- 전체 경고 세부 정보를 표시하는 플라이아웃 페이지를 열 사용자를 선택합니다.

### <a name="machine-investigation"></a>컴퓨터 조사

컴퓨터 **탭에서** 조사의 일부로 식별된 모든 컴퓨터를 볼 수 있습니다.

![AIR 조사 컴퓨터 페이지](../../media/air-investigationmachinepage.png)

일부 플레이북의 일부로 AIR은 전자 메일 위협을 장치(예: Zapped 맬웨어)에 상관 관계화합니다. 예를 들어 조사는 악성 파일 해시를 [끝점용 Microsoft Defender로](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection
) 전달하여 조사합니다. 이렇게 하면 사용자에 대한 관련 컴퓨터를 자동화된 조사를 통해 클라우드와 끝점에서 위협이 모두 해결되도록 할 수 있습니다.

다음을 수행할 수 있습니다.

- 발견된 현재 컴퓨터 및 위협에 대한 시각적 개요를 얻습니다.

- Microsoft Defender 보안 센터에서 끝점 조사를 위한 [관련 Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) 조사에 해당 보기를 열기 위한 컴퓨터 선택

### <a name="entity-investigation"></a>엔터티 조사

엔터티 **탭에서** 조사의 일부로 식별 및 분석된 엔터티를 볼 수 있습니다.

여기에서 조사된 엔터티와 엔터티 유형(예: 전자 메일 메시지, 클러스터, IP 주소, 사용자 등)의 세부 정보를 볼 수 있습니다. 또한 분석된 엔터티 수와 각 엔터티와 연관된 위협도 볼 수 있습니다.

![AIR 조사 엔터티 페이지](../../media/air-investigationentitiespage.png)

다음을 수행할 수 있습니다.

- 발견된 조사 엔터티 및 위협에 대한 시각적 개요를 얻습니다.

- 관련 엔터티 세부 정보를 표시하는 플라이아웃 페이지를 열 엔터티를 선택합니다.

![AIR 조사 엔터티 세부 정보](../../media/air-investigationsentitiespagedetails.png)

### <a name="playbook-log"></a>Playbook 로그

로그 **탭에서** 조사 중에 발생한 모든 플레이북 단계를 볼 수 있습니다. 로그는 AIR의 일부로 Office 365 자동 조사 기능에 의해 완료된 모든 분석기 및 작업의 전체 인벤토리를 캡처합니다. 작업 자체, 설명 및 실제 시작부터 완료까지의 기간을 포함하여 수행되는 모든 단계를 명확하게 볼 수 있습니다.

![AIR 조사 로그 페이지](../../media/air-investigationlogpage.png)

다음을 수행할 수 있습니다.

- 수행한 플레이북 단계에 대한 시각적 개요를 확인할 수 있습니다.
- 결과를 CSV 파일로 내보낼 수 있습니다.
- 보기를 필터링합니다.

### <a name="recommended-actions"></a>권장 작업

작업 **탭에서** 조사가 완료된 후 수정에 권장되는 모든 플레이북 작업을 볼 수 있습니다. 작업은 조사가 끝날 때 Microsoft에서 권장하는 단계를 캡처합니다. 여기서 하나 이상의 작업을 선택하여 수정 작업을 수행할 수 있습니다.

승인을 **선택하면** 수정을 시작할 수 있습니다. 적절한 사용 권한이 필요합니다.  탐색기 및 AIR에서 작업을 실행하려면 검색 및 제거 역할이 필요합니다.

예를 들어 보안 읽기는 작업을 볼 수 있지만 승인할 수 없습니다.

> [!IMPORTANT]
> 모든 작업을 승인할 것은 없습니다. 권장 작업에 동의하지 않는 경우 또는 조직에서 특정 유형의 작업을 선택하지  않는 경우 작업을 거부하거나 무시하고 아무 작업도 수행하지 않을 수 있습니다.
> 모든 작업을 수락 및/또는 거부하면 조사가 완전히 닫히고(상태가 수정됩니다) 일부 작업이 불완전해진 상태로 두면 조사 상태가 부분적으로 수정된 상태로 변경됩니다.

![AIR 조사 작업 페이지](../../media/air-investigationactionspage.png)

다음을 수행할 수 있습니다.

- 플레이북 권장 작업에 대한 시각적 개요를 확인할 수 있습니다.
- 단일 작업 또는 여러 작업을 선택합니다.
- 설명을 통해 권장 작업을 승인하거나 거부합니다.
- 결과를 CSV 파일로 내보낼 수 있습니다.
- 보기를 필터링합니다.

## <a name="next-steps"></a>다음 단계

- [보류 중인 작업 검토 및 승인](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
