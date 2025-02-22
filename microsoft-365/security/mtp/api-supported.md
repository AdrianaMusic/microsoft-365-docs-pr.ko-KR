---
title: 지원되는 Microsoft 365 Defender API
description: 지원되는 Microsoft 365 Defender API
keywords: MTP, API, api
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
ms.openlocfilehash: dbb7613dae3755b0fb794a3d68b5b424d765cc62
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719325"
---
# <a name="supported-microsoft-365-defender-apis"></a>지원되는 Microsoft 365 Defender API 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**적용 대상:**
- Microsoft 365 Defender

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="list-of-available-apis"></a>사용 가능한 API 목록

문서 | 설명
-|-
[고급 헌팅 API](api-advanced-hunting.md) | 고급 헌팅 쿼리를 실행합니다.
[인시던트 API](api-incident.md) | 다른 실용적인 작업과 함께 인시던트 나열 및 업데이트

### <a name="endpoint-uris"></a>끝점 URIS

두 기본 API 모두에 대한 기본 URI는 . https://api.security.microsoft.com 성능을 향상하기 위해 지리적 위치와 더 가까운 서버를 사용하십시오.

- 미국: api-us.security.microsoft.com
- 유럽: api-eu.security.microsoft.com
- 영국: api-uk.security.microsoft.com

토큰은 액세스하여 획득할 수 https://api.security.microsoft.com 있습니다.

경로의 모든 `/api` API는 [OData](https://docs.microsoft.com/odata/overview) 프로토콜을 https://api.security.microsoft.com/api/incidents 사용합니다(예: .

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 개요](api-overview.md)
- [Microsoft Threat Protection API 액세스](api-access.md)
- [API 제한 및 라이선싱에 대해 자세히](api-terms.md)
- [오류 코드 이해](api-error-codes.md)
