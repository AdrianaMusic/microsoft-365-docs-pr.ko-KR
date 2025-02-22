---
title: 위협 탐색기 및 실시간 검색의 보기
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 위협 탐색기 및 실시간 검색 보고서를 사용하여 보안 및 준수 센터에서 위협을 조사하고 & 방법에 대해 자세히 알아보십시오.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b7300f8c87b100a38117b0cc4bee1bb95c9584c6
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615711"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>위협 탐색기 및 실시간 검색 보기

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


![위협 탐색기](../../media/ThreatExplorerFirstOpened.png)

[위협](threat-explorer.md) 탐색기(및 실시간 검색 보고서)는 보안 운영 팀이 보안 및 준수 센터에서 위협을 조사하고 대응하는 데 도움이 되는 강력한 거의 & 도구입니다. 탐색기(및 실시간 검색 보고서)는 Office 365의 전자 메일 및 파일에 의심되는 맬웨어 및 피싱과 조직에 대한 기타 보안 위협 및 위험에 대한 정보를 표시합니다.

- [Office 365 요금제 2용 Microsoft Defender가](office-365-atp.md) 있는 경우 탐색기가 있습니다.
- Office 365 요금제 1용 Microsoft Defender가 있는 경우 실시간 검색이 있습니다.

탐색기(또는 실시간 검색 보고서)를 처음 열면 기본 보기에 지난 7일 동안의 전자 메일 맬웨어 검색이 표시됩니다. 또한 이 보고서에는 안전한 링크로 검색된 악의적인 URL, 안전한 첨부 [](atp-safe-links.md)파일에서 검색된 악성 파일 등 Office 365용 Microsoft Defender 검색이 표시될 [수도 있습니다.](atp-safe-attachments.md) 이 보고서는 지난 30일 동안의 데이터를 표시하기 위해 수정할 수 있습니다(Office 365 P2 유료 구독용 Microsoft Defender 사용). 평가판 구독에는 지난 7일 동안의 데이터만 포함됩니다.

****

|구독|유틸리티|데이터 일 수|
|---|---|---|
|Microsoft Defender for Office 365 P1 평가판|실시간 탐지|7 |
|Office 365 P1용 Microsoft Defender 유료|실시간 탐지|30|
|Office 365 P1용 Microsoft Defender 유료 테스트 Defender for Office 365 P2 평가판|위협 탐색기|7 |
|Microsoft Defender for Office 365 P2 평가판|위협 탐색기|7 |
|Office 365 P2용 Microsoft Defender 유료|위협 탐색기|30|
|

보기 **메뉴를** 사용하여 표시되는 정보를 변경합니다. 도구tips를 사용하면 사용할 보기를 결정하는 데 도움이 됩니다.

![위협 탐색기 보기 메뉴](../../media/ThreatExplorerViewMenu.png)

보기를 선택한 후 필터를 적용하고 추가 분석을 수행하기 위한 쿼리를 설정할 수 있습니다. 다음 섹션에서는 탐색기에서 사용할 수 있는 다양한 보기(또는 실시간 검색)에 대한 간략한 개요를 제공합니다.

## <a name="email--malware"></a>전자 메일 > 맬웨어

이 보고서를 확인하려면 탐색기(또는 실시간 검색)에서 전자 메일 맬웨어  \> **보기를** \> **선택하십시오.** 이 보기에는 맬웨어가 포함된 것으로 확인된 전자 메일 메시지에 대한 정보가 표시됩니다.

![맬웨어로 식별된 전자 메일에 대한 데이터 보기](../../media/ExplorerEmailMalwareMenu.png)

보낸 **사람 클릭하여** 보기 옵션 목록을 열 수 있습니다. 이 목록을 사용하여 보낸 사람, 받는 사람, 보낸 사람 도메인, 제목, 검색 기술, 보호 상태 등에서 데이터를 볼 수 있습니다.

예를 들어 검색된 전자 메일 메시지에 대해 수행된 작업을 확인하기 위해 목록에서 **보호** 상태를 선택합니다. 옵션을 선택한 다음 새로 고침 단추를 클릭하여 보고서에 해당 필터를 적용합니다.

![위협 탐색기용 위협 방지 상태 옵션](../../media/ThreatExplorerProtectionStatusOptions.png)

차트 아래에서 특정 메시지에 대한 자세한 내용을 볼 수 있습니다. 목록에서 항목을 선택하면 선택한 항목에 대한 자세한 내용을 볼 수 있는 플라이아웃 창이 열립니다.

![플라이아웃이 열린 위협 탐색기](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>피싱 > 메일

이 보고서를 확인하려면 탐색기(또는 실시간 검색)에서 전자 메일 피싱  \>  \> **보기를 선택하십시오.** 이 보기에는 피싱 시도로 식별된 전자 메일 메시지가 표시됩니다.

![피싱 시도로 식별된 전자 메일에 대한 데이터 보기](../../media/ThreatExplorerEmailPhish.png)

보낸 **사람 클릭하여** 보기 옵션 목록을 열 수 있습니다. 이 목록을 사용하여 보낸 사람, 받는 사람, 보낸 사람 도메인, 보낸 사람 IP, URL 도메인, 클릭 판정 등에서 데이터를 볼 수 있습니다.

예를 들어 피싱 시도로 식별된 URL을 클릭할 때 수행된 작업을 보려면  목록에서 판정 클릭을 선택하고 하나 이상의 옵션을 선택한 다음 새로 고침 단추를 클릭합니다.

![피싱 보고서에 대한 결과 옵션 클릭](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

차트 아래에서 특정 메시지, URL 클릭, URL 및 전자 메일 출처에 대한 자세한 정보를 확인합니다.

![전자 메일 메시지에서 피싱으로 검색된 URL](../../media/ThreatExplorerEmailPhishURLs.png)

목록에서 항목(예: 검색된 URL)을 선택하면 선택한 항목에 대한 자세한 내용을 볼 수 있는 플라이아웃 창이 열립니다.

![검색된 URL에 대한 세부 정보](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>전자 > 제출

이 보고서를 확인하려면 탐색기(또는 실시간 검색)에서 **전자** 메일 제출 \>  \> **보기를 선택하십시오.** 이 보기에는 사용자가 정크 메일이 아닌 정크 메일 또는 피싱 전자 메일로 보고한 전자 메일이 표시됩니다.

![사용자가 보고한 전자 메일 메시지](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

보낸 **사람 클릭하여** 보기 옵션 목록을 열 수 있습니다. 이 목록을 사용하여 보낸 사람, 받는 사람, 보고서 유형(전자 메일이 정크 메일이 아니라 정크 메일 또는 피싱으로 확인) 등의 정보를 볼 수 있습니다.

예를 들어 피싱 시도로 보고된 전자 메일 메시지에 대한  정보를 보려면 보낸 사람 보고서 유형을 클릭하고 \>  **피싱을** 선택한 다음 새로 고침 단추를 클릭합니다.

![보고서 유형 필터에 대해 선택된 피싱](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

차트 아래에서 제목 줄, 보낸 사람 IP 주소, 메시지를 정크 메일로 보고한 사용자, 정크 메일 메시지 또는 피싱 등의 특정 전자 메일 메시지에 대한 세부 정보를 볼 수 있습니다.

![피싱 시도로 보고된 메시지](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

목록에서 항목을 선택하여 추가 세부 정보를 볼 수 있습니다.

## <a name="email--all-email"></a>전자 > 전자 메일

이 보고서를 확인하려면 탐색기에서 **전자** 메일 모두 \>  \> **보기를 선택하십시오.** 이 보기는 피싱 또는 맬웨어로 인해 악의적인 것으로 식별된 전자 메일뿐만 아니라 모든 악성 메일(일반 전자 메일, 스팸 및 대량 메일)을 포함하여 전자 메일 활동에 대한 전체 보기를 보여줍니다.

> [!NOTE]
> 표시할 데이터가 너무 많을 경우 필터를 추가하고 필요한 경우 보고 있는 날짜 범위를 좁힐 수 있습니다. 

필터를 적용하려면 **보낸** 사람, 목록에서 항목을 선택한 다음 새로 고침 단추를 클릭합니다. 이 예제에서는 검색  기술을 필터로 사용했습니다(몇 가지 옵션을 사용할 수 있습니다). 보낸 사람, 보낸 사람의 도메인, 받는 사람, 제목, 첨부 파일 이름, 맬웨어 패밀리, 보호 상태(Office 365의 위협 방지 기능 및 정책에 의해 수행되는 작업), 검색 기술(맬웨어가 검색된 방법) 등으로 정보를 볼 수 있습니다.

![검색 기술로 검색된 전자 메일에 대한 데이터 보기](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

차트 아래에서 제목 줄, 받는 사람, 보낸 사람, 상태 등 특정 전자 메일 메시지에 대한 자세한 내용을 볼 수 있습니다.

## <a name="content--malware"></a>콘텐츠 > 맬웨어

이 보고서를 보고 탐색기(또는 실시간 검색)에서 콘텐츠 맬웨어  \> **보기를** \> **선택하십시오.** 이 보기는 SharePoint Online, 비즈니스용 [OneDrive 및 Microsoft Teams에서 Office 365용 Microsoft Defender에](atp-for-spo-odb-and-teams.md)의해 악성으로 식별된 파일을 보여줍니다.

맬웨어 패밀리, 검색 기술(맬웨어가 검색된 방법) 및 워크로드(OneDrive, SharePoint 또는 Teams)를 통해 정보를 볼 수 있습니다.

![검색된 맬웨어에 대한 데이터 보기](../../media/d11dc568-b091-4159-b261-df13d76b520b.png)

차트 아래에서 첨부 파일 이름, 작업량, 파일 크기, 파일을 마지막으로 수정한 사람 등 특정 파일에 대한 자세한 정보를 들을 수 있습니다.

## <a name="click-to-filter-capabilities"></a>Click-to-filter capabilities

탐색기(및 실시간 검색)를 사용하여 클릭으로 필터를 적용할 수 있습니다. 범례에서 항목을 클릭하면 해당 항목이 보고서의 필터가 됩니다. 예를 들어 탐색기에서 맬웨어 보기를 보고 있는 경우를 가정해 보겠습니다.

![위협 관리 \> 탐색기로 이동](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

이 **차트에서 ATP** 검색을 클릭하면 보기가 다음으로 표시됩니다.

![Office 365 검색 결과용 Defender만 표시하기 위해 필터링된 탐색기](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

이 보기에서는 이제 안전한 첨부 파일로 검색된 파일에 대한 [데이터를 보고 있습니다.](atp-safe-attachments.md) 차트 아래에서는 안전한 첨부 파일에서 검색된 첨부 파일이 있는 특정 전자 메일 메시지에 대한 세부 정보를 볼 수 있습니다.

![검색된 첨부 파일이 있는 전자 메일 메시지에 대한 특정 세부 정보](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

하나 이상의 항목을 선택하면 **동작** 메뉴가 활성화되어 선택한 항목에 대해 선택할 수 있는 여러 가지 선택 항목이 제공됩니다.

![항목을 선택하면 동작 메뉴가 활성화됩니다.](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

클릭으로 필터링하고 특정 세부 정보로 이동하는 기능을 사용하면 위협을 조사하는 데 많은 시간을 절약할 수 있습니다.

## <a name="queries-and-filters"></a>쿼리 및 필터

탐색기(및 실시간 검색 보고서)에는 상위 대상 사용자, 상위 맬웨어 패밀리, 검색 기술 등의 세부 정보를 드릴다운할 수 있는 몇 가지 강력한 필터 및 쿼리 기능이 있습니다. 각 보고서 종류는 데이터를 보고 탐색하는 다양한 방법을 제공합니다.

> [!IMPORTANT]
> 탐색기(또는 실시간 검색)에 대한 쿼리 표시줄에 추가 또는 물음표와 같은 와일드카드 문자를 사용하지 않습니다. 제목 필드에서  전자 메일 메시지를 검색할 때 탐색기(또는 실시간 검색)는 부분 일치를 수행하고 와일드카드 검색과 유사한 결과를 산출합니다.
