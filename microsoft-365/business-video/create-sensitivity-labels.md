---
title: 민감도 레이블 만들기
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
description: 민감도 레이블을 만들고 관리하는 방법을 학습합니다.
ms.openlocfilehash: ff3f7eb5ffddf797e254fac0ed8fc87d96940455
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49703214"
---
# <a name="protect-documents-with-sensitivity-labels"></a>민감도 레이블을 통해 문서 보호

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

민감도 레이블을 사용하면 비즈니스에 중요한 콘텐츠를 분류하고 보호할 수 있습니다.

## <a name="try-it"></a>사용해 보세요!

1. 관리 [센터에서](https://admin.microsoft.com)준수 관리 **센터를** 선택합니다.
1. **분류를** 선택한 다음 **민감도 레이블을 선택합니다.**
1. 레이블 **만들기를 선택하고** 경고가 나타나면 예를 **선택합니다.**
1. 레이블 이름, **도구** **설명 및** 설명을 **입력합니다.** **다음** 을 선택합니다.
1. 암호화 **켜기.** 사용 권한을 할당할 시간, 콘텐츠에 대한 사용자의 액세스가 만료될지 여부 및 오프라인 액세스를 허용할지 여부를 선택하세요.
1. **사용 권한 할당을** 선택한 다음 이러한 전자 메일 **주소 또는 도메인을 추가합니다.**
1. 전자 메일 주소 또는 도메인 이름(예: Contoso.org.  추가를 **선택하고** 추가할 각 전자 메일 주소 또는 도메인에 대해 반복합니다.
1. 미리 **설정하거나 사용자 지정에서 사용 권한 선택을 선택합니다.**
1. 드롭다운 목록을 사용하여 미리 설정한 사용 권한(예: **검토자** 또는  뷰어)을 선택하거나 **사용자** 지정 권한을 선택합니다. 사용자 지정을 **선택한 경우** 목록에서 사용 권한을 선택합니다. **저장,** **저장,** 다음을 **선택합니다.**
1. 콘텐츠 **표시를 켜고** 사용할 표시를 선택하세요.
1. 선택한 각 표시에 대해 텍스트 사용자 **지정을 선택합니다.** 문서에 표시하려는 텍스트를 입력하고 글꼴 및 레이아웃 옵션을 설정할 수 있습니다. **저장을** 선택한 다음 추가 표시에 대해 반복합니다. **다음** 을 선택합니다.
1. 선택적으로 끝점 데이터 **손실 방지를 켜야 합니다.** **다음** 을 선택합니다.
1. 선택적으로 자동 레이블 **지정을 켜야 합니다.** 조건을 추가합니다. 예를 들어 포함된 콘텐츠 검색 **아래에서** 조건 **추가를 선택합니다.** 조건을 입력합니다. 예를 들어 passport, Social Security 또는 기타 중요한 정보가 감지되면 레이블이 추가되는 조건을 추가합니다. **다음** 을 선택합니다.
1. 설정을 검토하고 만들기를 **선택합니다.** 레이블이 만들어졌습니다. 원하는 추가 레이블에 대해 이 프로세스를 반복합니다.
1. 기본적으로 레이블은 Office 앱에 **기밀,** 내부 및 공용 순서로 **표시됩니다.** 순서를 변경하려면 각 레이블에  대해 추가 작업(타원)을 선택한 다음 레이블을 위나 아래로 이동하십시오. 일반적으로 사용 권한은 가장 낮은 권한에서 가장 높은 수준의 사용 권한으로 나열됩니다.
1. 레이블에 하위 레이블을 추가하려면 **추가** 작업을 선택한 다음 하위 **수준을 추가합니다.**
1. 완료되면 레이블 게시를 **선택하고** **게시할** 레이블을 선택한 다음 **추가합니다.** 게시할 레이블을 선택하고 **추가,** 완료 및 다음을 **선택합니다.**
1. 기본적으로 새 레이블 정책은 모든 사용자에 적용됩니다. 정책이 적용되는 사용자를 제한하려면 사용자 또는 그룹 **선택을** 선택한 다음 추가를 **선택합니다.** 정책을 적용할 대상을 선택하고 **추가,** 완료 및 다음을 **선택합니다.**
1. 문서 및 전자 메일에 대한 기본 레이블을 원하는 경우 드롭다운 목록에서 원하는 레이블을 선택합니다. 나머지 설정을 검토하고 필요한 경우 조정한 후 다음을 **선택합니다.**
1. 정책의 **이름** 및 **설명을** 입력합니다. **다음** 을 선택합니다.
1. 설정을 검토한 다음 게시를 **선택합니다.**

레이블이 작동하려면 각 사용자가 Azure Information Protection 통합 레이블 클라이언트를 다운로드해야 합니다. 웹에서AzinfoProtection_UL.exe **** 검색한 다음 Microsoft 다운로드 센터에서 다운로드하여 사용자 컴퓨터에서 실행합니다.

다음에 Word와 같은 Office 앱을 열면 생성된 민감도 레이블이 표시됩니다. 레이블을 변경하거나 적용하려면 민감도를 선택하고 레이블을 선택합니다.

