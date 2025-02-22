---
title: 도이클란드 Microsoft 클라우드에서 마이그레이션하기 위한 추가 장치 정보
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: '요약: 독일 Microsoft 클라우드(도이치란드 Microsoft 클라우드)에서 새 독일 데이터 센터 지역의 Office 365 서비스로 이동하는 경우 서비스에 대한 추가 장치 정보입니다.'
ms.openlocfilehash: 1bbb4bf39db61a93844c21cd6062a70699b5d6d7
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688657"
---
# <a name="additional-device-information-for-the-migration-from-microsoft-cloud-deutschland"></a>도이클란드 Microsoft 클라우드에서 마이그레이션하기 위한 추가 장치 정보

## <a name="frequently-asked-questions"></a>자주 묻는 질문

**조직이 영향을 받는지 어떻게 알 수 있나요?**

관리자는 등록된 장치가 있는지 `https://portal.microsoftazure.de` 여부를 확인해야 합니다. 조직에서 장치를 등록한 경우 영향을 받을 수 있습니다.

**사용자에게 어떤 영향이 있나요?**

마이그레이션이 [Azure AD](ms-cloud-germany-transition.md#how-is-the-migration-organized) 완료 마이그레이션 단계로 들어오면 등록된 장치의 사용자가 더 이상 로그인할 수 없습니다.  

조직이 도이클란드 Microsoft 클라우드와의 연결을 끊기 전에 모든 장치가 전 세계 끝점에 등록되어 있도록 합니다.
  
**사용자가 언제 장치를 다시 등록하나요?**

도이치란드 [Microsoft](ms-cloud-germany-transition.md#how-is-the-migration-organized) 클라우드 마이그레이션 단계와 별개인 마이그레이션 단계에서만 디바이스 등록을 등록을 다시 등록하고 다시 등록하는 것이 성공에 중요합니다.

**마이그레이션 후 장치 상태를 복원하려면 어떻게 해야 합니까?**

Azure AD에 등록된 하이브리드 Azure AD 가입 및 회사 소유의 Windows 디바이스의 경우 관리자는 원격으로 트리거된 워크플로를 통해 이전 장치 상태의 등록을 등록하지 않습니다.
  
Azure AD에 등록된 개인 Windows 장치를 포함하여 다른 모든 디바이스의 경우 최종 사용자는 이러한 단계를 수동으로 수행해야 합니다. Azure AD에 가입된 장치의 경우 사용자는 등록을 등록을 등록하지 않은 다음 디바이스를 다시 등록하기 위해 로컬 관리자 계정이 필요합니다.

Microsoft는 장치 상태를 성공적으로 복원하는 방법에 대한 지침을 게시합니다. 
 
**모든 장치가 공용 클라우드에 등록되어 있는 것을 어떻게 알 수 있나요?**

장치가 공용 클라우드에 등록되어 있는지 확인하려면 Azure AD 포털에서 Excel 스프레드시트로 장치 목록을 내보내고 다운로드해야 합니다. 그런 다음 도이클랜드 [Microsoft](ms-cloud-germany-transition.md#how-is-the-migration-organized) 클라우드와 분리된 마이그레이션 단계 후 _registeredTime_ 열을 사용하여 등록된 장치를 필터링합니다.

테넌트 마이그레이션 후 장치 등록이 비활성화되어 활성화 또는 비활성화할 수 없습니다. Intune이 사용되지 않는 경우 구독에 로그인하고 다음 명령을 실행하여 옵션을 다시 활성화합니다.

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

## <a name="windows-hybrid-azure-ad-join"></a>Windows 하이브리드 Azure AD 가입

### <a name="windows-down-level"></a>Windows 다운 수준

_Windows 다운_ 수준 장치는 현재 이전 버전의 Windows(예: Windows 8.1 또는 Windows 7)를 실행하거나 2019 및 2016 이전 버전의 Windows Server를 실행 중인 Windows 장치입니다. 이러한 장치가 전에 등록된 경우 등록을 해지하고 해당 장치를 다시 등록해야 합니다. 

Windows 다운 수준 장치가 이전에 Azure AD에 가입 했는지 확인하려면 장치에서 다음 명령을 사용합니다.

```console
%programfiles%\Microsoft Workplace Join\autoworkplace /status
```

디바이스가 이전에 Azure AD에 가입된 경우 장치에 전역 Azure AD 끝점에 대한 네트워크 연결이 있는 경우 다음 출력이 표시됩니다.

```console
+----------------------------------------------------------------------+
| Device Details                                                       |
+----------------------------------------------------------------------+
         DeviceId : AEE2B956-DA62-48D0-BB47-046DD992A110
       Thumbprint : 00fdfa2de5c32feae57489873a13aa6a3ff7433b
             User : user1@<tenantname>.de
Private key state : Okay
     Device state : Unknown
```

영향을 받는 디바이스의 값은 "알 수 없음"인 "장치 상태"입니다. 출력이 "디바이스에 가입되지 않은" 또는 "장치 상태" 값이 "괜찮습니다."인 경우 다음 지침을 무시합니다.

디바이스가 가입(deviceId, 지문 등)으로 표시하고 해당 "장치 상태" 값이 "알 수 없음"인 장치만 해당 다운 수준 장치에서 로그인하는 도메인 사용자 컨텍스트에서 다음 명령을 실행해야 합니다.

```console
"%programfiles%\Microsoft Workplace Join\autoworkplace /leave"
```

위의 명령은 Windows 다운 수준 장치에서 도메인 사용자당 한 번만 실행하면 됩니다. 이 명령은 도메인 사용자 로그인 컨텍스트에서 실행해야 합니다. 

사용자가 이후에 로그인할 때 이 명령을 실행하지 않을 수 있도록 충분히 주의해야 합니다. 위의 명령을 실행하면 로그인한 사용자의 로컬 하이브리드 Azure AD 가입 컴퓨터의 가입 상태가 지워지게 됩니다. 또한 컴퓨터가 여전히 테넌트에 하이브리드 Azure AD에 가입하도록 구성된 경우 사용자가 다시 로그인할 때 가입을 시도합니다.

### <a name="windows-current"></a>Windows Current

#### <a name="unjoin"></a>Unjoin

Windows 10 디바이스가 이전에 Azure AD에 가입 했는지 확인하려면 장치에서 다음 명령을 실행합니다.

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

장치가 하이브리드 Azure AD에 가입된 경우 관리자는 다음 출력을 볼 수 있습니다.

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : YES
```

출력이 "AzureAdJoined : No"이면 다음 지침을 무시합니다.

장치가 Azure AD에 가입된 것으로 표시하는 디바이스에 한해 관리자로 다음 명령을 실행하여 디바이스의 가입 상태를 제거합니다.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

위의 명령은 Windows 장치의 관리 컨텍스트에서 한 번만 실행하면 됩니다.

#### <a name="hybrid-ad-joinre-registration"></a>하이브리드 AD 가입\다시 등록

디바이스가 전역 Azure AD 끝점에 대한 네트워크 연결이 있는 한 디바이스가 사용자 또는 관리자 개입 없이 Azure AD에 자동으로 가입됩니다. 


## <a name="windows-azure-ad-join"></a>Windows Azure AD 가입

**중요:** Intune 서비스 보안 주체는 상거래 마이그레이션 후 사용하도록 설정되어 Azure AD 장치 등록의 활성화를 암시합니다. 마이그레이션 전에 Azure AD 장치 등록을 차단한 경우 PowerShell을 사용하여 Intune 서비스 계정을 사용하지 않도록 설정하여 Azure AD 포털에서 Azure AD 장치 등록을 다시 사용하지 않도록 설정해야 합니다. Azure Active Directory PowerShell for Graph 모듈에서 이 명령을 사용하여 Intune 서비스 계정을 사용하지 않도록 설정할 수 있습니다.

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

### <a name="unjoin"></a>Unjoin

Windows 10 디바이스가 이전에 Azure AD에 가입 했는지 여부를 확인하려면 사용자 또는 관리자가 디바이스에서 다음 명령을 실행할 수 있습니다.

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

디바이스가 Azure AD에 가입된 경우 사용자 또는 관리자는 다음 출력을 볼 수 있습니다.

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : NO
```

출력이 "AzureAdJoined : NO"이면 다음 지침을 무시합니다.

사용자: 디바이스가 Azure AD에 가입된 경우 사용자는 설정에서 디바이스 가입을 언가할 수 있습니다. Azure AD에서 디바이스를 연결하지 전에 디바이스에 로컬 관리자 계정이 있는지 확인합니다. 디바이스에 다시 로그인하려면 로컬 관리자 계정이 필요합니다.

관리자: 조직의 관리자가 Azure AD에 가입된 사용자의 디바이스에 가입을 해지하려는 경우 그룹 정책과 같은 메커니즘을 사용하여 각 디바이스에서 다음 명령을 실행하여 가입을 해지할 수 있습니다. 관리자는 Azure AD에서 디바이스에 연결을 하기 전에 디바이스에 로컬 관리자 계정이 있는지 확인해야 합니다. 디바이스에 다시 로그인하려면 로컬 관리자 계정이 필요합니다.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

위의 명령은 Windows 장치의 관리 컨텍스트에서 한 번만 실행하면 됩니다. 

### <a name="azure-ad-joinre-registration"></a>Azure AD 가입/다시 등록

사용자는 Windows 설정에서 Azure AD에 디바이스를 연결할 수 있습니다. 설정 > 계정 > 또는 학교 액세스 > **있습니다.**
 

## <a name="windows-azure-ad-registered-company-owned"></a>Windows Azure AD 등록(회사 소유)

Windows 10 장치가 Azure AD에 등록되어 있는지 확인하려면 장치에서 다음 명령을 실행합니다.

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

디바이스가 Azure AD 등록된 경우 다음 출력이 표시됩니다.

```console
+----------------------------------------------------------------------+
| User State                                                           |
+----------------------------------------------------------------------+
           WorkplaceJoined : YES
          WamDefaultSet : NO
          WamDefaultAuthority : organizations
```

디바이스에서 기존 Azure AD 등록 계정을 제거하려면

- 장치에서 Azure AD 등록 계정을 제거하려면 여기에서 다운로드할 수 있는 도구인 CleanupWPJ를 [CleanupWPJ.zip. ](https://download.microsoft.com/download/8/e/f/8ef13ae0-6aa8-48a2-8697-5b1711134730/WPJCleanUp.zip)

- ZIP 파일을 추출하고 **WPJCleanup.cmd를 실행합니다.** 이 도구는 디바이스의 Windows 버전에 따라 올바른 실행을 실행합니다.

- 관리자는 그룹 정책과 같은 메커니즘을 사용하여 디바이스에 로그인한 사용자의 컨텍스트에서 디바이스에서 명령을 실행할 수 있습니다.

Azure AD에서 디바이스를 등록하라는 메시지를 표시하는 웹 계정 관리자를 사용하지 않도록 설정하려면 다음 레지스트리 값을 추가합니다. 

- 위치: HKLM\SOFTWARE\Policies\Microsoft\Windows\WorkplaceJoin
- 형식: DWORD(32비트)
- 이름: BlockAADWorkplaceJoin
- 값 데이터: 1

이 레지스트리 값이 존재하면 회사 가입이 차단되어 사용자가 디바이스에 가입하라는 메시지가 표시되지 않도록 해야 합니다.

## <a name="android"></a>Android

Android의 경우 사용자는 디바이스 등록을 등록을 다시 등록하고 다시 등록해야 합니다. Microsoft Authenticator 앱 또는 회사 포털 앱을 통해 이행할 수 있습니다. 

- Microsoft Authenticator 앱에서는 사용자가 장치 등록을 위해 **> 수 있습니다.** 이 경우 사용자는 디바이스 등록을 등록을 다시 등록할 수 있습니다.
 
- 회사 포털에서 사용자는 장치 **탭으로** 이동하여 디바이스를 제거할 수 있습니다. 그런 다음 회사 포털을 사용하여 장치를 다시 등록합니다.
 
- 또한 사용자는 계정 설정 페이지에서 계정을 제거한 다음 직장 계정을 다시 추가하여 등록을 다시 등록 및 다시 등록할 수 있습니다.

Microsoft Authenticator 앱을 사용하여 Android에서 디바이스 등록을 등록을 등록하고 다시 등록하려면

1.  Microsoft Authenticator 앱을 열고 설정으로 **이동합니다.**
2.  장치 **등록을 선택합니다.**
3.  등록을 다시 등록하지 **않습니다.**
4.  장치 **등록의** 경우 전자 메일 주소를 입력하여 장치를 다시 등록한 다음 등록을 **선택합니다.**

Android 설정 페이지에서 Android 디바이스 등록을 등록을 등록하고 다시 등록하려면

1.  장치 **설정을 열고** 계정으로 **이동합니다.**
2.  다시 등록할 작업 계정을 선택하고 계정 **제거를 선택합니다.**
3.  계정이 제거된 후  계정 페이지에서 계정 추가 및 > **선택합니다.**
4.  Workplace **Join의** 경우 전자 메일 주소를 입력하고 **가입을** 선택하여 장치 등록을 완료합니다.

회사 포털에서 Android에서 디바이스 등록을 등록을 등록하고 다시 등록하려면

1.  회사 포털을 시작하고 장치 **탭으로** 이동하십시오.
2.  디바이스를 선택하여 장치 세부 정보를 확인합니다.
3.  타원(3개 점) 메뉴에서 장치 제거를 선택하고 대화 상자에서 확인하여 제거를 완료합니다.
4.  이제 회사 포털 앱에서 로그아웃됩니다. 로그인을 **선택하여** 장치를 다시 등록합니다.

이 워크로드의 마이그레이션 단계 중이나 관리 또는 사용에 미치는 영향에 대한 자세한 내용은 [도이치란드 Microsoft](ms-cloud-germany-transition-azure-ad.md)클라우드에서 마이그레이션하기 위한 추가 Azure AD 정보에서 Azure AD(Azure Active Directory)에 대한 정보를 검토하세요.

## <a name="ios"></a>iOS

iOS 장치에서는 사용자가 Microsoft Authenticator에서 캐시된 계정을 수동으로 제거하고, 디바이스의 등록을 등록하지 않은 후 장치의 모든 네이티브 앱에서 로그인해야 합니다.

### <a name="step-1-if-present-remove-the-account-from-the-microsoft-authenticator-app"></a>1단계: 있는 경우 Microsoft Authenticator 앱에서 계정 제거

1. Microsoft Authenticator 앱에서 계정을 탭합니다.
2. 오른쪽 위 **모서리에** 있는 설정 아이콘을 탭합니다. 설정 아이콘이 없는  경우 최신 버전의 Microsoft Authenticator를 사용하지 않을 수 있습니다.
3. 계정 제거 **단추를** 탭합니다.
4. 이 **디바이스의 모든 앱을 탭합니다.**
 
### <a name="step-2-unregister-the-device-from-the-microsoft-authenticator-app"></a>2단계: Microsoft Authenticator 앱에서 디바이스 등록을 등록을 하지 않습니다.

1. 오른쪽 위 모서리에 있는 메뉴 아이콘을 탭합니다.
2. 설정을 **탭한** 다음 **장치 등록을 누릅니다.**
4. 계정이 표시될 경우 **등록을** 다시 시작하고 대화 상자에서 **계속합니다.** 그 이후에는 계정이 없습니다.
 
### <a name="step-3-sign-out-from-individual-apps-if-necessary"></a>3단계: 필요한 경우 개별 앱에서 사인아웃

사용자는 Outlook, Teams 및 OneDrive와 같은 개별 앱으로 이동하여 해당 앱에서 계정을 제거할 수 있습니다.

## <a name="more-information"></a>추가 정보

시작:

- [독일 Microsoft 클라우드에서 새 독일 데이터 센터 지역의 Office 365 서비스로 마이그레이션](ms-cloud-germany-transition.md)
- [Microsoft Cloud Deutschland 마이그레이션 지원](https://aka.ms/germanymigrateassist)
- [마이그레이션에 대해 옵트인하는 방법](ms-cloud-germany-migration-opt-in.md)
- [마이그레이션 중의 고객 환경](ms-cloud-germany-transition-experience.md)

전환을 통해 이동:

- [문장 작업 및 영향 마이그레이션](ms-cloud-germany-transition-phases.md)
- [추가 사전 작업](ms-cloud-germany-transition-add-pre-work.md)
- [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [디바이스,](ms-cloud-germany-transition-add-devices.md) [환경 및](ms-cloud-germany-transition-add-experience.md)AD [FS에](ms-cloud-germany-transition-add-adfs.md)대한 추가 정보.

클라우드 앱:

- [Dynamics 365 마이그레이션 프로그램 정보](https://aka.ms/d365ceoptin)
- [Power BI 마이그레이션 프로그램 정보](https://aka.ms/pbioptin)
- [Microsoft Teams 업그레이드 시작하기](https://aka.ms/SkypeToTeams-Home)
