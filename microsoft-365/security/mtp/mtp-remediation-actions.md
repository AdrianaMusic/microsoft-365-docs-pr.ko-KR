---
title: Microsoft 365 Defender의 수정 작업
description: Microsoft 365 Defender에서 자동화된 조사를 따르는 수정 작업 개요 보기
keywords: 자동화된, 조사, 경고, 트리거, 작업, 수정
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.date: 12/09/2020
ms.reviewer: evaldm, isco
ms.openlocfilehash: 9e489e3b0100aa138b11d4bfb4ccc8048a2113f4
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49683298"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Microsoft 365 Defender의 수정 작업

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**적용 대상:**
- Microsoft 365 Defender

## <a name="remediation-actions"></a>수정 작업

Microsoft 365 Defender에서 자동화된 조사가 진행되는 동안 및 이후에 악의적 또는 의심스러운 항목에 대한 수정 작업이 식별됩니다. 일부 종류의 수정 작업은 끝점이라고도 하는 디바이스에서 수행됩니다. 기타 수정 작업은 전자 메일 콘텐츠에 대해 수행됩니다. 재구성 작업이 수행, 승인 또는 거부된 후 자동화된 조사가 완료됩니다.

> [!IMPORTANT]
> 수정 작업이 자동으로 수행될지 승인에만 수행될지는 자동화 수준과 같은 특정 설정에 따라 결정됩니다. 자세한 내용은 다음 문서를 참조합니다.
> - [Microsoft 365 Defender에서 자동화된 조사 및 대응 기능 구성](mtp-configure-auto-investigation-response.md)
> - [장치에서 위협이 해결되는 방법](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
> - [전자 메일 및 공동 작업 콘텐츠에 대한 & 수정 작업](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions#threats-and-remediation-actions)

다음 표에는 Microsoft 365 Defender에서 현재 지원되는 수정 작업이 요약됩니다. 

|장치(끝점) 수정 작업  |전자 메일 수정 작업  |
|---------|---------|
|- 조사 패키지 수집 <br/>- 장치 격리(이 작업은 실행을 실행하지 않습니다.)<br/>- 컴퓨터 오프보드 <br/>- 릴리스 코드 실행 <br/>- 릴리스 <br/>- 샘플 요청 <br/>- 코드 실행 제한(이 작업은 실행을 실행 중지할 수 있습니다.) <br/>- 바이러스 백신 검사 실행 <br/>- 중지 및 Quarantine      |- 차단 URL(클릭 시간)<br/>- 전자 메일 메시지 또는 클러스터를 소프트 삭제<br/>- 전자 메일 확인<br/>- 전자 메일 첨부 파일 확인<br/>- 외부 메일 전달 끄기          |

승인 보류 중인지 또는 이미 완료 여부에 따라 수정 작업은 관리 센터에서 볼 [수 있습니다.](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center)

## <a name="remediation-actions-that-follow-automated-investigations"></a>자동화된 조사를 따르는 수정 작업

자동화된 조사가 완료되면 관련된 모든 증거에 대한 판결에 도달합니다. 판정에 따라 수정 작업이 식별됩니다. 경우에 따라 수정 작업이 자동으로 수행 됩니다. 그 밖의 경우에는 재구성 작업이 승인을 기다립니다. 자동화된 조사 및 응답이 구성된 방식에 [따라 모두 달라 습니다.](mtp-configure-auto-investigation-response.md)

도출 가능한 의견과 결과는 다음 테이블에서 확인할 수 있습니다. 

| 의견    | 영역    | 결과|
|------|------|------|
| 악성    | 장치 (끝점)    | 재구성 작업은 자동으로 수행됩니다(조직의 장치 그룹이 전체로 설정되어 있는 경우 - 위협을 자동으로 **수정)** [](mtp-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)|
| 악성    | 전자 메일 콘텐츠 (Url 또는 첨부 파일) | 승인 보류 중인 재구성 활동 |
| 피싱    | 장치 또는 전자 메일 콘텐츠 | 승인 보류 중인 재구성 활동 |
| 위협을 찾을 수 없음    | 장치 또는 전자 메일 콘텐츠    | 재구성 작업이 필요 하지 않습니다.|


## <a name="remediation-actions-that-are-taken-manually"></a>수동으로 수행된 수정 작업

자동화된 조사에 따라 수정 작업 외에도 보안 운영 팀은 특정 수정 작업을 수동으로 수행할 수 있습니다. 여기에는 다음 작업이 포함됩니다.

- 장치 고리 또는 파일 검지와 같은 수동 장치 작업입니다.
- 수동 전자 메일 작업(예: 전자 메일 메시지 소프트 삭제) 
- [장치 또는 전자](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) 메일에 대한 고급 헌팅 작업
- [전자](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer) 메일을 정크 메일로 이동, 소프트 삭제 전자 메일 또는 하드 삭제 전자 메일과 같은 전자 메일 콘텐츠에 대한 탐색기 작업
- 파일 [삭제,](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response) 프로세스 중지, 예약된 작업 제거와 같은 수동 실시간 응답 작업
- [Microsoft Defender for Endpoint API를](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/management-apis#microsoft-defender-for-endpoint-apis)사용하여 실시간 응답 작업(예: 장치 고르기, 바이러스 백신 검사 실행, 파일에 대한 정보 다운로드) 

## <a name="next-steps"></a>다음 단계

- [알림 센터 방문](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center)
- [보류 중인 작업 승인 또는 거부](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir-actions)
- [자동화된 조사 및 응답 기능에서 가짓 긍정/부정 처리](mtp-autoir-report-false-positives-negatives.md)
