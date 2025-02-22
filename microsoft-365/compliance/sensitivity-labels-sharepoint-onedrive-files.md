---
title: SharePoint 및 OneDrive에서 Office 파일에 대한 민감도 레이블 사용
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 관리자는 SharePoint 및 OneDrive에서 Word, Excel 및 PowerPoint 파일에 대해 민감도 레이블 지원을 사용하도록 설정할 수 있습니다.
ms.openlocfilehash: f930c31eef35282a5be6487e981d65275add4d5b
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620601"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>SharePoint 및 OneDrive에서 Office 파일에 대한 민감도 레이블 사용

>*[보안 및 규정 준수를 위한 Microsoft 365 라이선싱 지침](https://aka.ms/ComplianceSD).*

사용자가 웹에서 Office에서 민감도 레이블을 적용할 수 있도록 SharePoint [](sensitivity-labels.md) 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정 이 기능을 사용하도록 설정하면 레이블을 적용할 수 있도록 리본 메뉴에 민감도 단추가 표시되고 상태 표시줄에 적용된 레이블 이름이 표시됩니다.  

또한 이 기능을 사용하도록 설정하면 SharePoint 및 OneDrive에서 민감도 레이블을 사용하여 암호화된 파일의 콘텐츠를 처리할 수 있습니다. 레이블은 웹용 Office 또는 Office 데스크톱 앱에서 적용하고 SharePoint 및 OneDrive에 업로드하거나 저장할 수 있습니다. 이 기능을 사용하도록 설정하기 전까지 이러한 서비스는 암호화된 파일을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 데이터 손실 방지, 검색 및 기타 공동 작업 기능이 이러한 파일에 대해 작동하지 않습니다.

SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정한 후 클라우드 기반 키로 암호화를 적용하고 이중 키 암호화를 사용하지 않는 민감도 레이블이 있는 새 파일 및 변경된 파일의 경우 [:](double-key-encryption.md)

- Word, Excel 및 PowerPoint 파일의 경우 SharePoint 및 OneDrive는 레이블을 인식하고 이제 암호화된 파일의 내용을 처리합니다.

- 사용자가 SharePoint 또는 OneDrive에서 이러한 파일을 다운로드하거나 액세스할 때 민감도 레이블과 레이블의 암호화 설정이 적용되고 저장되는 모든 위치에 파일에 유지됩니다. 레이블만 사용하여 문서를 보호하기 위한 사용자 지침을 제공해야 합니다. 자세한 내용은 [IRM(정보 권한 관리) 옵션 및 민감도 레이블을 참조하세요.](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels)

- 사용자가 레이블이 지정되고 암호화된 파일을 SharePoint 또는 OneDrive에 업로드하는 경우 해당 파일에 대한 보기 권한 이상이 있어야 합니다. 예를 들어 SharePoint 외부에서 파일을 열 수 있습니다. 최소 사용권이 없는 경우 업로드는 성공하지만 서비스에서 레이블을 인식하지 못하고 파일 콘텐츠를 처리하지 못합니다.

- 웹용 Office(Word, Excel, PowerPoint)를 사용하여 암호화를 적용하는 민감도 레이블이 있는 Office 파일을 열고 편집할 수 있습니다. 암호화와 함께 할당된 사용 권한이 적용됩니다. 이러한 문서에 자동 [레이블 지정을](apply-sensitivity-label-automatically.md) 사용할 수 있습니다.

- 외부 사용자는 게스트 계정을 사용하여 암호화 레이블이 지정된 문서에 액세스할 수 있습니다. 자세한 내용은 외부 사용자 및 레이블이 붙은 콘텐츠에 [대한 지원(지원)을 참조하세요.](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content) 

- Office 365 eDiscovery는 이러한 파일에 대한 전체 텍스트 검색을 지원하고 DLP(데이터 손실 방지) 정책은 이러한 파일의 콘텐츠를 지원합니다.

> [!NOTE]
> 암호화가 프레미스 키("자체 키 보유"나 HYOK라고도 하는 키 관리 토폴로지)를 사용하여 적용한 경우 또는 이중 키 암호화를 사용하여 파일 콘텐츠를 처리하기 위한 서비스 동작은 변경되지 않습니다. [](double-key-encryption.md) 따라서 이러한 파일의 경우 공동 작업, eDiscovery, 데이터 손실 방지, 검색 및 기타 공동 작업 기능이 작동하지 않습니다.
>
> 또한 SharePoint 및 OneDrive 동작은 단일 Azure 기반 키를 사용하여 암호화로 레이블이 지정되는 이러한 위치의 기존 파일에 대해 변경되지 않습니다. SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정한 후 이러한 파일을 새로운 기능을 사용하려면 파일을 다시 다운로드하여 업로드하거나 편집해야 합니다.

SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정하면 SharePoint 및 OneDrive의 문서에 적용되는 민감도 레이블을 모니터링하는 데 세 가지 새로운 감사 이벤트를 사용할 수 있습니다. [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities)
- **파일에 적용된 민감도 레이블**
- **파일에 변경된 민감도 레이블을 적용**
- **파일에서 제거된 민감도 레이블**

다음 비디오(오디오 없음)를 시청하여 새로운 기능을 사용할 수 있습니다.

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

언제든지 SharePoint 및 OneDrive(옵트아웃)에서 Office 파일에[](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)대한 민감도 레이블을 사용하지 않도록 설정할 수 있습니다.

현재 SharePoint IRM(정보 권한 관리)을 사용하여 SharePoint의 문서를 보호하는 경우 이 페이지에서 [SharePoint IRM(정보](#sharepoint-information-rights-management-irm-and-sensitivity-labels) 권한 관리) 및 민감도 레이블 섹션을 확인하십시오. 

## <a name="requirements"></a>요구 사항

이러한 새로운 기능은 민감도 [레이블에만 작동됩니다.](sensitivity-labels.md) 현재 Azure Information Protection 레이블이 있는 경우 먼저 민감도 레이블로 마이그레이션하여 업로드하는 새 파일에 대해 이러한 기능을 사용하도록 설정할 수 있습니다. 자세한 내용은 Azure Information Protection 레이블을 통합 민감도 [레이블로 마이그레이션하는 방법을 참조하세요.](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)

Windows에서는 OneDrive 동기화 앱 버전 19.002.0121.0008 이상, Mac에서는 버전 19.002.0107.0008 이상을 사용하세요. 두 버전 모두 2019년 1월 28일 릴리스된 후 현재 모든 링에 릴리스됩니다. 자세한 내용은 [OneDrive 릴리스 정보를 참조하세요.](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0) SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정하면 이전 버전의 동기화 앱을 실행한 사용자에게 업데이트하라는 메시지가 표시됩니다.

## <a name="limitations"></a>제한 사항

- SharePoint 및 OneDrive는 Azure Information Protection 레이블을 사용하여 이미 암호화한 기존 파일에 민감도 레이블을 자동으로 적용하지 않습니다. 대신 SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정한 후에 기능이 작동하려면 다음 작업을 완료합니다.
    
    1. Azure Information [Protection](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) 레이블을 민감도 레이블로 마이그레이션하고 [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) Microsoft 365 규정 준수 센터 또는 동등한 레이블 관리 센터에서 게시해야 합니다.
    
    2. 파일을 다운로드한 다음 SharePoint에 업로드합니다.

- 암호화를 적용한 레이블에 다음과 같은 암호화 구성이 있는 경우 SharePoint 및 OneDrive에서 암호화된 파일을 [처리하지 못합니다.](encryption-sensitivity-labels.md#configure-encryption-settings)
    - **사용자가 레이블 및** **Word, PowerPoint** 및 Excel의 확인란을 적용할 때 사용 권한을 할당할 수 있도록 사용자에게 사용 권한을 지정하라는 메시지를 표시합니다. 이 설정을 "사용자 정의 사용 권한"이라고도 합니다.
    - **콘텐츠에 대한 사용자 액세스가 만료되면** 사용 안 하도록 **설정됩니다.**
    - **이중 키 암호화가** 선택되어 있습니다.
    
    이러한 암호화 구성이 있는 레이블의 경우 레이블은 웹용 Office의 사용자에게 표시되지 않습니다. 또한 이러한 암호화 설정이 이미 있는 레이블이 지정되어 있는 문서에는 새 기능을 사용할 수 없습니다. 예를 들어 이러한 문서는 업데이트된 경우에도 검색 결과에 반환되지 않습니다.

- 사용자에게 편집 권한을 부여하는 암호화된 문서의 경우 Office 앱의 웹 버전에서는 복사를 차단할 수 없습니다.

- Azure Information Protection 문서 추적 사이트는 지원되지 않습니다.

- Office 데스크톱 앱 및 모바일 앱은 암호화로 레이블이 지정된 파일에 대한 공동 생성을 지원하지 않습니다. 이러한 앱은 계속 단독 편집 모드에서 레이블이 지정되고 암호화된 파일을 열 수 있습니다.

- 관리자가 사용자의 동기화 클라이언트에 다운로드된 파일에 이미 적용된 게시된 레이블의 설정을 변경하는 경우 사용자는 OneDrive 동기화 폴더에서 파일에 적용한 변경 내용을 저장하지 못할 수 있습니다. 이 시나리오는 암호화로 레이블이 지정되는 파일에 적용될 수 있으며, 암호화를 적용하는 레이블에 암호화를 적용하지 않은 레이블에서 레이블이 변경된 경우도 적용됩니다. 흰색 교차 [](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3)아이콘 오류가 있는 빨간색 원이 표시되고 새 변경 내용을 별도의 복사본으로 저장해야 합니다. 대신 파일을 닫았다가 다시 열거나 웹에서 Office를 사용할 수 있습니다.

- 레이블이 지정된 문서가 SharePoint 또는 OneDrive에 업로드되고 서비스 사용자 이름의 계정을 사용하여 암호화를 적용한 레이블이 적용된 경우 웹의 Office에서 문서를 열 수 없습니다. 예제 시나리오에는 Microsoft Cloud App Security 및 전자 메일로 Teams로 전송된 파일이 포함됩니다.

- 사용자는 웹용 Office를 사용하는 대신 Word, Excel 또는 PowerPoint용 데스크톱 및 모바일 앱을 사용할 때 오프라인 또는 절전 모드로 전환한 후 저장 문제를 경험할 수 있습니다. 이러한 사용자의 경우 Office 앱 세션을 다시 시작하고 변경 내용을 저장하려고 하면 원본 파일을 저장하는 대신 복사본을 저장하는 옵션이 있는 업로드 실패 메시지가 표시됩니다. 

- 다음과 같은 방법으로 암호화된 문서는 웹의 Office에서 열 수 없습니다.
    - -프레미스 키를 사용하는 암호화("자체 키 보유" 또는 HYOK)
    - 이중 키 암호화를 사용하여 [적용된 암호화](double-key-encryption.md)
    - 권한 관리 보호 템플릿을 직접 적용하는 등 레이블과 독립적으로 적용된 암호화입니다.

- 적용 가능한 레이블 정책에서 레이블을 제거하는 대신 SharePoint 또는 OneDrive의 문서에 적용된 레이블을 삭제하면 다운로드 시 문서에 레이블이 지정되거나 암호화되지 않습니다. 이에 비해 레이블이 지정한 문서가 SharePoint 또는 OneDrive 외부에 저장되어 있는 경우 레이블이 삭제된 경우 문서가 암호화된 상태로 남아 있습니다. 테스트 단계에서 레이블을 삭제할 수 있습니다. 그러나 프로덕션 환경에서 레이블을 삭제하는 경우는 매우 드물습니다.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>SharePoint 및 OneDrive에 대해 민감도 레이블을 사용하도록 설정하는 방법(옵트인)

Microsoft 365 규정 준수 센터를 사용하여 또는 PowerShell을 사용하여 새 기능을 사용하도록 설정할 수 있습니다. SharePoint 및 OneDrive에 대한 모든 테넌트 수준 구성 변경과 함께 변경 내용을 적용하는 데 15분 정도 걸립니다.

### <a name="use-the-compliance-center-to-enable-support-for-sensitivity-labels"></a>준수 센터를 사용하여 민감도 레이블에 대한 지원을 사용하도록 설정

이 옵션은 SharePoint 및 OneDrive에 대해 민감도 레이블을 사용하도록 설정하는 가장 쉬운 방법이지만 테넌트에 대한 전역 관리자로 로그인해야 합니다.

1. 전역 관리자로 [Microsoft 365](https://compliance.microsoft.com/) 규정 준수 센터에 로그인하고 솔루션 정보   >  **보호로 이동합니다.**
    
    이 옵션이 바로 보이지 않는 경우에는 먼저 **모두 표시** 를 선택합니다. 

2. Office Online 파일에서 콘텐츠를 처리 하는 기능을 켜는 메시지가 표시 된 경우 지금 켜기 **선택:**
    
    ![지금 켜기 단추를 켜서 Office Online에 대해 민감도 레이블을 사용하도록 설정](../media/sensitivity-labels-turn-on-banner.png)
    
    이 명령은 즉시 실행됩니다. 페이지가 다음에 새로 고쳐지면 메시지나 단추가 더 이상 표시되지 않습니다.

> [!NOTE]
> Microsoft 365 Multi-Geo가 있는 경우 PowerShell을 사용하여 모든 지리적 위치에 대해 이러한 기능을 사용하도록 설정해야 합니다. 자세한 내용은 다음 섹션을 참조하세요.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>PowerShell을 사용하여 민감도 레이블 지원 사용

준수 센터를 사용하는 대신 SharePoint Online PowerShell의 [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenant) cmdlet을 사용하여 민감도 레이블에 대한 지원을 사용하도록 설정할 수 있습니다. 

Microsoft 365 Multi-Geo가 있는 경우 PowerShell을 사용하여 모든 지리적 위치에 대해 이 지원을 사용하도록 설정해야 합니다.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>SharePoint Online 관리 셸 준비

PowerShell 명령을 실행하여 SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정하기 전에 SharePoint Online 관리 셸 버전 16.0.19418.12000 이상을 실행 중인지 확인하십시오. 이미 최신 버전이 있는 경우 다음 [](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) 절차로 건너뛰어 PowerShell 명령을 실행할 수 있습니다.

1. PowerShell 갤러리에서 이전 버전의 SharePoint Online 관리 셸을 설치한 경우 다음 cmdlet을 실행하여 모듈을 업데이트할 수 있습니다.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. 또는 Microsoft 다운로드 센터에서 이전 버전의 SharePoint Online 관리 셸을 설치한 경우  프로그램 추가 또는 제거로 이동하여 SharePoint Online 관리 셸을 제거할 수도 있습니다.

3. 웹 브라우저에서 다운로드 센터 페이지로 이동한 다음 [최신 SharePoint Online 관리 셸을 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=255251)합니다.

4. 언어를 선택한 다음 **다운로드** 를 클릭합니다.

5. X64 및 x86 .msi 파일 중에서 선택합니다. 32비트 버전을 실행한 경우 64비트 버전의 Windows 또는 x86 파일을 실행한 경우 x64 파일을 다운로드합니다. 모르는 경우 실행 중인 Windows 운영 체제 버전을 [참조하세요.](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. 파일을 다운로드한 후 파일을 실행하고 설치 마법사의 단계를 따릅니다.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>PowerShell 명령을 실행하여 민감도 레이블 지원을 사용하도록 설정

새 기능을 사용하도록 설정하려면 *EnableAIPIntegration* 매개 변수와 함께 [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenant) cmdlet을 사용합니다.

1. Microsoft 365에서 전역 관리자 또는 SharePoint 관리자 권한이 있는 직장 또는 학교 계정을 사용하여 SharePoint에 연결합니다. 자세한 방법은 [SharePoint Online 관리 셸 시작](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)을 참조하세요.
    
    참고: Microsoft 365 Multi-Geo가 있는 경우 [Connect-SPOService와](https://docs.microsoft.com/powershell/module/sharepoint-online/connect-sposervice)함께 -Url 매개 변수를 사용하여 지리적 위치 중 하나에 대해 SharePoint Online 관리 센터 사이트 URL을 지정합니다.

2. 다음 명령을 실행하고 **Y를 눌러** 다음을 확인할 수 있습니다.

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. Microsoft 365 Multi-Geo의 경우: 나머지 각 지리적 위치에 대해 1단계와 2단계를 반복합니다.

## <a name="publishing-and-changing-sensitivity-labels"></a>민감도 레이블 게시 및 변경

SharePoint 및 OneDrive에서 민감도 레이블을 사용하는 경우 새 민감도 레이블을 게시하거나 기존 민감도 레이블을 업데이트할 때 복제 시간을 허용해야 합니다. 이는 암호화를 적용하는 새 레이블에 특히 중요합니다.

예를 들어 암호화를 적용하는 새 민감도 레이블을 만들고 게시하면 사용자의 데스크톱 앱에 매우 빠르게 표시됩니다. 사용자가 이 레이블을 문서에 적용한 다음 SharePoint 또는 OneDrive에 업로드합니다. 서비스에 대해 레이블 복제가 완료되지 않은 경우 새 기능이 업로드 시 해당 문서에 적용되지 않습니다. 따라서 문서를 검색하거나 eDiscovery에 대해 반환하지 못하며 웹용 Office에서 문서를 열 수 없습니다.  

다음 변경 내용은 1시간 내에 복제됩니다. 새 민감도 레이블 및 삭제된 민감도 레이블 및 정책에 있는 레이블을 포함 하는 민감도 레이블 정책 설정.

다음 변경 내용은 24시간 내에 복제됩니다. 기존 레이블에 대한 민감도 레이블 설정에 대한 변경 내용입니다.

복제 지연은 새 민감도 레이블의 경우 1시간 뿐이기 때문에 이 예제의 시나리오에서 실행될 가능성이 낮습니다. 그러나 안전 조치로, 먼저 몇 테스트 사용자에게만 새 레이블을 게시하고 한 시간 동안 기다렸다가 SharePoint 및 OneDrive에서 레이블 동작을 확인하는 것이 좋습니다. 마지막 단계에서는 기존 레이블 정책에 사용자를 더 추가하여 더 많은 사용자가 레이블을 사용할 수 있도록 설정하거나 표준 사용자에 대한 기존 레이블 정책에 레이블을 추가합니다. 표준 사용자에게 레이블이 표시될 때 이미 SharePoint 및 OneDrive에 동기화되어 있습니다.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint IRM(정보 권한 관리) 및 민감도 레이블

[SharePoint IRM(정보](set-up-irm-in-sp-admin-center.md) 권한 관리)은 파일을 다운로드할 때 암호화 및 제한을 적용하여 목록 및 라이브러리 수준에서 파일을 보호하는 이전 기술입니다. 이 이전 보호 기술은 권한이 없는 사용자가 SharePoint 외부에 있는 동안 파일을 열지 못하도록 디자인됩니다.

이에 비해 민감도 레이블은 암호화 외에도 시각적 표시(머리발, 발자국, 워터마크)의 보호 설정을 제공합니다. 암호화 설정은 사용자가 콘텐츠로 할 수 있는 작업을 제한하는 모든 사용 권한을 지원하며, 많은 시나리오에서 동일한 민감도 레이블이 [지원됩니다.](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) [](https://docs.microsoft.com/azure/information-protection/configure-usage-rights) 워크로드 및 앱 전체에서 일관된 설정으로 동일한 보호 방법을 사용하면 일관된 보호 전략이 설정됩니다.

그러나 두 보호 솔루션을 함께 사용할 수 있으며 동작은 다음과 같습니다. 

- 암호화를 적용하는 민감도 레이블이 있는 파일을 업로드하는 경우 SharePoint에서 이러한 파일의 콘텐츠를 처리하지 못하기 때문에 이러한 파일에 대해 공동 생성, eDiscovery, DLP 및 검색이 지원되지 않습니다.

- 웹용 Office를 사용하여 파일에 레이블을 지정하면 레이블의 암호화 설정이 적용됩니다. 이러한 파일의 경우 공동 사용, eDiscovery, DLP 및 검색이 지원됩니다.

- 웹에서 Office를 사용하여 레이블이 지정되는 파일을 다운로드하면 레이블이 유지되고 레이블의 암호화 설정이 IRM 제한 설정이 아닌 적용됩니다.

- 민감도 레이블로 암호화되지 않은 Office 또는 PDF 파일을 다운로드하면 IRM 설정이 적용됩니다.

- 사용자가 IRM을 지원하지 않는 문서를 업로드하지 못하게 하는 등 추가 IRM 라이브러리 설정을 사용하도록 설정한 경우 이러한 설정이 적용됩니다.

이 동작을 사용하면 레이블이 지정되지 않은 경우에도 다운로드된 모든 Office 및 PDF 파일이 무단 액세스로부터 보호됩니다. 그러나 업로드된 레이블이 지정되어 있는 파일은 새로운 기능을 통해 혜택을 받을 수 없습니다.


## <a name="search-for-documents-by-sensitivity-label"></a>민감도 레이블로 문서 검색    

관리 속성 **InformationProtectionLabelId를** 사용하여 특정 민감도 레이블이 있는 SharePoint 또는 OneDrive의 모든 문서를 찾을 수 있습니다. 다음 구문을 사용 합니다. `InformationProtectionLabelId:<GUID>`

예를 들어 "기밀"으로 레이블이 지정되어 있는 모든 문서를 검색하고 해당 레이블의 GUID는 "8faca7b8-8d20-48a3-8ea2-0f96310a848e"입니다. 검색 상자에 다음을 입력합니다.

`InformationProtectionLabelId: 8faca7b8-8d20-48a3-8ea2-0f96310a848e`    

민감도 레이블의 GUID를 얻습니다. [Get-Label](https://docs.microsoft.com/powershell/module/exchange/get-label) cmdlet을 사용 합니다.  

1. 우선 [Office 365 보안 및 준수 센터 PowerShell에 연결](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)합니다. 
   
    예를 들어 관리자로 실행하는 PowerShell 세션에서 전역 관리자 계정으로 로그인합니다.    

2. 그런 다음 다음 명령을 실행합니다.  

    ```powershell   
    Get-Label |ft Name, Guid    
    ``` 

관리 속성 사용에 대한 자세한 내용은 [SharePoint에서 검색 schema 관리를 참조하세요.](https://docs.microsoft.com/sharepoint/manage-search-schema)

## <a name="remove-encryption-for-a-labeled-document"></a>레이블이 있는 문서에 대한 암호화 제거

SharePoint 관리자가 SharePoint에 저장된 문서에서 암호화를 제거해야 하는 경우는 드문 경우가 있습니다. 해당 문서에 [](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) 대해 권한 관리 사용 권한을 부여하거나 해당 문서에 대해 모든 권한을 할당한 사용자는 Azure Information Protection에서 Azure 권한 관리 서비스에서 적용한 암호화를 제거할 수 있습니다. 예를 들어 이러한 사용 권한 중 하나를 사용하는 사용자는 암호화를 적용하는 레이블을 암호화 없이 레이블로 바꿀 수 있습니다. 또는 슈퍼 [](https://docs.microsoft.com/azure/information-protection/configure-super-users) 사용자는 파일을 다운로드하고 암호화 없이 로컬 복사본을 저장할 수 있습니다.

또는 전역 관리자 또는 [SharePoint](https://docs.microsoft.com/sharepoint/sharepoint-admin-role) 관리자는 [Unlock-SPOSensitivityLabelEncryptedFile](https://docs.microsoft.com/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet을 실행하여 민감도 레이블과 암호화를 모두 제거할 수 있습니다. 이 cmdlet은 관리자가 사이트 또는 파일에 대한 액세스 권한이 없거나 Azure 권한 관리 서비스를 사용할 수 없는 경우에도 실행됩니다. 

예를 들어,

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

요구 사항:

- SharePoint Online 관리 셸 버전 16.0.20616.12000 이상.

- 암호화는 관리자 정의 암호화 설정을 사용하여 민감도 레이블에 [](encryption-sensitivity-labels.md#assign-permissions-now) 의해 적용되었습니다(이제 권한 할당은 레이블 설정). [이 cmdlet에는](encryption-sensitivity-labels.md#double-key-encryption) 이중 키 암호화가 지원되지 않습니다.

사당성 텍스트는 파일에서 제거된 민감도 레이블의 감사 이벤트에 추가되고 **암호** 해독 작업은 Azure Information Protection에 대한 보호 사용 현황 [로깅에도 기록됩니다.](https://docs.microsoft.com/azure/information-protection/log-analyze-usage) [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities)

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>SharePoint 및 OneDrive에 대해 민감도 레이블을 사용하지 않도록 설정하는 방법(옵트아웃)

이러한 새 기능을 사용하지 않도록 설정하면 레이블 설정이 계속 적용되어 SharePoint 및 OneDrive에 대해 민감도 레이블을 사용하도록 설정한 후에 업로드한 파일이 계속 레이블로 보호됩니다. 이러한 새 기능을 사용하지 않도록 설정한 후 새 파일에 민감도 레이블을 적용하면 전체 텍스트 검색, eDiscovery 및 공동 작업 기능이 더 이상 작동하지 않습니다.

이러한 새 기능을 사용하지 않도록 설정하려면 PowerShell을 사용해야 합니다. SharePoint Online 관리 셸 및 [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenant) cmdlet을 사용하여 [PowerShell](#use-powershell-to-enable-support-for-sensitivity-labels) 사용 섹션에서 설명한 바와 동일한 *EnableAIPIntegration* 매개 변수를 지정하여 민감도 레이블 섹션을 지원하도록 합니다. 그러나 이번에는 매개 변수 값을 false로 설정하고 **Y를 눌러** 다음을 확인할 수 있습니다.

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Microsoft 365 Multi-Geo가 있는 경우 각 지리적 위치에 대해 이 명령을 실행해야 합니다.

## <a name="next-steps"></a>다음 단계

SharePoint 및 OneDrive에서 Office 파일에 대해 민감도 레이블을 사용하도록 설정한 후 자동 레이블 지정 정책을 사용하여 이러한 파일에 자동으로 레이블을 지정하는 것이 좋습니다. 자세한 내용은 자동으로 민감도 레이블 적용을 [참조하세요.](apply-sensitivity-label-automatically.md)
