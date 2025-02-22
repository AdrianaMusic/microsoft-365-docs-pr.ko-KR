---
title: PowerShell을 사용하여 Microsoft 365에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Microsoft 365용 PowerShell을 사용하여 Microsoft 365 테넌트에 연결하여 명령줄에서 관리 센터 작업을 수행합니다.
ms.openlocfilehash: 33f9af45418ae8a1f126d2b321e7246201bd1f6e
ms.sourcegitcommit: f07442d077eb4357fa5d99d051b035705eb30efa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "49002408"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>PowerShell을 사용하여 Microsoft 365에 연결

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Microsoft 365용 PowerShell을 사용하여 명령줄에서 Microsoft 365 설정을 관리할 수 있습니다. PowerShell에 연결하려면 필수 소프트웨어를 설치하고 Microsoft 365 조직에 연결하면 됩니다.

Microsoft 365 및 관리자 계정, 그룹 및 라이선스에 연결하는 데 사용할 수 있는 두 가지 버전의 PowerShell 모듈이 있습니다.

- Azure Active Directory PowerShell for Graph(cmdlet의 이름에 *AzureAD* 포함)
- Windows PowerShell용 Microsoft Azure AD 모듈(cmdlet의 이름에 *Msol* 포함)

현재, Azure Active Directory PowerShell for Graph 모듈이 사용자, 그룹 및 라이선스 관리를 위한 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 완전히 대체하는 것은 아닙니다. 어떤 경우에는, 두 버전을 모두 사용해야 합니다. 동일한 컴퓨터에 두 버전을 안전하게 설치할 수 있습니다.

## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 사항은 무엇인가요?


**운영 체제**

64비트 버전의 Windows를 사용해야 합니다. 32비트 버전의 Windows PowerShell용 Microsoft Azure Active Directory 모듈 지원은 2014년에 종료됩니다.

다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10, Windows 8.1, Windows 8 또는 Windows 7 서비스팩 1(SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1

>[!Note]
>Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2 SP1의 경우, [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)을 다운로드하고 설치합니다. 

**PowerShell**

- Azure Active Directory PowerShell for Graph 모듈의 경우 PowerShell 버전 5.1 이상을 사용해야 합니다.

- Windows PowerShell용 Microsoft Azure Active Directory 모듈의 경우 PowerShell 버전 5.1 이상 PowerShell 버전 6 이하를 사용해야 합니다. PowerShell 버전 7은 사용할 수 없습니다.
       
>[!Note]
>이러한 절차는 Microsoft 365 관리자 역할의 구성원인 사용자를 대상으로 합니다. 자세한 내용은 [관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요.


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>그런 다음, Azure Active Directory PowerShell for Graph 모듈에 연결합니다.

Azure Active Directory PowerShell for Graph 모듈의 명령에는 cmdlet 이름에 *AzureAD* 가 있습니다. [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) 모듈 또는 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps)을 설치할 수 있습니다.

Azure Active Directory PowerShell for Graph 모듈에서 새 cmdlet을 필요로 하는 프로시저의 경우, 이러한 단계를 사용해서 모듈을 설치하고 Microsoft 365 구독에 연결할 수 있습니다.

> [!Note]
> Windows의 여러 버전에 대한 지원 정보는 [Azure Active Directory PowerShell for Graph 모듈](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2)을 참조하세요.

### <a name="step-1-install-the-required-software"></a>1단계: 필수 소프트웨어 설치

이러한 단계는 컴퓨터에서 한 번만 필요합니다. 그러나 소프트웨어를 정기적으로 업데이트해야 할 수 있습니다.
  
1. 관리자 권한의 Windows PowerShell 명령 프롬프트 창을 엽니다(관리자 권한으로 Windows PowerShell 실행).
    
2. 다음 명령을 실행합니다.
    
    ```powershell
    Install-Module -Name AzureAD
    ```

   신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y** 를 입력하고 Enter 키를 누릅니다.

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>2단계: Microsoft 365 구독을 위해 Azure AD에 연결

계정 이름 및 암호를 사용하여 또는 다단계 인증을 사용하여 Microsoft 365 구독을 위해 Azure AD(Azure Active Directory)에 연결하려면, Windows PowerShell 명령 프롬프트에서 이 명령 중 하나를 실행하세요. (관리자일 필요는 없습니다.)

| Office 365 클라우드 | 명령 |
|:-------|:-----|
| Office 365 Worldwide(+GCC) | `Connect-AzureAD` |
| 21 Vianet이 운영하는 Office 365 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

**계정에 로그인하세요** 대화 상자에서, Microsoft 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인** 을 선택하세요.

다단계 인증을 사용하는 경우 지침에 따라 확인 코드와 같은 추가 인증 정보를 제공합니다.

연결 후 [Azure Active Directory PowerShell for Graph 모듈](https://docs.microsoft.com/powershell/module/azuread)의 cmdlet을 사용할 수 있습니다.

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결

>[!Note]
>Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 *sol* 이 있습니다.

PowerShell 버전 7 이상은 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 *Msol* 이 있는 cmdlet을 지원하지 않습니다. PowerShell 버전 7 이상의 경우 Azure Active Directory PowerShell for Graph 모듈 또는 Azure PowerShell을 사용해야 합니다.

PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 *Msol* 이 있는 cmdlet을 지원하지 않습니다. Windows PowerShell에서 이러한 cmdlet을 실행합니다.
    
### <a name="step-1-install-the-required-software"></a>1단계: 필수 소프트웨어 설치

이러한 단계는 컴퓨터에서 한 번만 필요합니다. 그러나 소프트웨어를 정기적으로 업데이트해야 할 수 있습니다.
  
1.  Windows 10을 사용하는 것이 아니라면 64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.
    
2. 다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.
    
   1. 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
   1.  **Install-Module MSOnline** 명령을 실행합니다.
   1. NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y** 를 입력하고 Enter 키를 누릅니다.
   1. PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y** 를 입력하고 Enter 키를 누릅니다.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>2단계: Microsoft 365 구독을 위해 Azure AD에 연결

계정 이름 및 암호를 사용하여 또는 MFA(다중 요소 인증)을 사용하여 Microsoft 365 구독을 위해 Azure AD에 연결하려면, Windows PowerShell 명령 프롬프트(관리자 권한이 아니어도 됨)에서 이 명령 중 하나를 실행하세요. (관리자일 필요는 없습니다.)

| Office 365 클라우드 | 명령 |
|:-------|:-----|
| Office 365 Worldwide(+GCC) | `Connect-MsolService` |
| 21 Vianet이 운영하는 Office 365 | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

**계정에 로그인하세요** 대화 상자에서, Microsoft 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인** 을 선택하세요.

다단계 인증을 사용하는 경우 지침에 따라 확인 코드와 같은 추가 인증 정보를 제공합니다.

### <a name="how-do-you-know-it-worked"></a>작동 여부는 어떻게 확인하나요?

오류 메시지가 표시되지 않으면 성공적으로 연결된 것입니다. 빠르게 테스트하려면 **Get-MsolUser** 과 같은 Microsoft 365 cmdlet을 실행하고 결과를 확인하세요.
  
오류 메시지가 표시되는 경우 다음 문제를 확인하세요.
  
- **가장 흔한 문제는 암호를 잘못 입력한 경우입니다**. [2단계](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription)를 다시 실행하고 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.
    
- **Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하려면 컴퓨터에 Microsoft .NET Framework 3.5.* x*가 있어야 합니다**. 컴퓨터에 최신 버전(예: 4 또는 4.5.* x*)이 설치되어 있을 수 있습니다. 이전 버전의 .NET Framework와 이전 버전과의 호환성을 사용하거나 사용하지 않도록 설정할 수 있습니다. 자세한 내용은 다음 문서를 참조하세요.
    
  - Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.
    
  - Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.

  - Windows 10, Windows 8.1 및 Windows 8의 경우, [Windows 10, Windows 8.1 및 Windows 8에 .NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)를 참조하세요.

  
- **Windows PowerShell용 Microsoft Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Windows PowerShell용 Microsoft Azure Active Directory 모듈 또는 Microsoft 365용 PowerShell에서 다음 명령을 실행하세요.
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    반환된 버전 번호가 *1.0.8070.2* 보다 낮은 경우 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 제거한 후 위의 [1단계](#step-1-install-the-required-software)에서 최신 버전을 설치합니다.

- **연결 오류 메시지가 표시되면**, ["Connect-MsolService: 형식 예외가 발생함" 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377)를 참조하세요.
    
- **"Get-Item: 경로를 찾을 수 없음" 오류 메시지가 표시되면**, 다음 명령을 실행하세요.


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="see-also"></a>참고 항목

- [PowerShell로 Microsoft 365 관리](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Microsoft 365용 PowerShell 시작](getting-started-with-microsoft-365-powershell.md)
- [단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
