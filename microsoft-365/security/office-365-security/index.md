---
title: Office 365 보안, Office 365용 Microsoft Defender, EOP, MSDO
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Office 365의 보안, EOP에서 Office 365 계획 1 및 2, Standard 및 엄격한 보안 구성 등입니다. 가지고 있는 정보 및 속성을 보호하는 방법을 이해합니다.
ms.openlocfilehash: 84d7dcfc68ce78bfde92f3d7096cd4104355ce94
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616251"
---
# <a name="office-365-security-overview"></a>Office 365 보안 개요

이 문서에서는 클라우드의 새로운 보안 속성을 소개합니다. 보안 운영 센터에 새로 추가된 보안 관리자인지 아니면 새로 고침을 시작해야 하는지 여부에 따라 시작해보아야 합니다.

> [!CAUTION]
> Outlook.com, **Microsoft 365** 패밀리 **또는** Microsoft **365 개인을** 사용 중일 때  안전한 링크 또는 안전한 첨부 파일 정보가 필요한 경우 ***** 이 링크 _: [Microsoft 365 구독자를](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2)위한 고급 Outlook.com 보안 . 

## <a name="office-365-security-spelled-out"></a>Office 365 보안 맞춤법 검사

모든 Office 365 구독에는 보안 기능이 함께 제공되어 있습니다. 수행할 수 있는 목표와 작업은 이러한 여러 구독의 포커스에 따라 다릅니다. Office 365 보안에는 구독 유형과 3가지 주요 보안 서비스(또는 제품)가 있습니다.

1. EOP(Exchange Online Protection)
1. Microsoft Defender for Office 365 요금제 1(Office P1용 Defender)
1. Microsoft Defender for Office 365 요금제 2(Defender for Office P2)

> [!NOTE]
> 구독을 구입하고 지금*에서 보안 기능을 롤아웃해야 하는 경우 _right [](protect-against-threats.md) 위협 방지 문서의 단계로 건너뛰세요. 구독을 새로 시작하고 시작하기 전에 라이선스를 알고자 하는 경우 [Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage)관리 센터에서 > 제품을 검색합니다.

Office 365 보안은 EOP에서 제공하는 핵심 보호 기능을 구축합니다. EOP는 Exchange Online 사서함을 찾을 수 있는 모든 구독에 있습니다(여기에 설명된 모든 보안 제품은 클라우드 기반임).

이러한 방식으로 설명된 세 가지 구성 요소를 보는 데 익숙할 수 있습니다.

|EOP|Office 365 P1용 Microsoft Defender|Office 365 P2용 Microsoft Defender|
|---|---|---|
|광범위하고 볼륨 기반의 알려진 공격을 방지합니다.|제로 데이 맬웨어, 피싱 및 비즈니스 전자 메일 손상으로부터 전자 메일 및 공동 작업을 보호합니다.|위반 사후 조사, 헌팅 및 대응뿐만 아니라 자동화 및 시뮬레이션(교육용)을 추가합니다.|
|

그러나 아키텍처 측면에서 각 조각을 보안이 강조된 누적 보안 계층으로 생각하는 것으로 시작해보아야 합니다. 더 많은 예:

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP 및 Office 365용 Microsoft Defender와 전자 메일 인증에 대한 참고 사항 등 서비스 강조를 통해 다른 사용자와의 관계":::

이러한 각 서비스는 보호, 감지, 조사 및 응답 중에서 목표를 강조하기는 하지만 * _**_ **all** _ 서비스는 보호, 검색, 조사 및 대응의 목표를 달성할 수 있습니다.

Office 365 보안의 핵심은 EOP 보호입니다. Office 365 P1용 Microsoft Defender에는 EOP가 포함되어 있습니다. Office 365 P2용 Defender에는 P1 및 EOP가 포함되어 있습니다. 구조체가 누적됩니다. 따라서 이 제품을 구성할 때 EOP로 시작하고 Office 365용 Defender에 대해 작업해야 합니다.

전자 메일 인증 구성은 공용 DNS에서 진행하지만 스푸핑을 방어하는 데 도움이 하도록 이 기능을 구성하는 것이 중요합니다. _EOP가 있는 경우* ***전자 메일 [인증을 구성해야 합니다.](email-validation-and-authentication.md)**_

If you have an Office 365 E3 or below, you have EOP, but with the option to buy standalone Defender for Office 365 P1 through upgrade. Office 365 E5가 있는 경우 Office 365 P2용 Defender가 이미 있습니다.

> [!TIP]
> 구독이 Office 365 E3 또는 E5가 아닐 경우 여전히 Office 365 P1용 Microsoft Defender로 업그레이드할 수 있는 옵션이 있는지 확인할 수 있습니다. 관심이 있는 경우 이 웹 [페이지는](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) Microsoft Defender for Office 365 P1 업그레이드를 사용할 수 있는 구독 목록을 제공합니다(페이지 끝에서 미세 인쇄 확인).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>EOP에서 Office 365용 Microsoft Defender로의 Office 365 보안 사다리

![EOP 및 Office 365용 Microsoft Defender 및 보안 강조, 보호 및 감지에서 조사 및 응답으로 진행 EOP에 대해 전자 메일 인증 구성(DKIM 및 DMARC 이상)을 설정해야 합니다.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> [Exchange Online Protection](exchange-online-protection-overview.md)및 Office [365용 Defender](office-365-atp.md)페이지에 대한 자세한 내용을 참조하세요.

Office 365용 Microsoft Defender 요금제 추가를 순수 EOP 위협 관리의 이점으로 만드는 것은 한눈에 알기 어려울 수 있습니다. 업그레이드 경로가 조직에 적합한지 정렬하려면 각 제품의 기능에 대해 살펴보고자 합니다.

- 위협 방지 및 감지
- 조사 중
- responding

_*Exchange Online Protection**부터 시작:
<p>

|방지/감지|조사|응답|
|---|---|---|
|기술에는 다음이 포함됩니다.<ul><li>스팸</li><li>피싱</li><li>맬웨어</li><li>대량 메일</li><li>스푸핑 인텔리전스</li><li>가장 검색</li><li>관리자 Quarantine</li><li>가짓 긍정 및 거짓 부정의 관리자 및 사용자 제출</li><li>URL 및 파일에 대한 허용/차단</li><li>보고서</li></u1>|<li>감사 로그 검색</li><li>메시지 추적</li>|<li>ZAP(제로 아워 자동 제거)</li><li>허용 및 차단 목록의 구체화 및 테스트</li>|
|

EOP로 이동하려는 경우 이 **[문서로 이동하세요.](exchange-online-protection-overview.md)**

이러한 제품은 누적적이기 때문에 Office 365 P1용 Microsoft Defender를 평가하고 구독하기로 결정하면 이러한 기능을 추가할 수 있습니다.

**Office 365용 Defender,** 계획 1(현재까지) 이득:
<p>

|방지/감지|조사|응답|
|---|---|---|
|기술에는 EOP의 모든 것을 더한 다음이 포함됩니다.<u1><li>안전한 첨부 파일</li><li>안전한 링크<li>워크로드에 대한 Microsoft Defender for Office 365 보호 기능(예: SharePoint Online, Teams, 비즈니스용 OneDrive)</li><li>전자 메일, Office 클라이언트 및 Teams에서 클릭 시 보호</li><li>Defender for Office 365의 피싱 방지</li><li>사용자 및 도메인 가장 보호</li><li>경고 및 경고에 대한 SIEM 통합 API</li>|<li>검색을 위한 SIEM 통합 API</li><li>**실시간 검색 도구**</li><li>URL 추적</li>|<li>동일</li></u1>

따라서 Office 365 P1용 Microsoft Defender는 집의 **_prevention_* _ 쪽을 확장하고 추가 형태의 검색을 _*_추가합니다._*_

Office 365 P1용 Microsoft Defender는 조사를 위해 _ *실시간* 검색 *도 추가합니다. 이 위협 헌팅 도구의 이름은 Office 365 P1용 Defender가 있다는 것을 알기 때문에 굵게 표시됩니다.  Office 365 P2용 Defender에는 나타나지 않습니다.

**Office 365용 Defender,** 계획 2(현재까지) 이득:
<p>

|방지/감지|조사|응답|
|---|---|---|
|기술에는 EOP의 모든 사항과 Office 365 P1용 Microsoft Defender 및 다음이 포함됩니다.<u1><li>동일</li>|<li>**위협 탐색기**</li><li>위협 트래커</li><li>캠페인 보기</li>|<li>AIR(자동화된 조사 및 대응)</li><li>위협 탐색기에서 AIR</li><li>손상된 사용자를 위한 AIR</li><li>자동화된 조사를 위한 SIEM 통합 API</li>

따라서 Microsoft Defender for Office 365 P2는 집의 **_조사_* 및 응답 _ 쪽을 확장하고 새로운 헌팅 강도를 추가합니다. 자동화.

Microsoft Defender for Office 365 P2에서 기본 헌팅 도구를 실시간 검색이 아닌 _ *Threat Explorer** 라고 합니다. 보안 센터로 이동할 때 위협 탐색기가 표시될 경우 Office 365 P2용 Microsoft Defender에 있습니다.

Office 365 P1 및 P2용 Microsoft Defender의 세부 정보를 확인한 후 이 **[문서로 이동하세요.](office-365-atp.md)**

> [!TIP]
> EOP 및 Office 365용 Microsoft Defender도 최종 사용자와 다를 수 있습니다. EOP 및 Office 365 P1용 Defender에서는 인식에 중점을 *두며,* 이러한 두 서비스에는 사용자가 추가 분석을 위해 의심스러운 전자 메일을 보고할 수 있도록 보고서 메시지 *Outlook* 추가 기능을 포함합니다. <p> EOP 및 P1의 모든 기능을 포함하는 Office 365 P2용 Defender에서 포커스가 최종 사용자를 위한 추가 교육으로 전환됩니다. 따라서 보안 운영 센터는 강력한 *위협* 시뮬레이터 도구 및 이 도구에서 제공하는 최종 사용자 메트릭에 액세스할 수 있습니다. 

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender for Office 365 요금제 1과 계획 2 치트 시트 비교

이 빠른 참조는 각 Microsoft Defender for Office 365 구독에 제공된 기능을 이해하는 데 도움이 됩니다. EOP 기능에 대한 지식과 결합하면 비즈니스 의사 결정권자는 Office 365용 Microsoft Defender가 요구에 가장 적합한지 결정하는 데 도움이 될 수 있습니다.

|Office 365 계획 1용 Defender|Office 365 계획 2용 Defender|
|---|---|
|구성, 보호 및 검색 기능: <ul><li>[안전한 첨부 파일](atp-safe-attachments.md)</li><li>[안전한 링크](atp-safe-links.md)</li><li>[SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP](atp-for-spo-odb-and-teams.md)</li><li>[Office 365용 Defender의 피싱 방지 보호 기능](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[실시간 탐지](threat-explorer.md)</li></ul>|Office 365 계획 1의 Defender 기능 <p> --- 추가 --- <p> 자동화, 조사, 수정 및 교육 기능: <ul><li>[위협 트래커](threat-trackers.md)</li><li>[위협 탐색기](threat-explorer.md)</li><li>[자동화된 조사 및 응답](office-365-air.md)</li><li>[공격 시뮬레이터](attack-simulator.md)</li></ul>|
|

- Office 365 계획 2용 Microsoft Defender는 Office 365 E5, Office 365 A5 및 Microsoft 365 E5에 포함되어 있습니다.

- Microsoft Defender for Office 365 요금제 1은 Microsoft 365 Business Premium에 포함되어 있습니다.

- Microsoft Defender for Office 365 요금제 1 및 Office 365 계획 2용 Defender는 각각 특정 구독에 대한 추가 기능으로 사용할 수 있습니다. 자세한 내용은 Office [365 계획용 Microsoft Defender의](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)또 다른 링크 기능 가용성입니다.

- 안전한 [문서](safe-docs.md) 기능은 Microsoft 365 E5 또는 Microsoft 365 E5 보안 라이선스가 있는 사용자만 사용할 수 있습니다(Office 365 요금제용 Microsoft Defender에는 포함되지 않음).

- 현재 구독에 Office 365용 Microsoft Defender가 포함되어하지 [](https://go.microsoft.com/fwlink/p/?LinkId=518644)않는 경우 영업에 문의하여 평가판을 시작하고 Office 365용 Microsoft Defender가 조직에서 어떻게 작동할 수 있는지 찾아보아야 합니다.

> [!TIP]
> ***Insider tip** _. EOP 및 Docs.microsoft.com Microsoft Defender for Office 365에 대해 자세히 알아보는 데 docs.microsoft.com 목차를 사용할 수 있습니다. 이 페이지, [Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security)보안 개요로 돌아가면 사이드바에 콘텐츠 조직의 표가 표시됩니다. 배포(마이그레이션 포함)로 시작하여 예방, 검색, 조사 및 대응을 계속합니다. <p> 이 구조는 *_Security Administration** 항목 다음에 보안 작업 **항목으로 나뉘어** 있습니다. 두 작업 역할의 새 구성원인 경우 이 팁의 링크와 내용 표에 대한 지식을 사용하여 공간을 학습할 수 있습니다. 피드백 링크를 *사용하며* *문서를* 평가하는 방법을 기억하세요. 피드백은 고객에게 제공하는 기능을 개선하는 데 도움이 됩니다.

## <a name="where-to-go-next"></a>다음으로 이동 위치

보안 관리자인 경우 메일에 대해 DKIM 또는 DMARC를 구성해야 할 수 있습니다. 우선 순위 사용자에 대해 '엄격' 보안 미리 설정은 롤아웃하거나 제품의 새로운 것을 찾아야 할 수 있습니다. 또는 Security Ops를 사용하는 경우 실시간 검색 또는 위협 탐색기를 활용하여 공격 시뮬레이터를 사용하여 최종 사용자 감지를 조사 및 대응하고 교육할 수 있습니다. 어느 경우든 다음에 볼 수 있는 사항에 대한 몇 가지 추가 권장 사항은 다음과 같습니다.

[SPF, DKIM 및 DMARC를 포함한 전자 메일 인증(세 가지 설정에 대한 링크 포함)](email-validation-and-authentication.md)

[특정 권장 '골든'](recommended-settings-for-eop-and-office365-atp.md) 구성을 참조하고 권장되는 미리 설정을 사용하여 보안 정책을 신속하게 [구성합니다.](preset-security-policies.md)

[Office 365용 Microsoft Defender의](whats-new-in-office-365-atp.md) 새로운 제품(EOP 개발 포함)

[위협 탐색기 또는 실시간 검색 사용](threat-explorer.md)

[Microsoft Defender에서 Office 365용](attack-simulator.md) 공격 시뮬레이터 사용
