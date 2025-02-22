---
title: 랜섬웨어에 대한 전자 메일 규칙 만들기
f1.keywords:
- NOCSH
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
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: 랜섬웨어를 방지하기 위한 전자 메일 규칙을 만드는 방법을 배워야 합니다.
ms.openlocfilehash: 85898480438225848fc09db9a9c507045f8a182c
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702449"
---
# <a name="create-email-rules-to-prevent-ransomware"></a>랜섬웨어를 방지하는 전자 메일 규칙 만들기

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

Microsoft 365는 JavaScript, 배치 및 실행 파일과 같은 잠재적으로 위험한 파일이 Outlook에서 열리지 못하게 하여 랜섬웨어로부터 비즈니스를 보호합니다. 추가 파일 형식을 차단하거나 경고하는 규칙을 추가하여 이 보호 수준을 높이기 위해 다음 단계를 수행합니다.

## <a name="try-it"></a>사용해 보세요!

1. 관리 센터에서 [https://admin.microsoft.com](https://admin.microsoft.com) 관리 **센터에서 Exchange를** **선택하세요.**
1. 왼쪽의 메뉴에서 메일 **흐름을 선택합니다.**
1. 규칙 탭에서 더하기(+) 기호 옆에 있는 화살표를 선택한 다음 새 규칙 **만들기를 선택합니다.**
1. 새 규칙 **페이지에서** 규칙의 이름을 입력하고 아래쪽으로 스크롤한 다음 추가 옵션을 **선택합니다.**
1. 이 **규칙 적용 아래에서** 첨부 파일을 선택한 다음 다음 단어를 포함하는 파일 **확장명을 선택합니다.** 
1. 단어나 구를 지정하는 상자에 규칙을 적용할 파일 확장명(예: 매크로를 포함할 수 있는 파일 확장명)을 입력합니다.  더하기(+) 기호를 사용하여 한 번씩 추가합니다.

    랜섬웨어로부터 보호를 읽어 파일 형식에 대해 [자세히 알아보십시오.](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/secure-your-business-data#ransomware)

1. 아래로 스크롤하여 목록을 검토한 다음 확인을 **선택합니다.**
1. 새 규칙 **페이지에서** 조건 추가를 선택한 다음 다음을 할 때 **조건을 선택합니다.**
1. 선택할 수 있는 규칙 옵션이 많지만 이 예에서는 받는 사람에게 메시지를 **알리도록 선택합니다.**
1. 알림에 대한 메시지 텍스트를 입력하고 확인을 **선택하십시오.**
1. 선택 사항:  새 규칙 페이지에서 예외 추가를 선택하고 규칙 예외에 대한 세부 정보(예: 신뢰할 수 있는 보낸 사람이 보낸 메시지)를 입력합니다.
1. 새 규칙 페이지에서 저장을 **선택하고** 제공된 규칙 요약 정보를 검토합니다.