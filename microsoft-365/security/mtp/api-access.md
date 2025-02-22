---
title: Microsoft 365 Defender API 액세스
description: Microsoft 365 Defender API에 액세스하는 방법에 대해 자세히 알아보기
keywords: 액세스, api, 응용 프로그램 컨텍스트, 사용자 컨텍스트, aad 응용 프로그램, 액세스 토큰
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
ms.openlocfilehash: 5e01aaf2ee9255fd909b26278346fd4ccf54729a
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719241"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Microsoft 365 Defender API 액세스

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**적용 대상:**

- Microsoft 365 Defender

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft 365 Defender는 프로그래밍 API 집합을 통해 많은 데이터 및 작업을 노출합니다. 이러한 API는 워크플로를 자동화하고 Microsoft 365 Defender의 기능을 완전히 활용하는 데 도움이 됩니다.

일반적으로 API를 사용하려면 다음 단계를 수행해야 합니다.

- Azure Active Directory 응용 프로그램 만들기
- 이 응용 프로그램을 사용하여 액세스 토큰 얻기
- 토큰을 사용하여 Microsoft 365 Defender API 액세스

> [!NOTE]
> API 액세스에는 OAuth2.0 인증이 필요합니다. 자세한 내용은 [OAuth 2.0 권한 부여 코드 흐름을 참조하세요.](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)

이러한 단계를 완료하면 특정 컨텍스트를 사용하여 Microsoft 365 Defender API에 액세스할 수 있습니다.

## <a name="application-context-recommended"></a>응용 프로그램 컨텍스트(권장)

백그라운드 서비스 또는 데몬과 같이 로그인한 사용자가 없는 실행된 앱에 대해 이 컨텍스트를 사용하세요.

1. Azure Active Directory 웹 응용 프로그램을 만드십시오.
2. 원하는 사용 권한을 응용 프로그램에 할당합니다.
3. 응용 프로그램의 키를 만드시다.
4. 응용 프로그램 및 해당 키를 사용하여 보안 토큰을 얻습니다.
5. 토큰을 사용하여 Microsoft 365 Defender API에 액세스합니다.

자세한 내용은 사용자 없이 **[Microsoft 365 Defender에 액세스하는 앱 만들기를 참조하세요.](api-create-app-web.md)**

## <a name="user-context"></a>사용자 컨텍스트

이 컨텍스트를 사용하여 단일 사용자를 대신하여 작업을 수행할 수 있습니다.

1. Azure Active Directory 기본 응용 프로그램을 만드십시오.
2. 원하는 권한을 응용 프로그램에 할당합니다.
3. 응용 프로그램의 사용자 자격 증명을 사용하여 보안 토큰을 얻습니다.
4. 토큰을 사용하여 Microsoft 365 Defender API에 액세스합니다.

자세한 내용은 사용자를 대신하여 **[Microsoft 365 Defender API에](api-create-app-user-context.md)** 액세스하는 앱 만들기를 참조하세요.

## <a name="partner-context"></a>파트너 컨텍스트

여러 테넌트에서 많은 사용자에게 앱을 제공해야 하는 경우 이 [컨텍스트를 사용하세요.](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

1. Azure Active Directory 다중 테넌트 응용 프로그램을 만드십시오.
2. 원하는 권한을 응용 프로그램에 할당합니다.
3. 각 [테넌트에서](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) 앱에 대한 관리자 동의를 얻습니다.
4. 고객의 테넌트 ID에 따라 사용자 자격 증명을 사용하여 보안 토큰을 얻습니다.
5. 토큰을 사용하여 Microsoft 365 Defender API에 액세스합니다.

자세한 내용은 **[파트너가 Microsoft 365 Defender API에](api-partner-access.md)** 액세스할 수 있는 앱 만들기를 참조하세요.

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 개요](api-overview.md)
- [사용자 로그인 및 API 액세스에 대한 OAuth 2.0 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Azure Key Vault를 사용하여 서버 앱의 비밀 관리](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/)
- [Microsoft 365 API에 액세스하는 'Hello world' 응용 프로그램 만들기](api-hello-world.md)
