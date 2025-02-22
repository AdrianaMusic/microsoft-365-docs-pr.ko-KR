---
title: 일반적인 Microsoft 365 Defender REST API 오류 코드
description: 일반적인 Microsoft 365 Defender REST API 오류 코드에 대해 자세히
keywords: api, 오류, 코드, 일반적인 오류, mtp, api 오류 코드
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
ms.openlocfilehash: 0df741efb7555d587a6033acc23716e93f542d5e
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719217"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>일반적인 Microsoft 365 Defender REST API 오류 코드

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**적용 대상:**

- Microsoft 위협 방지

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.

오류 코드는 Microsoft 365 Defender API에 대한 작업으로 반환될 수 있습니다. 모든 오류 응답에는 문제 해결에 도움이 될 수 있는 오류 메시지가 포함되어 있습니다. 표 섹션의 오류 메시지 열에는 몇 가지 예제 메시지가 표시됩니다. 실제 메시지의 내용은 응답을 트리거한 요인에 따라 달라집니다. 가변 콘텐츠는 표에 앵글 괄호로 표시됩니다.

## <a name="error-codes"></a>오류 코드

오류 코드 | HTTP 상태 코드 | 메시지
-|-|-
BadRequest | BadRequest (400) | 일반 잘못된 요청 오류 메시지입니다.
ODataError | BadRequest (400) | 잘못된 OData URI \<the specific error is specified\> 쿼리입니다.
InvalidInput | BadRequest (400) | 입력이 \<the invalid input\> 잘못되었습니다.
InvalidRequestBody | BadRequest (400) | 요청 본문이 잘못되었습니다.
InvalidHashValue | BadRequest (400) | 해시 값이 \<the invalid hash\> 잘못되었습니다.
InvalidDomainName | BadRequest (400) | 도메인 이름이 \<the invalid domain\> 잘못되었습니다.
InvalidIpAddress | BadRequest (400) | IP \<the invalid IP\> 주소가 잘못되었습니다.
InvalidUrl | BadRequest (400) | URL이 \<the invalid URL\> 잘못되었습니다.
MaximumBatchSizeExceeded | BadRequest (400) | 최대 일괄 처리 크기가 초과됩니다. Received: \<batch size received\> , allowed: {batch size allowed}.
MissingRequiredParameter | BadRequest (400) | 매개 \<the missing parameter\> 변수가 없습니다.
OsPlatformNotSupported | BadRequest (400) | 이 \<the client OS Platform\> 작업에서 OS 플랫폼이 지원되지 않습니다.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> 는 클라이언트 버전 \<supported client version\> 이상에서 지원됩니다.
권한이 없는 경우 | 권한이 없는 경우(401) | 권한이 없는 경우 <br /><br />*참고: 일반적으로 유효하지 않은 또는 만료된 권한 부여 헤더로 인해 발생했습니다.*
금지 | 금지(403) | 금지 <br /><br />*참고: 유효한 토큰이지만* 작업 권한이 없습니다.
DisabledFeature | 금지(403) | 테넌트 기능을 사용할 수 없습니다.
DisallowedOperation | 금지(403) | \<the disallowed operation and the reason\>.
NotFound | 찾을 수 없습니다(404) | 일반 찾을 수 없는 오류 메시지입니다.
ResourceNotFound | 찾을 수 없습니다(404) | 리소스를 \<the requested resource\> 찾을 수 없습니다.
InternalServerError | 내부 서버 오류(500) | *참고: 오류 메시지가 없는 경우 작업을 다시 시도하거나 해결되지 않은 경우 Microsoft에 문의하십시오.*

## <a name="examples"></a>예

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>본문 매개 변수

> [!IMPORTANT]
> 본문 매개 변수는 대소문자 구분입니다.

*InvalidRequestBody* 또는 *MissingRequiredParameter* 오류가 발생하는 경우 오타로 인해 발생할 수 있습니다. API 설명서를 검토하고 제출된 매개 변수가 관련 예제와 일치하는지 검토합니다.

## <a name="tracking-id"></a>추적 ID

각 오류 응답에는 추적을 위한 고유한 ID 매개 변수가 포함되어 있습니다. 이 매개 변수의 속성 이름은 *target입니다.* 오류에 대해 문의할 때 이 ID를 첨부하면 문제의 근본 원인을 찾는 데 도움이 됩니다.

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 개요](api-overview.md)
- [지원되는 Microsoft 365 Defender API](api-supported.md)
- [Microsoft 365 Defender API 액세스](api-access.md)
- [API 제한 및 라이선싱에 대해 자세히](api-terms.md)
