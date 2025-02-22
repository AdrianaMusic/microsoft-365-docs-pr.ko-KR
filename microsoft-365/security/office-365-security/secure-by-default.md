---
title: Office 365에서 기본적으로 보안
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: EOP(Exchange Online Protection)의 보안 기본 설정에 대해 자세히 알아보시고
ms.openlocfilehash: 758d2169d80630a38c0b498e8c1848568e5ec941
ms.sourcegitcommit: 1beaf89d2faa32f11fe1613be2fa2b31c4bc4a91
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "49602044"
---
# <a name="secure-by-default-in-office-365"></a>Office 365에서 기본적으로 보안

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

"기본적으로 보안"은 가능한 한 가장 안전한 기본 설정을 정의하는 데 사용되는 용어입니다.

그러나 보안은 생산성과 균형을 유지해야 합니다. 여기에는 다음에 대한 균형 조정이 포함됩니다.

- **사용 가능성:** 설정이 사용자 생산성에 영향을 주면 안 됩니다.
- **위험**: 보안이 중요한 활동을 차단할 수 있습니다.
- **레거시 설정:** 새로운 최신 설정이 개선된 경우에도 비즈니스상의 이유로 이전 제품 및 기능에 대한 일부 구성을 유지 관리해야 할 수 있습니다.

Exchange Online에 사서함이 있는 Microsoft 365 조직은 EOP(Exchange Online Protection)를 통해 보호됩니다. 이 보호에는 다음이 포함됩니다.

- 의심되는 맬웨어가 있는 전자 메일은 자동으로 차단되고 받는 사람에게 알림이 발송됩니다. [EOP에서 맬웨어 방지 정책 구성을 참조합니다.](configure-anti-malware-policies.md)
- 높은 신뢰도 피싱으로 식별된 전자 메일은 스팸 방지 정책 조치에 따라 처리됩니다. [EOP에서 스팸 방지 정책 구성을 참조합니다.](configure-your-spam-filter-policies.md)

EOP에 대한 자세한 내용은 [Exchange Online Protection 개요를 참조하세요.](exchange-online-protection-overview.md)

Microsoft는 기본적으로 고객의 보안을 유지하기를 원하기 때문에 일부 테넌트는 맬웨어 또는 높은 신뢰도 피싱에 적용되지 않습니다. 이러한 오버라이드에는 다음이 포함됩니다.

- 허용된 보낸 사람 목록 또는 허용된 도메인 목록(스팸 방지 정책)
- Outlook 수신이 안전한 보낸 사람
- IP 허용 목록(연결 필터링)

이러한 overrides에 대한 자세한 내용은 수신이 가능한 보낸 사람 목록 [만들기에서 찾을 수 있습니다.](create-safe-sender-lists-in-office-365.md)

기본적으로 보안은 켜거나 끄는 설정이 아니며, 위험할 수 있는 메시지나 원치 않는 메시지를 사서함 밖으로 유지하기 위해 필터링이 기본적으로 작동하는 방식입니다. 맬웨어 및 높은 신뢰도의 피싱 메시지는 차단해야 합니다. 관리자만 맬웨어 또는 높은 신뢰도 피싱으로 탐지된 메시지를 관리할 수 있으며, 가음성도 Microsoft에 보고할 수 있습니다. 자세한 내용은 EOP에서 관리자로 [quarantined messages and files as an admin(EOP에서](manage-quarantined-messages-and-files.md) 관리자로 전송된 메시지 및 파일 관리)을 참조하세요.

## <a name="more-on-why-were-doing-this"></a>이 작업을 수행하고 있는 이유에 대한 추가

기본적으로 보안이 유지되는 것은 허용이 있었어도 악의적인 메시지를 차단할 경우 취할 수 있는 동일한 조치를 취하고 있습니다. 이 방법은 맬웨어에 사용한 방법과 동일하며, 이제 이 동작을 높은 신뢰도의 피싱 메시지로 확장하고 있습니다. 이 데이터는 높은 신뢰도 피싱 메시지에 대한 가긍성 비율이 매우 낮고 관리자가 관리자 제출을 통해 가음성 문제를 해결할 수 있다는 것입니다. 또한 이 데이터에서는 스팸 방지 정책 및 Outlook의 수신 허용 도메인 목록 및 허용된 도메인 목록이 너무 광범위하여 양호한 것보다 더 많은 해를 줄 수 있는 것으로 나타납니다.

이를 또 다른 방법으로 말하기 위해, 보안 서비스로, 사용자가 손상되지 않도록 사용자를 대신하여 행동하고 있습니다. 또한 기본적으로 보안은 스팸 방지 정책에서 높은 신뢰도의 피싱 메시지에 대해 사용 가능한 옵션을 완전하게 받아들이지 않습니다. 항상 사용 가능한 다른 작업을 계속 사용할 수 있습니다(정크 메일 폴더로 이동 또는 전자 메일 주소로 리디렉션).

## <a name="exceptions"></a>예외

높은 신뢰도의 피싱 메시지가 필터링을 무시할 수 있는 유일한 무시는 Exchange 메일 흐름 규칙(전송 규칙라고도 합니다.)입니다. 메일 흐름 규칙을 사용하여 필터링을 무시하는 경우 메일 흐름 규칙을 사용하여 [메시지에 SCL을 설정하십시오.](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)

다음과 같은 시나리오에서만 오버라이드를 사용하는 것이 좋습니다.

- 피싱 시뮬레이션: 시뮬레이션된 공격은 실제 공격이 조직에 영향을 미치기 전에 취약한 사용자를 식별하는 데 도움이 될 수 있습니다.
- Security/SecOps 사서함: 보안 팀에서 필터되지 않은 메시지를 받는 데 사용하는 전용 사서함(좋음 및 불량) 그러면 Teams에서 검토하여 악성 콘텐츠가 포함되어 있는지 검토할 수 있습니다.
- 타사 필터: 타사 필터가 메일 필터링을 관리하기에 일부 타사 공급업체에서는 EOP(SCL=-1)를 해제하는 것이 좋습니다. Microsoft Defender for [Office 365에](office-365-atp.md)EOP가 필요하기에 EOP를 끄는 것은 권장되지 않습니다. 대신 커넥터에 대한 향상된 필터링을 켜는 [것이 좋습니다.](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)
- 가양성: 관리자 제출을 통해 Microsoft에서 여전히 분석하고 있는 특정 메시지를 일시적으로 [허용할 수 있습니다.](admin-submission.md) 모든 재지정과 함께 임시로 지정하는 것이 좋습니다.
