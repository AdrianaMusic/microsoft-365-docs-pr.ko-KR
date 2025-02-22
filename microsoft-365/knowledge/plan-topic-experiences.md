---
title: Microsoft 365의 항목 환경 계획
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Microsoft 365에서 항목 환경을 계획하는 방법 학습
ms.openlocfilehash: 153937cf6bc4a12f0a27866204b2286c343ddf55
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49668228"
---
# <a name="plan-topic-experiences-in-microsoft-365"></a>Microsoft 365의 항목 환경 계획

조직에서 주제가 어떻게 경험하는지 제어할 수 있습니다. 항목 환경의 계획 결정에 따라 사용자에게 고품질 주제가 표시될 수 있으며 사용자에게 지식을 소비하고 기여할 수 있는 올바른 권한이 부여됩니다.

이 문서에서는 이러한 계획 결정을 검토합니다.

- 항목에 대해 크롤링할 SharePoint 사이트
- 항목 환경에서 제외하려는 항목(있는 경우)
- 항목을 표시하려는 사용자
- 항목 센터에서 항목을 관리할 수 있는 권한을 부여하려는 사용자
- 항목 센터에서 항목을 만들거나 편집할 수 있는 권한을 부여하려는 사용자
- 항목 센터에 지정하려는 이름입니다.

데이터의 보안 및 개인 정보는 준수하며 항목 환경은 사용자에게 권한이 없는 파일에 대한 추가 액세스 권한을 부여하지 않습니다. 또한 계획 프로세스의 일부로 [항목](topic-experiences-security-privacy.md) 환경 보안 및 개인 정보 보호를 읽는 것이 좋습니다.

## <a name="requirements"></a>요구 사항

Microsoft 365 관리 센터에 액세스하고 항목 환경을 설정하려면 전역 관리자 또는 SharePoint 관리자 되어야 합니다.

항목 환경을 사용하려면 모든 사용자에게 항목 환경 **라이선스가** 필요합니다. 라이선스 할당은 항목 설정 [환경에서 다를 수 있습니다.](set-up-topic-experiences.md)

## <a name="topic-discovery"></a>항목 검색

항목 검색 설정은 항목의 원본으로 사용되는 SharePoint 사이트를 지정합니다. 모든 SharePoint 사이트, 특정 사이트 목록 또는 사이트를 포함하지하도록 선택할 수 있습니다. 항목 환경이 사용자에게 좋은 많은 항목을 검색할 수 있도록 모든 사이트를 선택하는 것이 좋습니다.

항목 환경을 설정할 때 다음 옵션 중 선택할 수 있습니다.

- **모든 사이트**: 조직의 모든 SharePoint 사이트 여기에는 현재 및 향후 사이트가 포함됩니다.
- **선택한 사이트를 제외한** 모든 사이트: 지정한 사이트를 제외한 모든 사이트 앞으로 만든 사이트는 항목 검색을 위한 원본으로 포함됩니다. 
- **선택한 사이트만**: 지정한 사이트만 앞으로 만든 사이트는 항목 검색을 위한 원본으로 포함되지 않습니다.
- **사이트 없음**: SharePoint 사이트를 포함하지 않습니다.

선택한 사이트 또는  선택한 사이트만 제외한 모두를 선택하는 경우 사이트 목록이 있는 .csv 파일을 업로드할 수 있습니다. 이러한 옵션은 파일럿을 수행 중일 때 시작할 사이트 수를 제한적으로 포함하려는 경우 유용합니다.

아래에서 .csv 템플릿을 복사할 수 있습니다.

``` csv
Site name,URL
```

항목을 자동으로 **만들거나** 업데이트하지 못하게 하여 사이트를 선택하지 않는 것이 좋습니다. 그러나 항목 환경을 설정한 다음 나중에 사이트를 추가하려는 경우 이 옵션을 선택할 수 있습니다.

조직에서 필요한 경우 항목 검색에서 개별 사이트를 제거해 보거나 사용자 또는 기술 관리자를 위한 프로세스를 만드는 것이 좋습니다.

## <a name="user-permissions"></a>사용자 권한

지정하는 사용자 권한에 따라 조직의 사용자가 항목과 상호 작용하는 사용자와 사용자가 할 수 있는 작업을 결정할 수 있습니다.

*항목 관리*

지식 관리자는 정보의 품질, 정보의 구조화 방법 및 조직의 기타 모범 사례를 감독합니다. 항목을 확인하고 거부할 수 있습니다.

개별 항목 관리자를 지정할 수 있는 반면, 지식 관리자로 지정할 사용자가 포함된 보안 그룹을 만들거나 기존 항목을 사용하는 것이 좋습니다. 설치 프로세스 중에 이 보안 그룹을 지정할 수 있습니다.

*항목 만들기 및 편집*

주제 참가자는 조직의 챔피언이자 주제 전문가입니다. 항목을 만들고 편집할 수 있습니다. 

모든 사용자가 정보를 공유할 수 있는 경우 항목 환경이 가장 잘 작동하기 때문에 조직의 모든 사용자가 항목을 만들고 편집할 수 있도록 하는 것이 좋습니다.

항목을 만들고 편집하는 항목을 특정 사용자나 그룹으로 제한하려면 해당 사용자에 대한 보안 그룹을 만들고 설치 프로세스 중에 지정합니다.

누구나 항목에 참여할 수 있도록 허용하지 않을 수 있습니다. 그러나 이는 권장되지 않습니다. 지식 관리자는 항목을 편집하고 만들 수 있습니다.

*주제 뷰어*

항목 뷰어는 SharePoint 페이지와 같은 콘텐츠에서 항목을 강조 표시하는 경우, 검색 결과 및 항목 페이지에 대한 정보를 볼 수 있습니다. 사용자는 항목에서 검색된 파일 및 페이지에 액세스할 수 있는 경우 검색된 항목만 볼 수 있습니다.

항목 뷰어를 설정할 때 다음 중 선택할 수 있습니다.

- **조직의 모든 사용자**
- **선택한 사용자 또는 보안 그룹만**
- **아무도 없어**

조직의 모든 **사용자가** 권장되지만 파일럿을 수행하고 있는 경우 선택한 사람 또는 보안 그룹만 선택할 수 있습니다. 항목 환경을  설정하려는 경우 아무도 선택하지 않지만 사용자가 아직 항목을 볼 수 있도록 허용하지 않을 수 있습니다. (지식 관리자는 여전히 주제를 보고 항목 환경을 광범위하게 사용할 수 있도록 하는 결정을 내리는 데 도움을 줄 수 있는 액세스 권한이 있습니다.)

## <a name="knowledge-rules"></a>지식 규칙

관리자는 항목 환경에서 특정 항목을 제외할 수 있습니다. 이 기능은 중요한 데이터가 항목에 나타나지 못하게 하려는 경우 유용합니다. 지식 관리자는 항목 센터에서 항목을 제외할 수 있는 반면, 관리자가 제외한 항목은 지식 관리자에게도 표시되지 않습니다. (지식 관리자는 검색 후 항목 센터에서 항목을 제거할 수 있습니다.)

관리자 수준에서 항목을 제외하려면 .csv 파일에 항목을 추가하고 파일을 업로드해야 합니다. 설치하는 동안 또는 나중에 이 작업을 할 수 있습니다.

.csv 파일에는 다음 매개 변수가 포함되어야 합니다.

- **이름:** 제외할 항목의 이름을 입력합니다. 이 작업은 다음 두 가지 방법으로 수행할 수 있습니다.
- **MatchType-Exact/Partial**: 입력한 이름이 정확히 일치하는 형식인지 부분 일치 *형식인지* *여부를* 입력합니다.
    - 정확한 일치: 정확한 이름이나 약어(예: *Contoso* 또는 ATL)를 포함할 *수 있습니다.*
    - 부분 일치: 특정 단어가 있는 모든 항목을 제외할 수 있습니다.  예를 들어 *호는* 호 원, 마주치기 또는 교육 호와 같이 단어 호가 있는 모든 항목을 *제외합니다.*  아키텍처와 같이 텍스트가 단어의 일부로 포함된 항목은 제외하지 *않습니다.*
- **약어(선택 사항)**: (확장라고도 *합니다.)* 약어를 제외하려는 경우 약어가 서 있는 단어를 입력합니다.

    ![CSV 템플릿의 항목 제외](../media/exclude-topics-csv.png) 

아래 csv 템플릿을 복사할 수 있습니다.

``` csv
Name (required),Expansion,MatchType- Exact/Partial (required)
```

## <a name="administration"></a>관리

항목 환경을 설정할 때 설치 프로세스의 일부로 항목 센터가 자동으로 만들어집니다. 항목 센터의 이름을 지정하려는 항목과 URL의 이름을 지정하려는 항목을 생각해 보아야 합니다. 설치 프로세스의 일부로 이름과 URL을 설정할 수 있으며, 나중에 Microsoft 365 관리 센터에서 이름을 변경할 수 있지만 URL은 변경할 수 없습니다. 하나의 항목 센터만 사용할 수 있습니다.

## <a name="setup-checklist"></a>설치 검사 목록

항목 환경을 설정할 때 설치 마법사를 진행할 때 다음 항목이 필요합니다.

> [!div class="checklist"]
> * 항목 검색에 대한 모든 사이트를 포함하지 않는 경우 포함하거나 제외할 사이트 목록
> * 모든 사용자가 항목을 볼 수 있도록 허용하지 않는 경우 항목을 보는 사용자의 보안 그룹
> * 모든 사용자가 항목을 만들고 편집할 수 있도록 허용하지 않는 경우 항목 참가자에 대한 보안 그룹
> * 모든 사용자가 항목을 관리할 수 있도록 허용하지 않는 경우 항목 지식 관리자를 위한 보안 그룹
> * 항목 검색에서 제외할 중요한 항목 목록
> * 항목 센터 사이트의 이름

## <a name="see-also"></a>참고 항목

[항목 환경 설정](set-up-topic-experiences.md)

[Microsoft 365에서 항목 검색 관리](topic-experiences-discovery.md)

[Microsoft 365에서 항목 표시 관리](topic-experiences-knowledge-rules.md)

[Microsoft 365에서 항목 사용 권한 관리](topic-experiences-user-permissions.md)

[Microsoft 365에서 항목 센터의 이름 변경](topic-experiences-administration.md)
