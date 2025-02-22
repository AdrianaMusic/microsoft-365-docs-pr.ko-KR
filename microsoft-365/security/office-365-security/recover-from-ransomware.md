---
title: 랜섬웨어 공격으로부터 복구
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.article: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Microsoft 365 관리자는 랜섬웨어 공격으로부터 복구하는 방법을 배울 수 있습니다.
ms.openlocfilehash: ad3f044e338abeb56046538bdda8df7b8510be0e
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615903"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Microsoft 365의 랜섬웨어 공격으로부터 복구

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


조직을 보호하기 위해 모든 예방 조치를 취하는 경우에도 랜섬웨어 공격의 피해자가 될 [수](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware) 있습니다. 랜섬웨어는 대기업에 있으며 공격은 매우 정교합니다.

이 문서의 단계는 데이터를 복구하고 내부 감염 확산을 중지할 수 있는 최상의 기회를 제공합니다. 시작하기 전에 다음 항목을 고려하세요.

- 대금을 지불하면 파일에 대한 액세스 권한이 반환된다고 보장할 수 없습니다. 실제로 대가를 지불하면 더 많은 랜섬웨어의 대상이 될 수 있습니다.

  이미 결제했지만 공격자 솔루션을 사용하지 않고 복구한 경우 은행에 문의하여 거래를 차단할 수 있는지 문의합니다.

  또한 랜섬웨어 공격을 법 집행 기관, 사기 보고 웹 사이트 및 Microsoft에 보고하는 것이 좋습니다.

- 공격과 그 결과에 빠르게 대응하는 것이 중요합니다. 대기 시간이 길면 영향을 받는 데이터를 복구할 가능성이 낮아질 수 있습니다.

## <a name="step-1-verify-your-backups"></a>1단계: 백업 확인

오프라인 백업이 있는 경우 환경에서 랜섬웨어  페이로드(맬웨어)를 제거한 후 암호화된 데이터를 복원할 수 있습니다.

백업이 없는 경우 또는 백업이 랜섬웨어의 영향을 받은 경우 이 단계를 건너뛸 수 있습니다.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>2단계: Exchange ActiveSync 및 OneDrive 동기화를 사용하지 않도록 설정

여기서 핵심적인 점은 랜섬웨어에 의해 데이터 암호화 확산을 중지하는 것입니다.

전자 메일이 랜섬웨어 암호화의 대상으로 의심되는 경우 사서함에 대한 사용자 액세스를 일시적으로 사용하지 않도록 설정하십시오. Exchange ActiveSync Exchange Online 사서함 간에 데이터를 동기화할 수 있습니다.

사서함에 Exchange ActiveSync 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 Exchange Online에서 사용자에 대해 Exchange ActiveSync 사용하지 않도록 [설정하는 방법을 참조하세요.](https://support.microsoft.com/help/2795303)

다른 유형의 사서함 액세스를 사용하지 않도록 설정하는 경우 다음을 참조합니다.

- [사서함에 대해 MAPI를 사용하도록 설정하거나 사용하지 않도록 설정](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi)

- [사용자에 대해 POP3 또는 IMAP4 액세스 사용 또는 사용 안 하도록 설정](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

OneDrive 동기화를 Pausing하면 잠재적으로 감염된 장치에 의해 클라우드 데이터가 업데이트되지 못하도록 보호할 수 있습니다. 자세한 내용은 [OneDrive에서 동기화를](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e)일시 중지하고 다시 시작하는 방법을 참조하세요.

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>3단계: 영향을 받는 장치에서 맬웨어 제거

의심되는 모든 컴퓨터 및 장치에서 전체 최신 바이러스 백신 검색을 실행하여 랜섬웨어와 연결된 페이로드를 검색하고 제거합니다.

데이터를 동기화하는 장치 또는 매핑된 네트워크 드라이브의 대상을 검색하는 것을 잊지 마세요.

.에서 [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) 또는 (이전 클라이언트의 [경우)](https://www.microsoft.com/download/details.aspx?id=5201)Microsoft Security Essentials.

랜섬웨어 또는 맬웨어를 제거하는 데 도움이 되는 [MSRT(악성](https://www.microsoft.com/download/details.aspx?id=9905)소프트웨어 제거 도구)를 대신 사용할 수 있습니다.

이러한 옵션이 작동하지 않는 경우 오프라인으로 전환하거나 Windows Defender 맬웨어 검색 및 제거 문제를 [해결할 수 있습니다.](https://support.microsoft.com/help/4466982) [](https://support.microsoft.com/help/17466)

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>4단계: 정리된 컴퓨터 또는 장치에서 파일 복구

사용자 환경에서 랜섬웨어 페이로드를 제거하는 이전 단계를 완료한 후(랜섬웨어가 파일을 암호화하거나 제거하지 못하게 하려는 [](https://support.microsoft.com/help/17128) 경우) Windows 10 및 Windows 8.1의 파일 기록 또는 Windows 7의 시스템 보호를 사용하여 로컬 파일 및 폴더를 복구할 수 있습니다.

**참고**:

- 일부 랜섬웨어는 또한 백업 버전을 암호화하거나 삭제하기 때문에 파일 기록 또는 시스템 보호를 사용하여 파일을 복원할 수 없습니다. 이 경우 다음 섹션에 설명된 바와 같이 랜섬웨어 또는 OneDrive의 영향을 받지 않는 외부 드라이브 또는 디바이스에서 백업을 사용해야 합니다.

- 폴더가 OneDrive와 동기화된 경우 최신 버전의 Windows를 사용하지 않는 경우 파일 기록을 사용하는 데 몇 가지 제한이 있을 수 있습니다.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>5단계: 비즈니스용 OneDrive에서 파일 복구

비즈니스용 OneDrive에서 파일 복원을 사용하면 지난 30일 이내에 전체 OneDrive를 이전 시점으로 복원할 수 있습니다. 자세한 내용은 [OneDrive 복원을 참조하세요.](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="step-6-recover-deleted-email"></a>6단계: 삭제된 전자 메일 복구

드물지만 랜섬웨어가 모든 전자 메일을 삭제한 경우 삭제된 항목을 복구할 수 있습니다. 자세한 내용은 다음을 참조하시기 바랍니다.

- [사용자의 사서함에서 삭제된 메시지 복구](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Windows용 Outlook에서 삭제된 항목 복구](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>7단계: Exchange ActiveSync 및 OneDrive 동기화 다시 사용하도록 설정

컴퓨터와 장치를 정리하고 데이터를 복구한 후 이전에 [2단계에서](#step-2-disable-exchange-activesync-and-onedrive-sync)사용하지 않도록 Exchange ActiveSync 및 OneDrive 동기화를 다시 사용하도록 설정할 수 있습니다.

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>8단계(선택 사항): 특정 파일 확장명에 대한 OneDrive 동기화 차단

복구한 후 비즈니스용 OneDrive 클라이언트가 이 랜섬웨어의 영향을 받은 파일 형식을 동기화하지 못하게 할 수 있습니다. 자세한 내용은 [Set-SPOTenantSyncClientRestriction을 참조하세요.](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>공격 보고

### <a name="contact-law-enforcement"></a>담당자 법 집행

해당 지역의 법 집행 기관에 문의해야 합니다. 예를 들어 미국에 있는 경우 [FBI](https://www.fbi.gov/contact-us/field)현지 사무실 [IC3](http://www.ic3.gov/complaint/default.aspx) 또는 비밀 서비스에 [문의할 수 있습니다.](http://www.secretservice.gov/)

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>국가의 사기 보고 웹 사이트에 보고서 제출

사기 보고 웹 사이트는 사기를 방지하고 방지하는 방법에 대한 정보를 제공합니다. 또한 사기를 당했다고 보고하는 메커니즘도 제공합니다.

- 오스트레일리아: [SCAMwatch](http://www.scamwatch.gov.au/)

- 캐나다: [캐나다의 사기 방지 센터](http://www.antifraudcentre-centreantifraude.ca/)

- 프랑스: [Agence nationale de la sécurité des systémes d'information](http://www.ssi.gouv.fr/)

- 독일: [der Informationstechnik의 번들어amt für Sicherheit](https://www.bsi.bund.de/DE/Home/home_node.html)

- 아일랜드: [가르다 신오크라나](http://www.garda.ie/)

- 뉴질랜드: [소비자 사기](http://www.consumeraffairs.govt.nz/scams)

- 영국: [작업 사기](http://www.actionfraud.police.uk/)

- 미국: [On Guard Online](http://www.onguardonline.gov/)

해당 국가가 목록에 없는 경우 현지 또는 연방 법 집행 기관에 요청합니다.

### <a name="submit-email-messages-to-microsoft"></a>Microsoft에 전자 메일 메시지 제출

여러 방법 중 하나를 사용하여 랜섬웨어가 포함된 피싱 메시지를 보고할 수 있습니다. 자세한 내용은 [Microsoft에 메시지와 파일 보고](report-junk-email-messages-to-microsoft.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [랜섬웨어](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware)

- [랜섬웨어 응답 - 지불할지 또는 지불하지 않을 것인가?](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)

- [Norsk 연산은 투명성을 통해 랜섬웨어 공격에 대응합니다.](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)

- [OneDrive에서 랜섬웨어 검색 및 파일 복구](https://support.microsoft.com/office/0d90ec50-6bfd-40f4-acc7-b8c12c73637f)

- [Microsoft 보안 인텔리전스 보고서](https://www.microsoft.com/securityinsights/)

- [Office 파일에서 매크로 사용 또는 사용 안 하도록 설정](https://support.microsoft.com/office/12b036fd-d140-4e74-b45e-16fed1a7e5c6)

- [EOP 및 Office 365용 Microsoft Defender 보안에 대한 권장 설정](recommended-settings-for-eop-and-office365-atp.md)

- [업그레이드 가치가 있는 업그레이드: Windows 10의 차세대 보안은 2017년 랜섬웨어 발생에 대해 탄력적인 업그레이드를 증명합니다.](https://www.microsoft.com/security/blog/2018/01/10/a-worthy-upgrade-next-gen-security-on-windows-10-proves-resilient-against-ransomware-outbreaks-in-2017/)

- [No mas, Samas: What's in this ransomware's modus operandi?](https://www.microsoft.com/security/blog/2016/03/17/no-mas-samas-whats-in-this-ransomwares-modus-operandi/)

- [잠긴 맬웨어, 방지할 수 있는 다행](https://www.microsoft.com/security/blog/2016/02/24/locky-malware-lucky-to-avoid-it/)

- [MSRT 2016년 7월: Cerber 랜섬웨어](https://www.microsoft.com/security/blog/2016/07/12/msrt-july-2016-cerber-ransomware/)

- [Cerberus와 같은 Cerber 랜섬웨어의 세 가지 헤드](https://www.microsoft.com/security/blog/2016/03/09/the-three-heads-of-the-cerberus-like-cerber-ransomware/)

- [(the) Da Vinci 코드의 영향을 Troldesh 랜섬웨어](https://www.microsoft.com/security/blog/2016/07/13/troldesh-ransomware-influenced-by-the-da-vinci-code/)
