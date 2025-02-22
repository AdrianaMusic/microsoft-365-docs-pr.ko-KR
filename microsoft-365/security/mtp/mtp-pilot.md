---
title: 파일럿 Microsoft 365 Defender 프로젝트 실행
description: 프로덕션에서 파일럿 Microsoft 365 Defender 프로젝트를 실행하여 Microsoft 365 Defender의 이점과 채택을 효과적으로 파악합니다.
keywords: Microsoft 위협 방지 파일럿, 파일럿 Microsoft Threat Protection 프로젝트 실행, 프로덕션에서 Microsoft Threat Protection 평가, Microsoft Threat Protection 파일럿 프로젝트, 사이버 보안, 고급 영구 위협, 엔터프라이즈 보안, 장치, 장치, ID, 사용자, 데이터, 응용 프로그램, 인시던트, 자동화된 조사 및 수정, 고급 헌팅
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.openlocfilehash: f01e918d35ce77d9239c200355c7b4c48c9e2b84
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659324"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>파일럿 Microsoft 365 Defender 프로젝트 실행 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**적용 대상:**
- Microsoft 365 Defender


이 가이드는 체계적인 계획을 세우고, 공격 시뮬레이션 기능을 사용하는 방법을 안내하고, 마지막으로 주요 이행을 통해 파일럿을 끝내고, 결과를 반영하고 문서화하는 포인터를 제공하여 파일럿 프로젝트를 실행할 수 있도록 합니다.

![Microsoft 365 Defender 파일럿 실행 단계](../../media/pilotphases.png)


파일럿을 실행하면 Microsoft 365 Defender 채택의 이점을 효과적으로 확인할 수 있습니다. 프로덕션 환경에서 Microsoft 365 Defender를 사용하도록 설정하고 사용 사례를 시작하기 전에 파일럿 프로젝트에 대해 수행할 작업을 결정하고 성공 기준을 설정하는 것이 가장 좋습니다. 


## <a name="how-to-use-this-pilot-playbook"></a>이 파일럿 플레이북을 사용하는 방법

이 가이드에서는 Microsoft 365 Defender에 대한 개요와 파일럿 프로젝트를 설정하는 방법에 대한 단계별 지침을 제공합니다. 

Microsoft 365 Defender는 엔드포인트, ID, 전자 메일 및 응용 프로그램에서 기본적으로 보호, 탐지, 예방, 조사 및 대응을 조정하여 정교한 공격으로부터 통합된 보호를 제공하는 통합 사전 및 사후 위반 엔터프라이즈 방어 제품군입니다. 이를 위해 다음 기능을 결합하고 단일 보안 솔루션으로 오케스트레이션합니다.
  - Microsoft Defender for Endpoint, Microsoft Defender Advanced Threat Protection의 새 이름(끝점)
  - Office 365 ATP의 새로운 이름인 Office 365용 Microsoft Defender(전자 메일) 
  - Azure ATP의 새 이름인 ID용 Microsoft Defender(ID) 
  - Microsoft Cloud App Security(앱)

![클라우드 of_Microsoft, Microsoft Cloud App Security 및 데이터용 끝점용 Microsoft Defender for Identity에 대한 사용자용 이미지 365 Defender 솔루션, ID용 Microsoft Defender](../../media/mtp/m365pillars.png)

통합된 Microsoft 365 Defender 솔루션을 사용하여 보안 전문가는 끝점용 Microsoft Defender, Office 365용 Microsoft Defender, ID용 Microsoft Defender 및 Microsoft Cloud App Security에서 수신하는 위협 신호를 통합하고 위협의 전체 범위와 영향, 위협이 환경에 들어오고 있는 방법, 영향을 받는 방법 및 현재 조직에 미치는 영향을 확인할 수 있습니다. Microsoft 365 Defender는 공격을 방지하거나 중지하고 영향을 받는 사서함, 끝점 및 사용자 ID를 자체적으로 예방하거나 중지하는 자동 조치를 취합니다. 자세한 내용은 [Microsoft 365 Defender 개요를](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) 참조하세요.



다음 샘플 타임라인은 환경에 적합한 리소스가 있는 데 따라 다릅니다. 일부 검색 및 워크플로는 다른 검색 및 워크플로보다 학습 시간이 더 필요할 수 있습니다.

![Microsoft 365 Defender 파일럿 실행 샘플 타임라인](../../media/phase-diagrams/pilot-phases.png)

>[!IMPORTANT]
>최적의 결과를 얻기 위해 가능한 한 파일럿 지침을 따르세요.


### <a name="pilot-playbook-phases"></a>파일럿 플레이북 단계 

Microsoft 365 Defender 파일럿을 실행하는 네 가지 단계가 있습니다.

|단계 | 설명 | 
|:-------|:-----|
| [계획](mtp-pilot-plan.md)<br> ~ 1일| Microsoft 365 Defender 파일럿 프로젝트를 실행하기 전에 고려해야 할 내용을 알아보고 다음을 실행합니다. <br><br>- 범위 <br> - 사용 사례 <br>- 요구 사항 <br>- 테스트 계획 <br> - 성공 기준 <br> - Scorecard 
| [준비](mtp-evaluation.md) <br>~2일|  Microsoft 365 보안 센터에 액세스하여 Microsoft 365 Defender 파일럿 환경을 설정할 수 있습니다. 다음을 안내합니다.<br><br>- 관련자 식별 및 파일럿에 대한 사인오프 모색 <br> - 환경 고려 사항 <br>- Access <br>- Azure Active Directory 설정 <br> - 구성 순서 <br> - Microsoft 365 E5 평가판 등록 <br> - 도메인 구성 <br>- Microsoft 365 E5 라이선스 할당 <br> - 포털에서 설정 마법사 완료|
| [공격 시뮬레이션](mtp-pilot-simulate.md) <br>~2일| 공격을 시뮬레이트하기 위해 다음을 안내합니다.<br><br>- 테스트 환경 요구 사항 확인 <br>- 시뮬레이션 실행 <br>- 인시던트 조사 <br>- 인시던트 해결 
| [닫기 및 요약](mtp-pilot-close.md) <br>~ 1일| 프로세스가 끝났을 때 다음을 안내합니다.<br><br>- 최종 출력을 진행합니다.<br>- 이해 관계자에게 출력 표시 <br>- 피드백 제공 <br>- 다음 단계 수행 

## <a name="next-step"></a>다음 단계
|[계획 단계](mtp-pilot-plan.md) | Microsoft 365 Defender 파일럿 프로젝트 계획 
|:-------|:-----|
