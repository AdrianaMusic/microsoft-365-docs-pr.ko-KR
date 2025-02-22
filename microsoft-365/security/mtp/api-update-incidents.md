---
title: 인시던트 업데이트 API
description: Microsoft 365 Defender API를 사용하여 인시던트 업데이트 방법 학습
keywords: 업데이트, api, 인시던트
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 6fc1ff730994f03aa500ad9a4559b66970e32d87
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719407"
---
# <a name="update-incidents-api"></a>인시던트 업데이트 API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**적용 대상:**

- Microsoft 365 Defender

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="api-description"></a>API 설명

기존 인시던트의 속성을 업데이트합니다. 업데이트할 수 있는 속성은 ```status``` , ```determination``` 및 ```classification``` ```assignedTo``` ```tags``` .

### <a name="quotas-resource-allocation-and-other-constraints"></a>할당량, 리소스 할당 및 기타 제약 조건

1. 제한 임계값에 도달하기 전에 분당 최대 50통 또는 시간당 1500통의 통화를 만들 수 있습니다.
2. 이 속성은 `determination` `classification` TruePositive로 설정된 경우만 설정할 수 있습니다.

요청이 스로틀된 경우 응답 `429` 코드가 반환됩니다. 응답 본문은 새 통화를 시작할 수 있는 시간을 나타냅니다.

## <a name="permissions"></a>권한

이 API를 호출하려면 다음 권한 중 하나를 필요합니다. 사용 권한을 선택하는 방법을 포함하여 자세한 내용은 [Microsoft 365 Defender API](api-access.md)액세스를 참조합니다.

사용 권한 유형 | 사용 권한 | 사용 권한 표시 이름
-|-|-
응용 프로그램 | Incident.ReadWrite.All | 모든 인시던트 읽기 및 쓰기
위임(직장 또는 학교 계정) | Incident.ReadWrite | 인시던트 읽기 및 쓰기

> [!NOTE]
> 사용자 자격 증명을 사용하여 토큰을 얻을 때 사용자는 포털에서 인시던트 업데이트 권한이 필요합니다.

## <a name="http-request"></a>HTTP 요청

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>요청 헤더

이름 | 유형 | 설명
-|-|-
권한 부여 | 문자열 | Bearer {token}. **필수 .**
Content-Type | 문자열 | application/json. **필수 .**

## <a name="request-body"></a>요청 본문

요청 본문에 업데이트해야 하는 필드의 값을 제공합니다. 관련 값의 변경으로 인해 다시 계산해야 하는 경우를 위해 요청 본문에 포함되지 않은 기존 속성은 해당 값을 유지 관리합니다. 최상의 성능을 위해 변경되지 않은 기존 값을 생략해야 합니다.

속성 | 유형 | 설명
-|-|-
status | Enum | 경고의 현재 상태를 지정합니다. 가능한 값은 ```Active``` , ```Resolved``` 및 ```Redirected``` .
assignedTo | 문자열 | 인시던트의 소유자입니다.
classification | Enum | 경고 사양입니다. 가능한 값은 ```Unknown``` ```FalsePositive``` , , ```TruePositive``` .
determination | Enum | 경고 결정 가능한 값은 ```NotAvailable``` ```Apt``` , ```Malware``` ```SecurityPersonnel``` ```SecurityTesting``` ```UnwantedSoftware``` ```Other``` 입니다.
tags | string List | 인시던트 태그 목록입니다.

## <a name="response"></a>응답

성공하면 이 메서드는 `200 OK` 를 반환합니다. 응답 본문에는 업데이트된 속성이 포함된 인시던트 엔터티가 포함되어 있습니다. 지정한 ID의 인시던트가 발견되지 않으면 메서드에서 `404 Not Found` 를 반환합니다.

## <a name="example"></a>예제

**요청**

요청의 예는 다음과 같습니다.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

**응답**

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"]
}
```

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 액세스](api-access.md)
- [API 제한 및 라이선싱에 대해 자세히](api-terms.md)
- [오류 코드 이해](api-error-codes.md)
- [인시던트 API](api-incident.md)
- [인시던트 열거](api-list-incidents.md)
- [인시던트 개요](incidents-overview.md)
