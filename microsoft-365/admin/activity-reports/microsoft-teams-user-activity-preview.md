---
title: 관리 센터의 Microsoft 365 보고서 - Microsoft Teams 사용자 활동
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Microsoft Teams 사용자 활동 보고서를 얻고 조직의 Teams 활동에 대한 인사이트를 얻는 방법을 학습합니다.
ms.openlocfilehash: 7e32ca6b665cab9da93dec9632ef25176db0e839
ms.sourcegitcommit: 039205fdaaa2a233ff7e95cd91bace474b84b68c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49611403"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>관리 센터의 Microsoft 365 보고서 - Microsoft Teams 사용자 활동

Microsoft 365 **보고서** 대시보드에는 조직의 제품 전체에 대한 활동 개요가 표시됩니다. 보고서 대시보드를 통해 개별 제품 수준 보고서의 하위 수준을 표시하여 각 제품 내의 활동에 대한 더 세부화된 정보를 확인할 수 있습니다. [보고서 개요 항목](activity-reports.md)을 확인하세요. Microsoft Teams 사용자 활동 보고서에서는 조직의 Microsoft Teams 활동에 대한 정보를 확인할 수 있습니다.
  
> [!NOTE]
> Microsoft 365의 전역 관리자, 전역 읽기 권한자 또는 보고서 읽기 권한자 또는 Exchange, SharePoint, Teams 서비스, Teams 커뮤니케이션 또는 비즈니스용 Skype 관리자인 경우 보고서를 볼 수 있어야 합니다.  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Microsoft Teams 사용자 활동 보고서에 액세스하는 방법

1. 관리 센터에서 **보고서** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">사용 현황</a> 페이지를 참조하세요.
2. 대시보드 홈페이지에서 Microsoft Teams 활동 **View more** 카드에서 더 보기 단추를 클릭합니다.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Microsoft Teams 사용자 활동 보고서 해석

사용자 활동 탭을 선택하여 Teams 보고서에서 사용자 **활동을 볼 수** 있습니다. <br/>![Microsoft 365 보고서 - Microsoft Teams 사용자 활동.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

열 **선택을 선택하여** 보고서에서 열을 추가하거나 제거합니다.  <br/> ![Teams user activity report - choose columns](../../media/a1513028-cf09-4186-93a6-8a203cd22475.png)

내보내기 링크를 선택하여 보고서 데이터를 Excel .csv 파일로 내보낼 **수** 있습니다. 그러면 모든 사용자의 데이터를 내보내고 향후 분석을 위해 간단하게 정렬 및 필터링을 수행할 수 있습니다. 사용자가 2,000명 미만인 경우 보고서 자체의 표에서 정렬 및 필터링할 수 있습니다. 사용자가 2,000명 이상인 경우 필터링 및 정렬하려면 데이터를 내보내야 합니다. 오디오 **시간,** 비디오 시간 **video time** 및 화면 **공유** 시간의 내보낼 형식은 ISO8601 기간 형식을 따르게 됩니다.

데이터 품질을 보장하기 위해 지난 3일 동안 매일 데이터 유효성 검사를 수행하고 감지된 간격을 모두 채우게 됩니다. 프로세스 중에 기록 데이터에서 차이가 발견될 수 있습니다.

|항목|설명|
|:-----|:-----|
|**메트릭**|**정의**|
|사용자 이름  <br/> |사용자의 전자 메일 주소입니다. 실제 전자 메일 주소를 표시하거나 이 필드를 익명으로 만들 수 있습니다.   <br/> |
|채널 메시지   <br/> |사용자가 지정된 기간 동안 팀 채팅에 게시한 고유 메시지 수입니다.  <br/> |
|채팅 메시지   <br/> |사용자가 지정된 기간 동안 비공개 채팅에 게시한 고유 메시지 수입니다.  <br/> |
|총 모임 수   <br/> |지정된 기간 동안 사용자가 참가한 온라인 모임 수입니다.  <br/> |
|1:1 통화   <br/> | 지정된 기간 동안 사용자가 참여한 1:1 통화 수입니다.  <br/> |
|마지막 활동 날짜(UTC)  <br/> |사용자가 Microsoft Teams 활동에 마지막으로 참여한 날짜입니다.<br/> |
|모임에 참가한 adhoc   <br/> | 지정된 기간 동안 사용자가 참가한 일정에 예약되지 않은 모임 수입니다.  <br/> |
|모임이 조직된 애드후크 <br/> |지정된 기간 동안 사용자가 구성한 일정에 예약되지 않은 모임 수입니다. <br/>|
|예약된 모임  <br/> |지정된 기간 동안 사용자가 구성한 예약된 모임 수입니다.  <br/> |
|사용이 허가됩니다. |사용자에게 Teams를 사용할 수 있는 라이선스가 있는 경우 선택됩니다.|
|기타 활동|사용자는 활성 상태이지만 보고서에 제공된 노출된 작업 유형(채널 메시지 및 채팅 메시지 보내기 또는 회신, 1:1 통화 및 모임에 참가 또는 참가)보다 다른 작업을 수행했습니다. 예제 작업은 사용자가 Teams 상태 또는 Teams 상태 메시지를 변경하거나 채널 메시지 게시물을 열지만 회신하지 않는 경우입니다. |
|||