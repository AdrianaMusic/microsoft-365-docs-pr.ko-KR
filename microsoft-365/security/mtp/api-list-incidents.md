---
title: Microsoft 365 Defender의 목록 인시던트 API
description: Microsoft 365 Defender에서 인시던트 API를 나열하는 방법에 대해 자세히 알아보기
keywords: 목록, 인시던트, 인시던트, api
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
ms.openlocfilehash: 13508d3ad9d61797517ccb55a27152883947843a
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719431"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>Microsoft 365 Defender의 목록 인시던트 API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**적용 대상:**

- Microsoft 365 Defender

> [!IMPORTANT]
> 일부 정보는 상업적으로 출시되기 전에 상당수 수정될 수 있는 미리 판매된 제품과 관련이 있습니다. Microsoft makes no warranties, express or implied, with respect to the information provided here.


## <a name="api-description"></a>API 설명

목록 인시던트 API를 사용하면 인시던트들을 정렬하여 정보를 토대한 사이버 보안 대응을 만들 수 있습니다. 네트워크에서 플래그가 지정된 인시던트 컬렉션을 환경 보존 정책에 지정한 시간 범위 내에 노출합니다. 가장 최근 인시던트가 목록 맨 위에 표시됩니다. 각 인시던트에는 관련 경고 및 관련 엔터티의 배열이 포함되어 있습니다.

API는 다음 **OData 연산자를** 지원합니다.

- `$filter``lastUpdateTime`의 `createdTime` , `status` , 및 `assignedTo` 속성
- `$top`의 **최대값이 100인 경우**
- `$skip`

## <a name="limitations"></a>제한 사항

1. 최대 페이지 크기는 **인시던트 100개입니다.**
2. 최대 요청 속도는 분당 **50통,** 시간당 **1500통입니다.**

## <a name="permissions"></a>권한

이 API를 호출하려면 다음 권한 중 하나를 필요합니다. 사용 권한을 선택하는 방법을 포함하여 자세한 내용은 [Microsoft 365 Defender API 액세스](api-access.md) 참조

사용 권한 유형 | 사용 권한 | 사용 권한 표시 이름
-|-|-
응용 프로그램 | Incident.Read.All | 모든 인시던트 읽기
응용 프로그램 | Incident.ReadWrite.All | 모든 인시던트 읽기 및 쓰기
위임(직장 또는 학교 계정) | Incident.Read | 인시던트 읽기
위임(직장 또는 학교 계정) | Incident.ReadWrite | 인시던트 읽기 및 쓰기

> [!Note]
> 사용자 자격 증명을 사용하여 토큰을 얻을 때:
>
> - 사용자에게 포털에서 인시던트에 대한 보기 권한이 필요합니다.
> - 응답에는 사용자가 노출하는 인시던트만 포함됩니다.

## <a name="http-request"></a>HTTP 요청

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>요청 헤더

이름 | 유형 | 설명
-|-|-
권한 부여 | 문자열 | Bearer {token}. **필수**


## <a name="request-body"></a>요청 본문

없음

## <a name="response"></a>응답

성공하면 이 메서드는 응답 본문의 인시던트 목록과 `200 OK` 인시던트 목록을 반환합니다. [](api-incident.md)

## <a name="schema-mapping"></a>Schema mapping

### <a name="incident-metadata"></a>인시던트 메타데이터

필드 이름 | 설명 | 예제 값
-|-|-
incidentId | 인시던트에 대한 고유 식별자 | 924565
redirectIncidentId | 인시던트가 인시던트 처리 논리의 일부로 다른 인시던트와 함께 그룹화되는 경우만 채워야 합니다. | 924569
incidentName | 모든 인시던트에 사용할 수 있는 문자열 값입니다. | 랜섬웨어 활동
createdTime | 인시던트가 처음 만들어진 시간입니다. | 2020-09-06T14:46:57.073333Z
lastUpdateTime | 인시던트가 백엔드에서 마지막으로 업데이트된 시간입니다.<br /><br /> 이 필드는 인시던트가 검색된 시간 범위에 대한 요청 매개 변수를 설정할 때 사용할 수 있습니다. | 2020-09-06T14:46:57.29Z
assignedTo | 인시던트 소유자 또는 소유자가 할당되지 않은 경우 *null입니다.* | secop2@contoso.com
classification | 인시던트에 대한 사양입니다. 속성 값은 알 수 *없음,* *FalsePositive,* *TruePositive입니다.* | 알 수 없음
determination | 인시던트의 결정 속성 값은 *NotAvailable,* *Apt,* *Malware,* *SecurityPersonnel*, *Security Malwareg,* *UnwantedSoftware*, *Other* | NotAvailable
status | 인시던트(활성 또는 해결된 인시던트)를 *분류합니다.* 인시던트에 대한 대응을 구성하고 관리하는 데 도움이 될 수 있습니다. | 활성
심각도 | 자산에 미칠 수 있는 영향을 나타냅니다. 심각도가 높을수록 영향이 커집니다. 일반적으로 심각도가 높은 항목은 가장 즉각적인 주의가 필요합니다.<br /><br />정보, 낮음, *보통 및 *높음* 값 중 하나 | 보통
tags | 인시던트와 연결된 사용자 지정 태그의 배열입니다. 예를 들어 인시던트 그룹에 공통적인 특성이 있는 플래그를 지정합니다. | \[\]
alerts | 인시던트와 관련된 모든 경고와 심각도, 경고에 관련된 엔터티, 경고 원본 등의 기타 정보를 포함하는 배열입니다. | \[\] (아래 경고 필드에 대한 세부 정보 참조)

### <a name="alerts-metadata"></a>경고 메타데이터

필드 이름 | 설명 | 예제 값
-|-|-
alertId | 경고를 나타내는 고유 식별자 | caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC
incidentId | 이 경고가 연결된 문제를 나타내는 고유 식별자입니다. | 924565
serviceSource | 경고가 시작된 서비스(예: Endpoint용 Microsoft Defender, Microsoft Cloud App Security, ID용 Microsoft Defender 또는 Office 365용 Microsoft Defender) | MicrosoftCloudAppSecurity
creationTime | 알림을 처음 만든 시간입니다. | 2020-09-06T14:46:55.7182276Z
lastUpdatedTime | 백엔드에서 경고가 마지막으로 업데이트된 시간입니다. | 2020-09-06T14:46:57.243333Z
resolvedTime | 경고가 해결된 시간입니다. | 2020-09-10T05:22:59Z
firstActivity | 처음에 백엔드에서 활동이 업데이트된 것으로 경고가 보고된 시간입니다.| 2020-09-04T05:22:59Z
title | 각 경고에 사용할 수 있는 간단한 식별 문자열 값입니다. | 랜섬웨어 활동
설명 | 각 경고를 설명하는 문자열 값입니다. | 사용자 테스트 사용자2(testUser2@contoso.com)가 확장명을 여러 개 사용하여 99개 파일을 *조작했습니다.* 이는 비정상적인 파일 조작 수로, 잠재적인 랜섬웨어 공격을 나타내는 것입니다.
category | 킬체인을 따라 공격이 진행된 거리의 시각적 및 숫자 보기입니다. [MITRE ATT&CK™ 정렬됩니다.](https://attack.mitre.org/) | 영향
status | 경고를 새로, 활성 또는 해결된 *경고로 분류합니다.* 경고에 대한 응답을 구성하고 관리하는 데 도움이 될 수 있습니다. | 신규
심각도 | 자산에 미칠 수 있는 영향을 나타냅니다. 심각도가 높을수록 영향이 커집니다. 일반적으로 심각도가 높은 항목은 가장 즉각적인 주의가 필요합니다.<br>정보, 낮음, *보통 및 *높음* 값 중 하나 | 보통
investigationId | 이 경고에 의해 트리거된 자동화된 조사 ID입니다. | 1234
investigationState | 조사의 현재 상태에 대한 정보입니다. 다음 값 중 하나: *Unknown*, *Terminated*, *SuccessfullyRemediated*, *Benign*, *Failed*, *PartiallyRemediated*, *Running*, *PendingApproval*, *PendingResource*, *PartiallyInvestigated*, *TerminatedByUser*, *TerminatedBySystem*, *Queued*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *SuppressedAlert*. | UnsupportedAlertType
classification | 인시던트에 대한 사양입니다. 속성 값은 알 수 *없음,* *FalsePositive,* *TruePositive* 또는 *null입니다.* | 알 수 없음
determination | 인시던트의 결정 속성 값은 *NotAvailable,* *Apt,* *Malware*, *SecurityPersonnel*, *Security Malware, SecuritySoftware,* *Other* 또는 *null입니다.*  | Apt
assignedTo | 인시던트 소유자 또는 소유자가 할당되지 않은 경우 *null입니다.* | secop2@contoso.com
actorName | 이 경고와 연결된 활동 그룹(있는 경우)입니다. | BORON
threatFamilyName | 이 경고와 연결된 위협 패밀리입니다. | null
mitreTechniques | [MITRE ATT 및 CK 2013](https://attack.mitre.org/)프레임워크에&공격 ™ 기술입니다. | \[\]
장치 | 인시던트와 관련된 경고가 전송된 모든 장치입니다. | \[\] (아래 엔터티 필드에 대한 세부 정보 참조)

### <a name="device-format"></a>디바이스 형식

필드 이름 | 설명 | 예제 값
-|-|-
DeviceId | Microsoft Defender ATP에 지정된 장치 ID입니다. | 24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId |  Azure Active Directory에 지정된 장치 [ID입니다.](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) 도메인에 가입된 디바이스에서만 사용할 수 있습니다. | null
deviceDnsName | 디바이스의 정식 도메인 이름입니다. | user5cx.middleeast.corp.contoso.com
osPlatform | 디바이스가 실행 중인 OS 플랫폼입니다.| WindowsServer2016
osBuild | 디바이스가 실행 중인 OS의 빌드 버전입니다. | 14393
rbacGroupName | 장치와 [연결된](https://docs.microsoft.com/azure/role-based-access-control/overview) RBAC(역할 기반 액세스 제어) 그룹입니다. | WDATP-Ring0
firstSeen | 디바이스를 처음 본 시간입니다. | 2020-02-06T14:16:01.9330135Z
healthStatus | 장치의 상태입니다. | 활성
riskScore | 장치에 대한 위험 점수입니다. | 높음
엔터티 | 지정한 경고의 일부로 식별되거나 이와 관련된 모든 엔터티입니다. | \[\] (아래 엔터티 필드에 대한 세부 정보 참조)

### <a name="entity-format"></a>엔터티 형식

필드 이름 | 설명 | 예제 값
-|-|-
entityType | 지정한 경고의 일부로 식별되거나 이와 관련된 엔터티입니다.<br>속성 값은 *사용자,* *Ip,* *URL,* *파일,* *프로세스,* *MailBox,* *MailMessage,* *MailCluster,* *레지스트리입니다.* | 사용자
sha1 | entityType이 File인 경우 *사용할 수 있습니다.*<br>파일 또는 프로세스와 관련된 경고에 대한 파일 해시입니다. | 5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd
sha256 | entityType이 File인 경우 *사용할 수 있습니다.*<br>파일 또는 프로세스와 관련된 경고에 대한 파일 해시입니다. | 28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
fileName | entityType이 File인 경우 *사용할 수 있습니다.*<br>파일 또는 프로세스와 연결된 경고의 파일 이름 | Detector.UnitTests.dll
filePath | entityType이 File인 경우 *사용할 수 있습니다.*<br>파일 또는 프로세스와 연결된 경고의 파일 경로 | C: \\ \agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId | entityType이 Process인 경우 *사용할 수 있습니다.* | 24348
processCommandLine | entityType이 Process인 경우 *사용할 수 있습니다.* | "파일을 다운로드할 \_ 준비가1911150169.exe"
processCreationTime | entityType이 Process인 경우 *사용할 수 있습니다.* | 2020-07-18T03:25:38.5269993Z
parentProcessId | entityType이 Process인 경우 *사용할 수 있습니다.* | 16840
parentProcessCreationTime | entityType이 Process인 경우 *사용할 수 있습니다.* | 2020-07-18T02:12:32.8616797Z
ipAddress | entityType이 Ip인 경우 *사용할 수 있습니다.* <br>악성 네트워크 대상에 대한 통신과 같은 네트워크 이벤트와 관련된 경고의 IP *주소입니다.* | 62.216.203.204
url | entityType이 Url인 경우 *사용할 수 있습니다.* <br>악성 네트워크 대상에 대한 통신과 같은 네트워크 이벤트와 관련된 *경고의 URL입니다.* | down.esales360.cn
accountName | entityType이 User인 경우 *사용할 수 있습니다.* | testUser2
domainName | entityType이 User인 경우 *사용할 수 있습니다.* | europe.corp.contoso
userSid | entityType이 User인 경우 *사용할 수 있습니다.* | S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId | entityType이 User인 경우 *사용할 수 있습니다.* | fc8f7484-f813-4db2-afab-bc1507913fb6
userPrincipalName | entityType이 *User* / *MailBox* / *MailMessage인* 경우 사용할 수 있습니다. | testUser2@contoso.com
mailboxDisplayName | entityType이 *MailBox인 경우 사용할 수 있습니다.* | test User2
mailboxAddress | entityType이 *User* / *MailBox* / *MailMessage인* 경우 사용할 수 있습니다. | testUser2@contoso.com
clusterBy | entityType이 *MailCluster인 경우 사용할 수 있습니다.* | 제목; P2SenderDomain; ContentType
보낸 사람 | entityType이 *User* / *MailBox* / *MailMessage인* 경우 사용할 수 있습니다. | user.abc@mail.contoso.co.in
받는 사람 | entityType이 *MailMessage인 경우 사용할 수 있습니다.* | testUser2@contoso.com
subject | entityType이 *MailMessage인 경우 사용할 수 있습니다.* | \[외부 \] 주의
deliveryAction | entityType이 *MailMessage인 경우 사용할 수 있습니다.* | 배달
securityGroupId | entityType이 *SecurityGroup인 경우 사용할 수 있습니다.* | 301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName | entityType이 *SecurityGroup인 경우 사용할 수 있습니다.* | 네트워크 구성 연산자
registryHive | entityType이 *레지스트리인 경우 사용할 수 있습니다.* | HKEY \_ 로컬 \_ 컴퓨터 |
registryKey | entityType이 *레지스트리인 경우 사용할 수 있습니다.* | SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType | entityType이 *레지스트리인 경우 사용할 수 있습니다.* | 문자열
registryValue | entityType이 *레지스트리인 경우 사용할 수 있습니다.* | 31-00-00-00
deviceId | 엔터티와 관련된 장치의 ID(있는 경우)입니다. | 986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>예제

**요청**

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

**응답**

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>관련 문서

- [Microsoft 365 Defender API 액세스](api-access.md)
- [API 제한 및 라이선싱에 대해 자세히](api-terms.md)
- [오류 코드 이해](api-error-codes.md)
- [인시던트 개요](incidents-overview.md)
- [인시던트 API](api-incident.md)
- [인시던트 업데이트 API](api-update-incidents.md)
