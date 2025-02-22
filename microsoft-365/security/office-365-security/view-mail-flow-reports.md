---
title: 보고서 대시보드에서 메일 흐름 보고서 보기
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 관리자는 보안 및 준수 센터의 보고서 대시보드에서 사용할 수 있는 메일 흐름 & 수 있습니다.
ms.custom: ''
ms.openlocfilehash: 1ededf2d0d693c537c159c52d00deb03f278b4b2
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659468"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>보안 및 준수 센터의 보고서 대시보드에서 & 보고서 보기

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


보안 및 준수 센터의 메일 흐름 [](mail-flow-insights-v2.md) 대시보드에서 사용할 수 있는 메일 흐름 보고서 외에도 & 보고서 대시보드에서 다양한 추가 메일 흐름 보고서를 사용하여 Microsoft 365 조직을 모니터링할 수 있습니다.

필요한 사용 [](#what-permissions-are-needed-to-view-these-reports)권한이 있는 경우 보고서 대시보드로 & 보안 및 준수 [센터에서](https://office.protection.com) 이러한 보고서를 볼 **수** \> **있습니다.** 보고서 대시보드로 직접 이동하기 위해 를 <https://protection.office.com/insightdashboard> 열습니다.

![보안 및 준수 & 대시보드 보고](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="connector-report"></a>커넥터 보고서

커넥터 **보고서에는** 조직에 대해 [](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) 구성된 인바운드 및 아웃바운드 커넥터의 메일 흐름 활동이 표시됩니다.

보고서를 표시하려면 보안 및 준수 [센터를 &](https://protection.office.com) **보고서** 대시보드로 이동하여 커넥터 보고서를 \>  **선택합니다.** 보고서로 직접 이동하기 위해 를 열 수 <https://protection.office.com/reportv2?id=ConnectorReport> 있습니다.

![보고서 대시보드의 커넥터 보고서 위젯](../../media/connector-report-widget.png)

### <a name="report-view-for-the-connector-report"></a>커넥터 보고서에 대한 보고서 보기

보고서 보기에서는 다음 차트를 사용할 수 있습니다.

- **데이터 보기: 메일 흐름:** 이 차트에는 다음을 통해 구성되는 인바운드 및 아웃바운드 메시지 수가 표시됩니다.

  - **합계**
  - **커넥터가 없는 인터넷에서**
  - **커넥터가 없는 인터넷으로**
  - 구성한 특정 커넥터입니다.

  차트에서 데이터를 격리하려면 컨트롤에  대한 데이터 표시를 사용하여 이러한 옵션 또는 모든 메일 흐름 중 하나를 **선택합니다.**

  ![커넥터 보고서에서 메일 흐름에 따라 데이터 보기](../../media/connector-report-view-data-by-mail-flow.png)

- **데이터 보기: TLS 사용법:** 이 차트는 메일 흐름에 대한 TLS(전송 계층 보안) 버전 사용량의 백분율을 보여 줍니다.

  차트에서 데이터를 격리하려면 컨트롤에  대한 데이터 표시를 사용하여 다음 옵션 중 하나를 선택합니다.

  - **모든 메일 흐름**
  - **커넥터가 없는 인터넷에서**
  - **커넥터가 없는 인터넷으로**
  - 구성한 특정 커넥터입니다.

  ![커넥터 보고서에서 TLS 사용 현황으로 데이터 보기](../../media/connector-report-view-data-by-tls-usage.png)

보고서 보기에서 **필터를** 클릭하면 시작 날짜와 종료  날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

### <a name="details-table-view-for-the-connector-report"></a>커넥터 보고서에 대한 세부 정보 테이블 보기

보고서 **보기에서** 세부 정보 표 보기를 클릭하면 다음 정보가 표시됩니다.

- **날짜**
- **커넥터 방향 및 이름**
- **커넥터 유형**
- **강제 TLS?**: **True** 또는 **False** 값
- **TLS** 없음(백분율)
- **TLS 1.0(백분율)**
- **TLS 1.1(백분율)**
- **TLS 1.2(백분율)**
- **볼륨**: 메시지 수입니다.

세부 정보 표 보기에서 **필터를** 클릭하면 시작 날짜와  종료 날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

## <a name="exchange-transport-rule-report"></a>Exchange 전송 규칙 보고서

**Exchange 전송 규칙 보고서는** 메일 흐름 규칙(전송 규칙라고도 알려지음)이 조직의 받는 메시지와 보내진 메시지에 줄 수 있는 영향을 보여줍니다.

보고서를 표시하려면 보안 및 준수 [&](https://protection.office.com)보고서 대시보드로 이동하여 Exchange 전송  \>  **규칙을 선택합니다.** 보고서로 직접 이동하기 위해 를 열 수 <https://protection.office.com/reportv2?id=ETRRuleReport> 있습니다.

![보고서 대시보드의 Exchange 전송 규칙 위젯](../../media/transport-rule-report-widget.png)

### <a name="report-view-for-the-exchange-transport-rule-report"></a>Exchange 전송 규칙 보고서에 대한 보고서 보기

보고서 보기에서는 다음 차트를 사용할 수 있습니다.

- **데이터 보기: Exchange 전송 규칙** \> **세분화: 방향:** 이 차트에는  전송 규칙의 영향을 받은 인바운드 및 **아웃바운드** 메시지 수가 표시됩니다.

- **데이터 보기: Exchange 전송 규칙** \> **심각도:** 이 차트는 높은 심각도  및 보통 심각도 및 낮은 심각도 메시지의 수를 **보여** 주며,  심각도 수준을 규칙의 작업으로 설정할 수 있습니다(심각도 수준 또는 _SetAuditSeverity로_ 이 규칙 감사). 자세한 내용은 [Exchange Online의 메일 흐름 규칙 작업을 참조하세요.](https://docs.microsoft.com//Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

- **데이터 보기: DLP Exchange 전송 규칙** \> **세분화: 방향:** 이 차트는  DLP(데이터 손실 방지) 전송 규칙의 영향을 받은 인바운드 및 아웃바운드 메시지의 수를 보여줍니다.  다음 옵션 중 원하는 옵션을 선택하여 차트를 추가로 구체화할 수 있습니다.

  - **데이터 표시: 모든 DLP 전송 규칙**
  - **데이터 표시: 손상된 사용자**
  - **데이터 표시: 미국 애국법에서 검색된 콘텐츠의 양이 적습니다.**

- **데이터 보기: DLP Exchange 전송 규칙** \> **세분화: 방향:** 이 보기에는  높은 심각도 및 보통 심각도 및 DLP 전송 규칙의 영향을 받은 낮은 심각도 메시지의 수가 표시됩니다.  다음 옵션 중 원하는 옵션을 선택하여 차트를 추가로 구체화할 수 있습니다.

  - **데이터 표시: 모든 DLP 전송 규칙**
  - **데이터 표시: 손상된 사용자**
  - **데이터 표시: 미국 애국법에서 검색된 콘텐츠의 양이 적습니다.**

보고서 보기에서 **필터를** 클릭하면 다음 필터를 사용하여 결과를 수정할 수 있습니다.

- **시작 날짜** 및 **종료 날짜**
- 방향 값
- 심각도 값

![Exchange 전송 규칙 보고서의 보고서 보기](../../media/transport-rule-report-report-view.png)

### <a name="details-table-view-for-the-exchange-transport-rule-report"></a>Exchange 전송 규칙 보고서에 대한 세부 정보 테이블 보기

세부 **정보** 표 보기를 클릭하면 표시되는 정보는 보고 있는 차트에 따라 다를 수 있습니다.

- **데이터 보기: Exchange 전송 규칙:**

  - **날짜**
  - **전송 규칙**
  - **제목**
  - **보낸 사람 주소**
  - **받는 사람 주소**
  - **심각도**
  - **방향**

- **데이터 보기: DLP Exchange 전송 규칙:**

  - **날짜**
  - **DLP 정책**
  - **전송 규칙**
  - **제목**
  - **보낸 사람 주소**
  - **받는 사람 주소**
  - **심각도**
  - **방향**

세부 정보 테이블 보기에서 **필터를** 클릭하면 다음 필터를 사용하여 결과를 수정할 수 있습니다.

- **시작 날짜** 및 **종료 날짜**
- 방향 값
- 심각도 값

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

## <a name="forwarding-report"></a>전달 보고서

전달 **보고서에는** Exchange Online 사서함의 외부 도메인으로 조직의 자동으로 전달된 메시지가 표시됩니다. 전달된 메시지는 보안 또는 규정 준수 위험을 내포할 수 있으며 계정이 손상된 것일 수 있습니다.

보고서를 표시하려면 보안 및 준수 [&](https://protection.office.com)열고 보고서  대시보드로 이동한 후 전달 \>  **보고서를 선택합니다.** 보고서로 직접 이동하기 위해 를 열 수 <https://protection.office.com/reportv2?id=MailFlowForwarding> 있습니다.

![보고서 대시보드에서 보고서 위젯 전달](../../media/forwarding-report-widget.png)

### <a name="report-view-for-the-forwarding-report"></a>전달 보고서에 대한 보고서 보기

보고서 보기에서는 다음 차트를 사용할 수 있습니다.

- **데이터 표시: 전달** 메서드: 다음 메서드가 표시됩니다.

  - **전송 규칙:** 메일 흐름 [규칙으로도 알려져 있습니다.](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
  - **사서함 규칙:** 받은 편지함 [규칙으로도 알려져 있습니다.](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59)

  ![전달 보고서의 전달 메서드 보기](../../media/forwarding-report-forwarding-methods.png)

- **다음에 대한 데이터 표시:** 전달 도메인: 이 보기에는 전달 대상인 받는 사람 도메인이 표시됩니다.

  ![전달 보고서의 전달 도메인 보기](../../media/forwarding-report-forwarding-domains.png)

- **다음에 대한 데이터 표시: 전달자:** 다음 전달자 표시

  - **전송 규칙**
  - 전달 받은 편지함 규칙이 포함된 사서함입니다.

  ![전달 보고서의 전달자 보기](../../media/forwarding-report-forwarders.png)

보고서 보기에서 **필터를** 클릭하면 시작 날짜와 종료  날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

### <a name="details-table-view-for-the-forwarding-report"></a>전달 보고서에 대한 세부 정보 테이블 보기

보고서 **보기에서** 세부 정보 표 보기를 클릭하면 다음 정보가 표시됩니다.

- **전달자:** 전달 **받은** 편지함 규칙이 포함된 값 전송 규칙 또는 사서함입니다.
- **전달 유형:** 사서함 규칙 또는 전송 **규칙** 값입니다. 
- **받는 사람 이름**
- **받는 사람 도메인**
- **세부 정보:** 메일 흐름 규칙의 GUID 값 또는 받은 편지함 규칙의 RuleIdentity 값입니다.
- **개수**
- **첫 번째 전달 날짜**

세부 정보 표 보기에서 **필터를** 클릭하면 시작 날짜와  종료 날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

## <a name="mailflow-status-report"></a>메일 흐름 상태 보고서

메일 **흐름 상태 보고서는** 보낸 전자 메일 및 받은 전자 메일 보고서와 유사하며, [](#sent-and-received-email-report)에지에서 허용되거나 차단된 전자 메일에 대한 추가 정보가 있습니다. 이 보고서는 에지 보호 정보를 포함하는 유일한 보고서로, EOP(Exchange Online Protection)의 평가를 위해 서비스에 허용되기 전에 차단되는 전자 메일의 수만 보여 주며, 받는 사람 5명에게 메시지가 전송된 경우 하나의 메시지가 아니라 5개의 다른 메시지로 계산됩니다.
보고서를 확인하려면 보안 & 준수 센터를 열고  보고서 대시보드로 이동하여 메일 흐름 [상태](https://protection.office.com) \>  **보고서를 선택합니다.** 메일 흐름 상태 **보고서로** 직접 이동 하 고 를 를 를 를 를 를 를 를 열 수 <https://protection.office.com/mailflowStatusReport> 있습니다.

![보고서 대시보드의 메일 흐름 상황 보고서 위젯](../../media/mail-flow-status-report-widget.png)

### <a name="type-view-for-the-mailflow-status-report"></a>메일 흐름 상태 보고서의 형식 보기

보고서를 열면 유형  탭이 기본적으로 선택됩니다. 기본적으로 이 보기에는 다음 필터로 구성된 차트 및 데이터 테이블이 포함되어 있습니다.

- **날짜:** 지난 7일
- **방향**:

  - **인바운드**
  - **아웃바운드**
  - **Intra-org**: This count is for messages within a tenant i.e 보낸 사람 abc@domain.com 받는 사람에게 xyz@domain.com(인바운드  및 아웃바운드와 별도로 **계산)**

- **Type**:

  - **좋은 메일**
  - **맬웨어**
  - **스팸**
  - **에지 보호**
  - **규칙 메시지**
  - **피싱 전자 메일**

차트는 형식 값으로 **구성됩니다.**

필터를 클릭하거나 차트  범례에서 값을 클릭하여 이러한 필터를 변경할 수 있습니다.

데이터 테이블에는 다음 정보가 포함되어 있습니다.

- **방향**
- **Type**
- **24시간**
- **3일**
- **7일**
- **15일**
- **30일**

자세한 내용을 **보려면 범주** 선택을 클릭하면 다음 값에서 선택할 수 있습니다.

- **피싱 전자 메일**: 이 선택을 통해 위협 방지 상태 [보고서로 전송됩니다.](view-email-security-reports.md#threat-protection-status-report)
- **전자 메일의** 맬웨어: 이 선택을 통해 위협 방지 상태 [보고서로 전송됩니다.](view-email-security-reports.md#threat-protection-status-report)
- **스팸 검색:** 이 선택을 통해 스팸 검색 보고서로 [전송됩니다.](view-email-security-reports.md#spam-detections-report)
- **Edge 차단 스팸:** 이 선택을 통해 스팸 검색 보고서로 [전송됩니다.](view-email-security-reports.md#spam-detections-report)

**내보내기**:

세부 정보 보기의 경우 하루 동안만 데이터를 내보낼 수 있습니다. 따라서 7일 동안 데이터를 내보내는 경우 7개 다른 내보내기 작업을 수행해야 합니다.

내보낼 .csv 파일은 각각 150,000개 행으로 제한됩니다. 해당 일의 데이터에 150,000개 이상의 행이 포함되어 있는 경우 여러 .csv 파일이 만들어집니다.

![메일 흐름 상태 보고서의 유형 보기 ](../../media/mail-flow-status-report-type-view.png)

### <a name="direction-view-for-the-mailflow-status-report"></a>메일 흐름 상태 보고서의 방향 보기

방향 **탭을** 클릭하면 유형 보기의 동일한 기본 **필터가** 사용됩니다.

차트는 방향 값으로 **구성됩니다.**

필터를 클릭하거나 차트  범례에서 값을 클릭하여 이러한 필터를 변경할 수 있습니다. 형식 보기의 **동일한 필터가** 사용됩니다.

데이터 테이블에는 형식 보기와 동일한 **정보가** 들어 있습니다.

사용 **가능한 선택 항목** 및 동작에 대한 자세한 내용은 종류 선택 보기와 같습니다. 

**내보내기**:

세부 정보 보기의 경우 하루 동안만 데이터를 내보낼 수 있습니다. 따라서 7일 동안 데이터를 내보내는 경우 7개 다른 내보내기 작업을 수행해야 합니다.

내보낼 .csv 파일은 각각 150,000개 행으로 제한됩니다. 해당 일의 데이터에 150,000개 이상의 행이 포함되어 있는 경우 여러 .csv 파일이 만들어집니다.

![메일 흐름 상태 보고서의 방향 보기 ](../../media/mail-flow-status-report-direction-view.png)

### <a name="funnel-view-for-the-mailflow-status-report"></a>메일 흐름 상태 보고서의 FUNNEL 보기

**Funnel** 보기는 Microsoft의 전자 메일 위협 방지 기능이 조직에서 수신 및 전송되는 전자 메일을 필터링하는 방법을 보여줍니다. 전체 전자 메일 수와 에지 보호, 맬웨어 방지, 피싱 방지, 스팸 방지 및 스푸핑 방지를 비롯한 구성된 위협 방지 기능이 이 수에 미치는 영향에 대한 세부 정보를 제공합니다.

**FUNNel** 탭을 클릭하면 기본적으로 이 보기에는 차트와 다음 필터로 구성된 데이터 테이블이 포함되어 있습니다.

- **날짜:** 지난 7일

- **방향**:

  - **인바운드**
  - **아웃바운드**
  - **내부:** 테넌트 내에서 보낸 메시지에 대한 수입니다. 즉, 보낸 abc@domain.com 받는 사람에게 xyz@domain.com 수 있습니다(인바운드 및 아웃바운드와는 별도로 계산).

집계 보기 및 데이터 테이블 보기는 90일 동안 필터링할 수 있습니다.

필터를 클릭하면 차트와 데이터 테이블을 모두 필터링할 수 있습니다.

이 차트에는 다음별로 구성한 전자 메일 수가 표시됩니다.

- **총 전자 메일**
- **Edge 보호 후 전자 메일**
- **맬웨어 방지, 파일 신뢰도, 파일 형식 블록 이후의 전자 메일**
- **피싱 방지, URL 신뢰도, 브랜드 가장, 스푸핑 방지 이후의 전자 메일**
- **스팸 방지, 대량 메일 필터링 후 전자 메일**
- 사용자 및 도메인 가장 <sup>1</sup> **이후의 전자 메일**
- **파일 후 전자 메일 및 URL 확인**<sup>1</sup>
- **배달 후 보호 후 무해한 것으로 감지된 전자 메일(URL 클릭 시간 보호)**

<sup>1</sup> Office 365용 Defender만

EOP 또는 Office 365용 Defender에서 개별적으로 필터링한 전자 메일을 보려면 차트 범례의 값을 클릭합니다.

데이터 테이블에는 내선 날짜 순서로 표시되는 다음 정보가 들어 있습니다.

- **날짜**
- **총 전자 메일**
- **에지 보호**
- **맬웨어 방지, 파일 신뢰도, 파일 형식 블록:**
  - **파일 신뢰도**: 다른 Microsoft 고객이 첨부한 파일을 식별하여 필터링된 메시지입니다.
  - **파일 형식 블록:** 메시지에 식별된 악성 파일의 유형으로 인해 필터링된 메시지입니다.
- **피싱 방지, URL 신뢰도, 브랜드 가장,** 스푸핑 방지:
  - **URL 신뢰도**: 다른 Microsoft 고객이 URL을 식별하여 필터링된 메시지입니다.
  - **브랜드 가장:** 보낸 사람으로 가장하는 잘 알려진 브랜드에서 보낸 메시지로 인해 필터링된 메시지입니다.
  - **스푸핑** 방지: 받는 사람이 속한 도메인 또는 메시지 보낸 사람이 소유하지 않은 도메인을 스푸핑하려고 하여 필터링된 메시지입니다.
- **스팸 방지, 대량 메일 필터링:**
  - **대량 메일 필터링:** 받는 사람에게 대량 메일을 배달하려고 시도하여 필터링된 메시지입니다.
- **사용자 및 도메인 가장(Office 365용 Defender)**:
  - **사용자 가장:** 피싱 방지 정책의 가장 보호 설정에 정의된 사용자(메시지 보낸 사람)를 가장하려는 시도로 인해 필터링된 메시지입니다.
  - **도메인 가장:** 피싱 방지 정책의 가장 보호 설정에 정의된 도메인을 가장하려는 시도로 인해 필터링된 메시지입니다.
- **파일 및 URL 확인(Office 365용 Defender)**:
  - **파일 검색:** 안전한 첨부 파일 정책에 의해 필터링된 메시지입니다.
  - **URL 검색:** 안전한 링크 정책에 의해 필터링된 메시지입니다.
- **사후 배달 보호 및 ATP(ZAP) 또는 EOP(ZAP)**: ZAP는 0시간 자동 비우기를 나타냅니다.

데이터 테이블에서 행을 선택하면 플라이아웃에 전자 메일 수의 추가 분석이 표시됩니다.

**내보내기**:

옵션에서 **내보내기를** 클릭한 후 다음 값 중 하나를 선택할 수 있습니다. 

- **요약(최근 90일 동안의 데이터 사용)**
- **세부 정보(최근 30일 동안의 데이터 사용)**

**날짜에서** 범위를 선택한 다음 적용을 **클릭합니다.** 현재 필터에 대한 데이터는 .csv 파일로 내보낼 수 있습니다.

내보낼 .csv 파일은 각각 150,000개 행으로 제한됩니다. 데이터에 150,000개 이상의 행이 포함되어 있는 경우 여러 .csv 파일이 만들어집니다.

 ![메일 흐름 상태 보고서의 FUNNEL 보기 ](../../media/mail-flow-status-report-funnel-view.png)

### <a name="tech-view-for-the-mailflow-status-report"></a>메일 흐름 상태 보고서에 대한 기술 보기

기술 **보기는** **Funnel** 보기와 유사하여 구성된 위협 방지 기능에 대한 보다 세부적인 세부 정보를 제공합니다. 차트에서 다양한 위협 방지 단계에서 메시지를 분류하는 방법을 볼 수 있습니다.

기술 보기  탭을 클릭하면 기본적으로 이 보기에는 차트와 다음 필터로 구성된 데이터 테이블이 포함되어 있습니다.

- **날짜:** 지난 7일

- **방향**:

  - **인바운드**
  - **아웃바운드**
  - **Intra-org**: This count is for messages within a tenant i.e 보낸 사람 abc@domain.com 받는 사람에게 xyz@domain.com(인바운드 및 아웃바운드와 별도로 계산)

집계 보기 및 데이터 테이블 보기는 90일 동안 필터링할 수 있습니다.

필터를 클릭하면 차트와 데이터 테이블을 모두 필터링할 수 있습니다.

이 차트에는 다음 범주로 구성된 메시지가 표시됩니다.

- **총 전자 메일**
- **에지** 허용 **및 Edge 필터링**
- **맬웨어가 아닌** 경우, **안전 첨부 파일 검색,** 맬웨어 방지 <sup>\*</sup> 엔진 **검색** 및 **규칙 메시지**
- **피싱** 금지, **DMARC 실패,** 가장 **검색,** 스푸핑 **검색** 및 **피싱 감지**
- **URL 검색 및 URL** 검색으로 검색 **안**<sup>\*</sup>
- **스팸 및** 스팸  **아미**
- **악성이 아닌 전자 메일,** **안전한 링크 검색** 및 <sup>\*</sup> **ZAP**

<sup>\*</sup> Office 365용 Defender

차트에서 범주 위에 마우스를 대면 해당 범주의 메시지 수를 볼 수 있습니다.

데이터 테이블에는 내선 날짜 순서로 표시되는 다음 정보가 들어 있습니다.

- **날짜**
- **총 전자 메일**
- **필터링된 에지**
- **맬웨어 방지 엔진, 안전한 첨부 파일, 필터링된 규칙:**
  - **규칙 필터링된** 규칙: 메일 흐름 규칙(전송 규칙 이라고도 알려지음)으로 인해 필터링된 메시지입니다.
- **DMARC, 가장, 스푸핑, 피싱 필터링:**
  - **DMARC**: 메시지의 DMARC 인증 검사에 실패하여 필터링된 메시지입니다.
- **URL 검색**
- **스팸 방지 필터링**
- **ZAP 제거됨**
- **안전한 링크로 검색**

데이터 테이블에서 행을 선택하면 플라이아웃에 전자 메일 수의 추가 분석이 표시됩니다.

**내보내기**:

내보내기 **클릭 시** **옵션에서** 다음 값 중 하나를 선택할 수 있습니다.

- **요약(최근 90일 동안의 데이터 사용)**
- **세부 정보(최근 30일 동안의 데이터 사용)**

**날짜에서** 범위를 선택한 다음 적용을 **클릭합니다.** 현재 필터에 대한 데이터는 .csv 파일로 내보낼 수 있습니다.

내보낼 .csv 파일은 각각 150,000개 행으로 제한됩니다. 데이터에 150,000개 이상의 행이 포함되어 있는 경우 여러 .csv 파일이 만들어집니다.

 ![메일 흐름 상태 보고서의 기술 보기 ](../../media/mail-flow-status-report-Tech-view.png)

## <a name="sent-and-received-email-report"></a>보낸 메일 및 받은 전자 메일 보고서

**보내고** 받는 전자 메일 보고서는 스팸 검색, 맬웨어 및 "양호"로 식별된 전자 메일을 포함하여 들어오고 받는 전자 메일에 대한 정보를 표시하는 스마트 보고서입니다. 이 보고서와 [메일](#mailflow-status-report) 흐름 상태 보고서의 차이점은 이 보고서에 Edge 보호로 차단된 메시지에 대한 데이터는 포함하지 않습니다. 받는 사람 5명에게 메시지가 전송된 경우 하나의 메시지로 계산됩니다.

보고서의 집계 보기 및 세부 정보 보기에서는 90일 동안 필터링할 수 있습니다.

보고서를 확인하려면 Security [& 준수](https://protection.office.com)센터를 열고  보고서 대시보드로 이동하여 보내고 받은 전자 메일을 \>  **선택합니다.** 보고서로 직접 이동하기 위해 를 열 수 <https://protection.office.com/reportv2?id=SentAndReceivedMailATP> 있습니다.

![보고서 대시보드에서 보낸 전자 메일 위젯 및 받은 전자 메일 위젯](../../media/sent-and-received-email-report-widget.png)

### <a name="report-view-for-the-sent-and-received-email-report"></a>보내고 받은 전자 메일 보고서에 대한 보고서 보기

보고서 보기에서는 다음 차트를 사용할 수 있습니다.

- **세분화: 유형:** 차트에 사용 가능한 모든 범주가 표시됩니다.

  - **합계**
  - **좋은 메일**
  - **맬웨어(맬웨어** 방지)(EOP)
  - **스팸 감지**
  - **규칙 메시지**
  - **고급 맬웨어(Office** 365용 Microsoft Defender)

  차트에서 하루(데이터 포인트)에 마우스를 대면 해당 일자에 대한 세부 정보를 볼 수 있습니다.

  ![보내고 받은 전자 메일 보고서에 보기 입력](../../media/sent-and-received-email-report-type-view.png)

- **세분화하여: 방향:** 차트에  **총,** 인바운드 및 **아웃바운드 데이터가** 표시됩니다. 차트에서 하루(데이터 포인트)에 마우스를 대면 해당 일자에 대한 세부 정보를 볼 수 있습니다.

  ![보내고 받은 전자 메일 보고서의 방향 보기](../../media/sent-and-received-email-report-direction-view.png)

- **드릴다운** \> **맬웨어(맬웨어 방지)**: 이 선택을 통해 전자 메일 보고서의 [맬웨어 검색으로 전달됩니다.](view-email-security-reports.md#malware-detections-in-email-report)

- **드릴다운** \> **스팸 검색)**: 이 선택을 통해 스팸 검색 보고서로 [전송됩니다.](view-email-security-reports.md#spam-detections-report)

보고서 보기에서 **필터를** 클릭하면 다음 필터를 사용하여 결과를 수정할 수 있습니다.

- **시작 날짜** 및 **종료 날짜**
- 방향 값
- 형식 값

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

### <a name="details-table-view-for-the-sent-and-received-email-report"></a>보낸 전자 메일 보고서 및 받은 전자 메일 보고서에 대한 세부 정보 테이블 보기

**세분화로** 세부 정보 표 **보기:** 방향  또는 세분화: 방향 보기를 클릭하면 다음 정보가 표시됩니다.

- **날짜(UTC)**
- **Type**
- **방향**
- **메시지 수**

세부 정보 테이블 보기에서 **필터를** 클릭하면 다음 필터를 사용하여 결과를 수정할 수 있습니다.

- **시작 날짜** 및 **종료 날짜**
- 방향 값
- 형식 값

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

## <a name="top-senders-and-recipients-report"></a>상위 보낸 사람 및 받는 사람 보고서

Top **senders and recipients** report is a pie chart showing your top email senders and recipients.

보고서를 확인하려면 보안 & 준수 센터를 열고  보고서 대시보드로 이동한 다음 상위 보낸 사람 [및 받는](https://protection.office.com) \>  **사람을 선택합니다.** 보고서로 직접 이동하기 위해 를 열 수 <https://protection.office.com/reportv2?id=TopSenderRecipientsATP> 있습니다.

![보고서 대시보드의 상위 보낸 사람 및 받는 사람 위젯](../../media/top-senders-and-recipients-widget.png)

### <a name="report-view-for-the-top-senders-and-recipient-report"></a>상위 보낸 사람 및 받는 사람 보고서에 대한 보고서 보기

보고서 보기에서는 다음 차트를 사용할 수 있습니다.

- **상위 메일 보낸 \> 사람에 대한 데이터 표시**
- **상위 메일 \> 받는 사람에 대한 데이터 표시**
- **상위 스팸 받는 \> 사람에 대한 데이터 표시**
- **데이터 표시 \> 상위 맬웨어 받는** 사람(EOP)
- **상위 맬웨어 받는 사람에 대한 데이터 \> 표시(Office 365용 Defender)**

이러한 선택에 따라 파이 차트의 컴포지션이 변경됩니다.

파이 차트에서 에지 위에 마우스를 대면 보내거나 받은 메시지 수를 볼 수 있습니다.

보고서 보기에서 **필터를** 클릭하면 시작 날짜와 종료  날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

![상위 보낸 사람 및 받는 사람 보고서의 보고서 보기에 있는 파이 차트](../../media/top-senders-and-recipients-report-view.png)

### <a name="details-table-view-for-the-top-senders-and-recipient-report"></a>상위 보낸 사람 및 받는 사람 보고서에 대한 세부 정보 테이블 보기

세부 **정보** 표 보기를 클릭하면 표시되는 정보는 보고 있는 차트에 따라 다를 수 있습니다.

- **상위 메일 보낸 \> 사람에 대한 데이터 표시**

  - **상위 메일 보낸 사람**
  - **개수**

- **상위 메일 \> 받는 사람에 대한 데이터 표시**

  - **상위 메일 받는 사람**
  - **개수**

- **상위 스팸 받는 \> 사람에 대한 데이터 표시**

  - **상위 스팸 받는 사람**
  - **개수**

- **데이터 표시 \> 상위 맬웨어 받는** 사람(EOP)

  - **상위 맬웨어 받는 사람**
  - **개수**

- **상위 맬웨어 받는 사람에 대한 데이터 \> 표시(Office 365용 Defender)**

  - **상위 맬웨어 받는 사람(Office 365용 Defender)**
  - **개수**

세부 정보 표 보기에서 **필터를** 클릭하면 시작 날짜와  종료 날짜가 있는 날짜 범위를 **지정할 수 있습니다.**

보고서 보기로 돌아가려면 보고서 **보기를 클릭합니다.**

## <a name="what-permissions-are-needed-to-view-these-reports"></a>이러한 보고서를 보는 데 필요한 사용 권한은 무엇입니까?

이 문서에 설명된 보고서를 보고 사용하려면 Security & 준수 센터에서 다음 역할 그룹 중 하나에 & 합니다.

- **조직 관리**
- **보안 관리자**
- **보안 읽기**
- **전역 읽기**

자세한 내용은 [보안 및 준수 센터의 사용 권한](permissions-in-the-security-and-compliance-center.md)을 참조하세요.

**참고:** Microsoft 365 관리 센터에서 해당 Azure Active Directory 역할에 사용자를 추가하면 사용자에게 보안  & 준수 센터의 필요한 사용 권한과 Microsoft 365의 다른 기능에 대한 사용 권한이 부여됩니다. 자세한 내용은 [관리자 역할 정보](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)를 참조하세요.

## <a name="related-topics"></a>관련 항목

[보안 및 준수 센터의 스마트 보고서 및 인사이트](reports-and-insights-in-security-and-compliance.md)

[보안 및 준수 센터의 메일 흐름 파악](mail-flow-insights-v2.md)

[보안 및 준수 센터의 전자 메일 보안 보고서 보기](view-email-security-reports.md)

[Office 365용 Microsoft Defender에 대한 보고서 보기](view-reports-for-atp.md)
