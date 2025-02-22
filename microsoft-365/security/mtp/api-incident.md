---
title: Microsoft 365 Defender 인시던트 API 및 인시던트 리소스 유형
description: Microsoft 365 Defender의 인시던트 리소스 유형의 방법 및 속성에 대해 자세히 알아보기
keywords: 인시던트, 인시던트, api
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
ms.openlocfilehash: 372c939f5eed29832725e6b048735040ca7391d6
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719337"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incident-resource-type"></a>Microsoft 365 Defender 인시던트 API 및 인시던트 리소스 유형

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**적용 대상:**

- Microsoft 365 Defender

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.

인시던트는 공격을 설명하는 데 도움이 되는 관련 경고 모음입니다. [](incidents-overview.md) 조직의 여러 엔터티의 이벤트는 Microsoft 365 Defender에 의해 자동으로 집계됩니다. 인시던트 API를 사용하여 프로그래밍하여 조직의 인시던트 및 관련 경고에 액세스할 수 있습니다.

## <a name="quotas-and-resource-allocation"></a>할당량 및 리소스 할당

분당 최대 50통 또는 시간당 1500통의 통화를 요청할 수 있습니다. 각 메서드에는 자체 할당량도 있습니다. 메서드별 할당량에 대한 자세한 내용은 사용할 메서드에 대한 각 문서를 참조하십시오.

HTTP 응답 코드는 전송된 요청 수 또는 할당된 실행 시간으로 할당량에 도달했다는 `429` 메시지를 나타냅니다. 응답 본문에는 도달한 할당량 설정이 다시 설정될 때까지의 시간이 포함됩니다.

## <a name="permissions"></a>권한

인시던트 API에는 각 메서드에 대해 서로 다른 종류의 사용 권한이 필요합니다. 필요한 사용 권한에 대한 자세한 내용은 해당 방법의 문서를 참조하세요.

## <a name="methods"></a>메서드

메서드 | 반환 형식 | 설명
-|-|-
[인시던트 열거](api-list-incidents.md) | [인시던트](api-incident.md) 목록 | 인시던트 목록을 얻습니다.
[인시던트 업데이트](api-update-incidents.md) | [인시던트](api-incident.md) | 특정 인시던트 업데이트

## <a name="request-body-response-and-examples"></a>요청 본문, 응답 및 예제

요청을 생성하거나 응답을 구문 분석하는 방법에 대한 자세한 내용과 실제 예제는 각 메서드 문서를 참조합니다.

## <a name="common-properties"></a>일반 속성

속성 | 유형 | 설명
-|-|-
incidentId | long | 인시던트 고유 ID입니다.
redirectIncidentId | nullable long | 현재 인시던트가 병합된 인시던트 ID입니다.
incidentName | 문자열 | 인시던트의 이름입니다.
createdTime | DateTimeOffset | 인시던트가 만들어진 날짜 및 시간(UTC)입니다.
lastUpdateTime | DateTimeOffset | 인시던트가 마지막으로 업데이트된 날짜 및 시간(UTC)입니다.
assignedTo | 문자열 | 인시던트의 소유자입니다.
심각도 | Enum | 인시던트의 심각도입니다. 가능한 값은 ```UnSpecified``` , ```Informational``` , , 및 ```Low``` ```Medium``` ```High``` .
status | Enum | 인시던트의 현재 상태를 지정합니다. 가능한 값은 ```Active``` , ```Resolved``` 및 ```Redirected``` .
classification | Enum | 인시던트 사양입니다. 가능한 값은 ```Unknown``` ```FalsePositive``` , , ```TruePositive``` .
determination | Enum | 인시던트의 결정 가능한 값은 ```NotAvailable``` ```Apt``` , ```Malware``` ```SecurityPersonnel``` ```SecurityTesting``` ```UnwantedSoftware``` ```Other``` 입니다.
tags | string List | 인시던트 태그 목록입니다.
alerts | 경고 목록 | 관련 경고 목록입니다. 목록 인시던트 API [설명서에서 예제를](api-list-incidents.md) 참조하세요.

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 개요](api-overview.md)
- [인시던트 개요](incidents-overview.md)
- [인시던트 목록 API](api-list-incidents.md)
- [인시던트 업데이트 API](api-update-incidents.md)
