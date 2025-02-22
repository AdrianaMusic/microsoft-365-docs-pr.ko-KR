---
title: Office 365용 Microsoft Defender 켜기 - SharePoint, OneDrive, & Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: 검색된 파일에 대한 경고를 설정하는 방법을 포함하여 SharePoint, OneDrive 및 Teams에 대해 ATP를 켜는 방법을 알아보습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 44d487810156d5de5ae152e08040e8dccd2a4ee0
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682600"
---
# <a name="turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>SharePoint, OneDrive 및 Microsoft Teams의 ATP 켜기

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

SharePoint, OneDrive 및 Microsoft Teams용 Office 365용 Microsoft Defender는 악성 파일을 부수적으로 공유하지 못하게 조직을 보호합니다. 자세한 내용은 [SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP를 참조하세요.](atp-for-spo-odb-and-teams.md)

이 문서에는 SharePoint, OneDrive 및 Microsoft Teams에 대해 ATP를 사용하도록 설정하고 구성하는 단계가 포함되어 있습니다.

## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용은 무엇인가요?

- <https://protection.office.com>에서 보안 및 준수 센터를 엽니다. **ATP** 안전한 첨부 파일 페이지로 직접 이동하기 위해 를 을 을 을 을 을(를) 를 를 를 <https://protection.office.com/safeattachmentv2> 클릭합니다.

- SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP를 켜기 위해  보안  및 준수 센터에서 조직 관리 또는 보안 관리자 역할 그룹의 & 해야 합니다. 자세한 내용은 [보안 및 준수 센터의 사용 권한](permissions-in-the-security-and-compliance-center.md)을 참조하세요.

- SharePoint Online PowerShell을 사용하여 사용자가 악성 파일을 다운로드하지 못하게 [](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-administrator--company-administrator) 방지하려면 Azure AD에서 전역 관리자 또는 [SharePoint](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#sharepoint-administrator) 관리자 역할의 구성원이 되거나 구성원이 되거나,

- 조직에 대해 감사 로깅이 사용하도록 설정되어 있는지 확인합니다. 자세한 내용은 [감사 로그 검색 설정 및 해제](../../compliance/turn-audit-log-search-on-or-off.md)를 참조하세요.

- 설정이 적용되는 데 최대 30분을 허용합니다.

## <a name="step-1-use-the-security--compliance-center-to-turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>1단계: 보안 & 준수 센터를 사용하여 SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP 켜기

1. 보안 & 준수 센터에서 **위협** 관리 \>  \> **정책 ATP** 안전한 첨부 파일로 이동한 후 전역 설정을 **클릭합니다.**

2. 전역 **설정** 플라이아웃이 나타나면 **SharePoint, OneDrive** 및 Microsoft Teams 설정에 대한 ATP 켜기 설정으로 이동합니다. 토글을 오른쪽 토글 켜기로 이동하여 ![ ](../../media/scc-toggle-on.png) SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP를 켜야 합니다.

   작업을 마쳤으면 **저장** 을 클릭합니다.

### <a name="use-exchange-online-powershell-to-turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Exchange Online PowerShell을 사용하여 SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP 켜기

PowerShell을 사용하여 SharePoint, OneDrive 및 Microsoft Teams에 대한 ATP를 켜고 [Exchange Online PowerShell에](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) 연결하고 다음 명령을 실행합니다.

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

구문과 매개 변수에 대한 자세한 내용은 [Set-AtpPolicyForO365를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365)

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>2단계: (권장) SharePoint Online PowerShell을 사용하여 사용자가 악성 파일을 다운로드하지 못하게 방지

기본적으로 사용자는 ATP에서 검색된 악성 파일을 열거나 이동, 복사 또는 공유할 수 없습니다. 그러나 악성 파일을 삭제하고 다운로드할 수 있습니다.

사용자가 악성 파일을 다운로드하지 못하게 방지하려면 [SharePoint Online PowerShell에](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) 연결하고 다음 명령을 실행합니다.

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**참고:**

- 이 설정은 사용자와 관리자 모두에 영향을 미치게 됩니다.
- 사람들은 여전히 악성 파일을 삭제할 수 있습니다.

구문과 매개 변수에 대한 자세한 내용은 [Set-SPOTenant를 참조하십시오.](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant)

## <a name="step-3-recommended-use-the-security--compliance-center-to-create-an-alert-policy-for-detected-files"></a>3단계(권장) 보안 & 준수 센터를 사용하여 검색된 파일에 대한 경고 정책 만들기

SharePoint, OneDrive 및 Microsoft Teams의 ATP에서 악성 파일을 감지할 때 관리자와 다른 관리자에게 알리는 경고 정책을 만들 수 있습니다. 경고에 대한 자세한 내용은 보안 및 준수 센터에서 활동 [& 참조합니다.](../../compliance/create-activity-alerts.md)

1. 보안 & 규정 준수 [센터에서](https://protection.office.com)경고  경고 정책으로 이동하거나 \>  를 열 수 <https://protection.office.com/alertpolicies> 있습니다.

2. 경고 정책 **페이지에서** 새 경고 **정책을 클릭합니다.**

3. 새 **경고 정책 마법사가** 플라이아웃에서 열립니다. 경고 **이름 페이지에서** 다음 설정을 구성합니다.

   - **이름**: 고유하고 설명적인 이름을 입력합니다. 예를 들어 라이브러리의 악성 파일입니다.
   - **설명:** 선택적 설명을 입력합니다. 예를 들어 SharePoint Online, OneDrive 또는 Microsoft Teams에서 악성 파일이 검색되면 관리자에게 고지합니다.
   - **심각도**: 기본값을 낮게 **선택된** 값으로 그대로 두거나 중간 또는 높음으로  **선택합니다.**
   - **범주 선택**: **위협 관리 선택.**

   작업을 마친 후 **다음** 을 클릭합니다.

4. 경고 설정 **만들기 페이지에서** 다음 설정을 구성합니다.

   - **경고할 사항: 활동은**: **파일에서 검색된 맬웨어 선택입니다.**
   - **경고를 트리거하는 방법:** 활동이 선택된 규칙과 일치할 때마다 **기본값을 그대로 떠야** 합니다.

   작업을 마친 후 **다음** 을 클릭합니다.

5. 받는 **사람 설정 페이지에서** 다음 설정을 구성합니다.

   - **전자 메일 알림 보내기:** 이 설정이 선택되어 있는지 확인 전자 **메일 받는** 사람 상자에서 악의적인 파일이 감지될 때 알림을 수신해야 하는 전역 관리자, 보안 관리자 또는 보안 독자를 하나 이상 선택합니다.
   - **일별 알림 제한:** 기본값을 **제한하지 않습니다.**

   작업을 마친 후 **다음** 을 클릭합니다.

6. 설정 **검토 페이지에서** 설정을 검토하고 모든  섹션에서 편집을 클릭하여 변경합니다.

   정책을  바로 켜시겠습니까? 섹션에서 기본값인 **Yes를** 그대로 두고 바로 켜세요.

   완료되면 마쳤습니다. 

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>보안 & 준수 PowerShell을 사용하여 검색된 파일에 대한 경고 정책 만들기

PowerShell을 사용하여 이전 섹션에 설명된 동일한 경고 정책을 만들 수 있는 경우 보안 & 준수 센터 [PowerShell에](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell) 연결하고 다음 명령을 실행합니다.

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**참고:** 기본 _심각도 값은_ 낮습니다. Medium 또는 High를 지정하기 위해 _명령에 심각도_ 매개 변수와 값을 포함합니다.

구문과 매개 변수에 대한 자세한 내용은 [New-ActivityAlert를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/new-activityalert)

### <a name="how-do-you-know-these-procedures-worked"></a>이 절차가 제대로 수행되었는지 어떻게 확인하나요?

- SharePoint, OneDrive 및 Microsoft Teams에 대해 ATP가 설정되어 있는지 확인하기 위해 다음 단계 중 하나를 사용하세요.

  - 보안 [&](https://protection.office.com)준수 센터에서 위협 관리  정책 ATP 안전한 첨부 파일로 이동하여 전역 설정을 선택하고 \>  \>  **SharePoint, OneDrive** 및 Microsoft Teams 설정에 대한 ATP 켜기 값을 확인합니다.

  - Exchange Online PowerShell에서 다음 명령을 실행하여 속성 설정을 검증합니다.

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    구문과 매개 변수에 대한 자세한 내용은 [Get-AtpPolicyForO365를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/get-atppolicyforo365)

- 사용자가 악성 파일을 다운로드하지 못하게 차단하는지 확인하려면 SharePoint Online PowerShell을 열고 다음 명령을 실행하여 속성 값을 검증합니다.

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  구문과 매개 변수에 대한 자세한 내용은 [Get-SPOTenant를 참조하십시오.](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant)

- 검색된 파일에 대한 경고 정책이 성공적으로 구성되지 않은지 확인하려면 다음 단계를 수행합니다.

  - 보안 & 준수 센터에서 경고 경고  정책으로 이동하여 경고 정책을 선택하고 설정을 \>  \> 확인합니다.

  - 보안 & 준수 센터 PowerShell에서 경고 정책의 이름으로 바꾸고 다음 명령을 실행하고 속성 \<AlertPolicyName\> 값을 검증합니다.

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    구문과 매개 변수에 대한 자세한 내용은 [Get-ActivityAlert를 참조하십시오.](https://docs.microsoft.com/powershell/module/exchange/get-activityalert)

- 위협 방지 [상태 보고서를](view-email-security-reports.md#threat-protection-status-report) 사용하여 SharePoint, OneDrive 및 Microsoft Teams에서 검색된 파일에 대한 정보를 볼 수 있습니다. 특히 콘텐츠 맬웨어 보기를 사용하여 데이터 **\> 보기를 사용할 수** 있습니다.
