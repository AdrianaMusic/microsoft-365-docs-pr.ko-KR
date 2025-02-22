---
title: Office 365용 Microsoft Defender 평가
description: 평가 모드에서 Office 365용 Defender는 맬웨어와 같은 판정을 기록하지만 메시지에 대해 활동하지 않는 Office 365 전자 메일 정책에 대한 Defender를 만듭니다.
keywords: Office 365 평가, Office 365용 Microsoft Defender, Office 365 평가, Office 365, Microsoft Defender, ATP 평가
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: abb33b85717e63cb78a2b1edfd86584fd165a71f
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49701018"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Office 365용 Microsoft Defender 평가

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Office 365용 Microsoft Defender 평가는 곧 공개 미리 보기로 제공됩니다. 이 미리 보기 버전은 서비스 수준 계약 없이 제공됩니다. 일부 기능은 지원되지 않을 수도, 기능이 제한될 수도 있습니다.

포괄적인 보안 제품 평가를 수행하면 업그레이드 및 구매에 대한 정보를 제공한 결정을 내리는 데 도움이 될 수 있습니다. 보안 제품의 기능을 사용하여 보안 운영 팀이 일상적인 작업에서 어떻게 도움이 될 수 있는지 평가하는 데 도움이 됩니다.

[Office 365용 Microsoft Defender](office-365-atp.md) 평가 환경은 보안 솔루션의 기능을 평가하는 데 집중할 수 있도록 장치 및 환경 구성의 복잡한 문제를 제거하도록 설계되었습니다. SharePoint, Office 클라이언트 또는 Teams가 아닌 전자 메일 보호에만 적용됩니다.

Office 365용 Microsoft Defender를 지원하는 라이선스가 아직 없는 경우 [무료 30일](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) 평가를 시작하고 Office 365 보안 및 준수 센터에서 기능을 & 수 있습니다. https://protection.office.com/homepage) 빠른 설치를 즐길 수 있으며 필요한 경우 쉽게 해제할 수 있습니다.

## <a name="how-the-evaluation-works"></a>평가 작동 방식

평가 모드에서 Office 365용 Defender는 맬웨어와 같은 판정을 기록하지만 메시지에 대해 활동하지 않는 Office 365 전자 메일 정책에 대한 Defender를 만듭니다. MX 레코드 구성을 변경할 필요는 없습니다.

평가 [모드에서는](atp-safe-attachments.md)안전 첨부 파일, [](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)  [안전한](atp-safe-links.md)링크 및 피싱 방지 가장 정책이 사용자 대신 설정됩니다. Office 365용 모든 Defender 정책은 백그라운드에서 적용되지 않은 모드로 만들어지며 표시되지 않습니다.

또한 설치의 일부로 평가 모드는 커넥터에 대한 향상된 [필터링을 구성합니다.](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) IP 주소 및 보낸 사람 정보를 보존하여 필터링 정확도를 향상시킵니다. 이 정보는 메일이 Office 365용 Defender 앞에 있는 ESG(전자 메일 보안 게이트웨이)를 통과할 때 손실됩니다. 향상된 필터링은 EOP(Exchange Online Protection) 스팸 방지 및 피싱 방지 정책에 대한 필터링 정확도도 향상시킵니다.

일부 미지원 시나리오에 대한 잠재적인 프로덕션 영향을 최소화하기 위해 SCL(스팸 지수)을 -1로 설정하는 전송 규칙을 만들어 모든 EOP 필터링을 무시할 수 있습니다. 자세한 [내용은 EAC를 사용하여 메시지의 SCL을](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message)설정하는 메일 흐름   규칙을 만들 수 있습니다.

평가 모드가 설정되면 정책이 구현된 경우 차단될 메시지를 수량화하는 최대 90일의 데이터로 매일 보고서가 업데이트됩니다(예: 삭제, 정크 메일로 보내기, 정크 메일로 보내기, 정크 메일 보내기). Office 365 및 EOP 검색에 대한 모든 Defender에 대한 보고서가 생성됩니다. 검색 기술(예: 가장)별로 집계되어 시간 범위별로 필터링할 수 있습니다. 또한 주문형 메시지 보고서를 만들어 사용자 지정 피벗을 만들거나 위협 탐색기를 사용하여 심층 분석 메시지를 만들 수 있습니다.

간소화된 설정 환경을 통해 다음에 집중할 수 있습니다.

- 평가 실행
- 자세한 보고서 확인
- 보고서에서 작업 분석
- 평가 결과 발표

## <a name="before-you-begin"></a>시작하기 전에

### <a name="licensing"></a>라이선싱

평가에 액세스하려면 라이선스 요구 사항을 충족해야 합니다. 다음 라이선스 중 한 개가 작동됩니다.

- Office 365용 Microsoft Defender 플랜 1
- Office 365용 Microsoft Defender 플랜 2
- Microsoft 365 E5, Microsoft 365 E5 보안
- Office 365 E5

이러한 라이선스 중 하나만 있는 경우 평가판 라이선스를 얻어야 합니다.

#### <a name="trial"></a>평가판

Office 365용 Microsoft Defender에 대한 평가판 라이선스를  얻습니다. 대금 청구 관리자 역할 또는 전역 관리자 **역할이 필요합니다.** 전역 관리자 역할이 있는 사용자로부터 사용 권한을 요청합니다. [구독 및 라이선스에 대해 자세히](https://docs.microsoft.com/microsoft-365/commerce/licenses/subscriptions-and-licenses)

적절한 역할이 있는 경우 Microsoft 365 관리 센터에서 청구 서비스 구매 서비스로 > Microsoft Defender for Office 365(계획 2)에 대한 평가판 라이선스를 얻는 것이 좋습니다. 평가판에는 25개 라이선스에 대한 30일 무료 평가판이 포함되어 있습니다. [Office 365용 Microsoft Defender 평가판(계획 2)을 다운로드합니다.](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)

고급 위협을 모니터링하고 보고하는 평가가 있는 30일 기간이 있습니다. Office 365의 전체 Defender 기능을 원하는 경우 유료 구독을 구입할 수도 있습니다.

### <a name="roles"></a>역할

평가 모드에서 Office 365용 Defender를 설정하려면 Exchange Online 역할이 필요합니다.

- [Exchange Online의 사용 권한에 대해 자세히](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)
- [관리자 역할 할당에 대해 자세히](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)

다음 역할이 필요합니다.

|작업|역할|
|---|---|
|무료 평가판 다운로드 또는 Office 365용 Microsoft Defender 구입(계획 2)|청구 관리자 역할 또는 전역 관리자 역할|
|평가 정책 만들기|원격 및 허용 도메인 역할 보안 관리자 역할|
|평가 정책 편집|원격 및 허용 도메인 역할 보안 관리자 역할|
|평가 정책 삭제|원격 및 허용 도메인 역할 보안 관리자 역할 |
|평가 보고서 보기|보안 관리자 역할 또는 보안 읽기 관리자 역할|
|


### <a name="enhanced-filtering"></a>향상된 필터링

대량 및 스팸 방지와 같은 Exchange Online Protection 정책은 동일하게 유지됩니다. 메시지 배달도 동일하게 유지됩니다. 그러나 이 평가에서는 커넥터에 대한 향상된 필터링이 설정되어 우회하지 않는 한 메일 흐름 및 Exchange Online Protection 정책에 영향을 미치게 됩니다.

커넥터에 대한 향상된 필터링을 통해 테넌트는 스푸핑 방지 보호를 사용할 수 있습니다. 커넥터에 대한 향상된 필터링을 설정하지 않고도 ESG(전자 메일 보안 게이트웨이)를 사용하는 경우 스푸핑 방지가 지원되지 않습니다.

### <a name="urls"></a>URL

메일 흐름 중에 URL이 확인됩니다. 특정 URL을 검색하지 못하도록 하려는 경우 허용된 URL 목록을 적절하게 관리합니다. 자세한 [내용은 테넌트 허용/차단](tenant-allow-block-list.md) 목록에서 URL 관리를 참조하세요.

전자 메일 메시지 본문의 URL 링크는 줄 바꿈되지 않습니다. 이를 통해 고객 영향이 줄 바꿈되지 않습니다.

### <a name="email-routing"></a>전자 메일 라우팅

메일을 라우팅하는 인바운드 커넥터의 이름을 포함하여 전자 메일이 현재 라우팅되는 방법을 설정하는 데 필요한 해당 세부 정보를 준비합니다. Exchange Online Protection만 사용하는 경우 커넥터가 없습니다.  [메일 흐름 및 전자 메일 라우팅에 대해 자세히](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/mail-flow)

지원되는 전자 메일 라우팅 시나리오는 다음과 같습니다.

- 타사 파트너 **및/또는** 프레미스 서비스 공급자: 평가하려는 인바운드 커넥터는 타사 공급자를 사용하고/ 또는 전자 메일 보안에 대한 솔루션을 사용 중입니다.
- **Microsoft Exchange Online 보호만:** 평가하려는 테넌트는 전자 메일 보안에 Office 365를 사용하며 MX(메일 교환) 레코드는 Microsoft를 지날 수 있습니다.

### <a name="email-security-gateway"></a>전자 메일 보안 게이트웨이

타사 ESG(전자 메일 보안 게이트웨이)를 사용하는 경우 공급자의 이름을 알아야 합니다. ESG를 사용하는 경우 장치용 공용 IP 주소(예: ES)를 알아야 합니다.

지원되는 타사 파트너는 다음과 같습니다.

- Barracuda
- IronPort
- Mimecast
- Proofpoint
- 소포스
- Symantec
- 경향 마이크로

### <a name="scoping"></a>겹치기

평가 범위를 인바운드 커넥터로 제한할 수 있습니다. 커넥터가 구성되지 않은 경우 관리자는 평가 범위를 통해 테넌트의 모든 사용자로부터 데이터를 수집하여 Office 365용 Defender를 평가할 수 있습니다.

## <a name="get-started-with-the-evaluation"></a>평가 시작

Office 365 보안 및 준수 센터에서 Microsoft Defender for Office 365 평가판 &(다음 세 가지 액세스 https://protection.office.com/homepage) 지점에서)를 찾을 수 있습니다.

- 위협 관리 > 대시보드
- 위협 관리 > 정책
- 보고서 > 대시보드

## <a name="setting-up-the-evaluation"></a>평가 설정

평가를 위한 설정 흐름을 시작하면 두 가지 라우팅 옵션이 제공됩니다. 조직의 메일 라우팅 설정 및 평가 요구에 따라 타사 및/또는 프레미스 서비스 공급자를 사용할지 아니면 서비스 공급자만 사용하고 있는지를 선택할 수 Microsoft Exchange Online.

- 타사 파트너 및/또는 프레미스 서비스 공급자를 사용하는 경우 드롭다운 메뉴에서 공급업체의 이름을 선택해야 합니다. 다른 커넥터 관련 세부 정보를 제공합니다.

- MX 레코드가 Microsoft를 Microsoft Exchange Online Exchange Online 사서함이 있는 경우 이 옵션을 선택합니다.

설정을 검토하고 필요한 경우 편집합니다. 그런 다음 평가 **만들기를 선택합니다.** 설정이 완료된 것을 나타내는 확인 메시지가 표시됩니다.

Office 365용 Microsoft Defender 평가 보고서는 매일 한 번 생성됩니다. 데이터를 채우는 데 최대 24시간이 걸릴 수 있습니다.

### <a name="exchange-rules-optional"></a>Exchange 규칙(선택 사항)

기존 게이트웨이가 있는 경우 커넥터에 대한 향상된 필터링을 활성화하고 들어오는 보낸 사람 IP 주소를 변경하기 때문에 필터링을 무시할 수 있습니다. 우회하려면 Exchange 관리 센터로 이동하여 SCL -1의 정책을 생성합니다(아직 SCL이 없는 경우). 규칙 구성 요소 및 규칙의 작동 방식에 대한 자세한 내용은 Exchange Online의 메일 흐름 규칙(전송 규칙)을 참조하세요.

## <a name="evaluate-capabilities"></a>기능 평가

평가 보고서가 생성된 후 조직의 전자 메일 및 공동 작업 작업 공간에서 식별된 고급 위협 링크, 고급 위협 첨부 파일 및 잠재적인 가장 수를 참조하세요.

평가판이 만료되면 90일 동안 보고서에 계속 액세스할 수 있습니다. 그러나 더 이상 정보를 수집하지 않습니다. 평가판이 만료된 후 Office 365용 Microsoft Defender를 계속 사용하려면 [Office 365용 Microsoft Defender](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)유료 구독(계획 2)을 구입해야 합니다.

설정으로 **이동하여** 라우팅을 업데이트하거나 평가를 해제할 수 있습니다. 그러나 해제한 후 평가를 계속하기로 결정한 경우 동일한 설정 프로세스를 다시 진행해야 합니다.

## <a name="provide-feedback"></a>피드백 제공

사용자 의견은 고급 공격으로부터 환경을 보호하는 데 도움이 됩니다. 제품 기능 및 평가 결과에 대한 경험과 노출을 공유합니다.

의견 **제공을** 선택하여 의견을 보내주세요.
