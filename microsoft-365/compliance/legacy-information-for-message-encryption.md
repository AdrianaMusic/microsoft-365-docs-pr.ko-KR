---
title: Office 365 메시지 암호화 레거시 정보
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 레거시 파일을 조직의 OME(Office 365 메시지 암호화)로 전환하는 방법을 이해합니다.
ms.openlocfilehash: bf64d7991a843d2fd3d4f5f927eaa5c4bfef921c
ms.sourcegitcommit: a8f3c633714e934f9ad026c3bc72157ed535dcfc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/29/2020
ms.locfileid: "49738035"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Office 365 메시지 암호화 레거시 정보

아직 조직을 새 OME 기능으로 이동하지 않았지만 이미 OME를 배포한 경우 이 문서의 정보가 조직에 적용됩니다. 조직에 적절한 새 OME 기능으로의 이동 계획을 세우는 것이 좋습니다. 자세한 내용은 Azure Information Protection을 바탕으로 구축된 새로운 Office 365 메시지 암호화 [기능 설정을 참조하세요.](set-up-new-message-encryption-capabilities.md) 새 기능의 작동 방식에 대한 자세한 내용은 [Office 365 메시지](ome.md)암호화를 참조하세요. 이 문서의 나머지는 새 OME 기능이 릴리스되기 전에 OME 동작을 참조합니다.
  
Office 365 메시지 암호화를 사용하여 조직은 조직 내부 및 외부 사용자 간에 암호화된 전자 메일 메시지를 보내고 받을 수 있습니다. Office 365 메시지 암호화는 Outlook.com, Yahoo, Gmail 및 기타 전자 메일 서비스와 함께 작동합니다. 전자 메일 메시지 암호화를 사용하면 받는 사람만 메시지 콘텐츠를 볼 수 있습니다.
  
그 예는 다음과 같습니다.
  
- 은행 직원이 고객에게 신용 카드 문을 전송합니다.

- 보험 회사 담당자가 고객에게 정책 세부 정보를 제공합니다.

- 모기지 브로커가 대출 신청을 위해 고객의 재무 정보를 요청합니다.

- 의료 공급자가 환자에게 의료 정보를 전송합니다.

- 한 변호사가 고객 또는 다른 변호사에게 기밀 정보를 전송합니다.

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Office 365 메시지 암호화가 새로운 기능 없이 작동하는 방식

Office 365 메시지 암호화는 Microsoft Azure RMS(Azure 권한 관리)를 바탕으로 구축된 온라인 서비스입니다. Azure RMS를 사용하여 관리자는 메일 흐름 규칙을 정의하여 암호화 조건을 결정할 수 있습니다. 예를 들어 규칙은 특정 받는 사람에게 주소가 지정되는 모든 메시지의 암호화를 요구할 수 있습니다.
  
암호화 규칙과 일치하는 전자 메일 메시지를 Exchange Online에서 보내는 경우 해당 메시지는 HTML 첨부 파일과 함께 전송됩니다. 받는 사람이 HTML 첨부 파일을 열고 지침에 따라 Office 365 메시지 암호화 포털에서 암호화된 메시지를 볼 수 있습니다. 받는 사람은 Microsoft 계정이나 Office 365와 연결된 직장이나 학교에 로그인하거나 일회용 코드를 사용하여 메시지를 볼 수 있습니다. 두 옵션을 사용하면 해당 받는 사람만 암호화된 메시지를 볼 수 있도록 보장할 수 있습니다. 이 프로세스는 새로운 OME 기능에서 매우 다릅니다.
  
다음 다이어그램은 암호화 및 암호 해독 프로세스를 통한 전자 메일 메시지의 흐름이 요약되어 있습니다.
  
![암호화된 전자 메일의 경로를 보여 주는 다이어그램](../media/O365-Office365MessageEncryption-Concept.png)
  
자세한 내용은 새 OME 기능을 릴리스하기 전에 레거시 [Office 365](legacy-information-for-message-encryption.md#LegacyServiceInfo)메시지 암호화에 대한 서비스 정보를 참조하세요.
  
## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities"></a>새 OME 기능을 사용하지 않는 Office 365 메시지 암호화에 대한 메일 흐름 규칙 정의

새 기능 없이 Office 365 메시지 암호화를 사용하도록 설정하기 위해 Exchange Online 및 Exchange Online Protection 관리자는 Exchange 메일 흐름 규칙을 정의합니다. 이러한 규칙은 전자 메일 메시지를 암호화해야 하는 조건과 메시지 암호화 제거 조건에 따라 결정됩니다. 규칙에 대해 암호화 작업이 설정되어 있는 경우 서비스는 메시지를 보내기 전에 규칙 조건과 일치하는 모든 메시지에 대해 작업을 수행합니다.

메일 흐름 규칙은 유연하며 단일 규칙에서 특정 보안 요구 사항을 충족할 수 있도록 조건을 결합할 수 있습니다. 예를 들어 지정된 키워드를 포함하며 외부 받는 사람에게 주소가 지정된 모든 메시지를 암호화하는 규칙을 만들 수 있습니다. 또한 Office 365 메시지 암호화는 암호화된 전자 메일의 받는 사람의 응답을 암호화하며 전자 메일 사용자의 편의를 위해 해당 답장의 암호를 해독하는 규칙을 만들 수 있습니다. 이렇게 하면 조직의 사용자가 응답을 보기 위해 암호화 포털에 로그인할 수 없습니다.
  
Exchange 메일 흐름 규칙을 만드는 방법에 대한 자세한 내용은 [Office 365](define-mail-flow-rules-to-encrypt-email.md)메시지 암호화에 대한 규칙 정의를 참조하십시오.
  
### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>EAC를 사용하여 새 OME 기능 없이 전자 메일 메시지 암호화를 위한 메일 흐름 규칙 만들기

1. 웹 브라우저에서 전역 관리자 권한이 부여된 직장 또는 학교 계정을 사용하여 [Office 365에 로그인합니다.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. 관리 **타일을** 선택 합니다.

3. Microsoft 365 관리 센터에서 **관리 센터** \> **Exchange를 선택 합니다.**

4. EAC에서 메일 흐름 **규칙으로** 이동하고 새 새로 만들기 \>   ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **아이콘을 선택합니다.** EAC 사용에 대한 자세한 내용은 [Exchange Online의 Exchange 관리 센터를 참조하세요.](https://docs.microsoft.com/exchange/exchange-admin-center)

5. **이름에** 규칙의 이름을 입력합니다(예: 사용자 이름에 대한 메일 DrToniRamos@hotmail.com.

6. **다음의 경우 이 규칙 적용** 에서 조건을 선택하고 필요한 경우 값을 입력합니다. 예를 들어 DrToniRamos@hotmail.com에 보내는 메시지를 암호화하려면 다음을 수행합니다.

   1. **다음의 경우 이 규칙 적용** 에서 **받는 사람이 다음과 같음** 을 선택합니다.

   2. 연락처 목록에서 기존 이름을 선택하거나 **이름 확인** 상자에 새 전자 메일 주소를 입력합니다.

      - 기존 이름을 선택하려면 목록에서 이름을 선택한 다음 **확인** 을 클릭합니다.

      - 새 이름을 입력하려면 확인란에 전자  메일 주소를 입력한 다음 이름 **확인을** \> **선택합니다.**

7. 조건을 더 추가하려면 **추가 옵션을** 선택한 다음 조건 **추가를 선택하고** 목록에서 선택합니다.

   예를 들어 받는 사람이 조직 외부에 있는 경우만  규칙을 적용하려면 조건 추가를 선택한 다음 받는 사람이 **외부/내부** 조직 외부인 경우 확인을 \>  \> **선택합니다.**

8. 새 OME 기능을 사용하지 않고 암호화를 사용하도록 설정하려면  다음을 선택하고 메시지 보안 수정 OME의 이전 버전 적용을 선택한 다음 \> 저장을 **선택합니다.**

   IRM 라이선스를 사용할 수 없는 오류가 표시되면 레거시 OME를 사용하지 않습니다.

9. (선택 사항) 작업을 **추가하여** 다른 작업을 지정합니다.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Exchange Online PowerShell을 사용하여 새 OME 기능 없이 전자 메일 메시지 암호화를 위한 메일 흐름 규칙 만들기

1. Exchange Online PowerShell에 연결합니다. 자세한 내용은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)을 참조하세요.

2. **New-TransportRule** cmdlet을 사용하여 규칙을 만들고 _ApplyOME_ 매개 변수를 `$true` .로 설정

   이 예에서는 모든 전자 메일 메시지를 암호화해야 DrToniRamos@hotmail.com 합니다.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Where,

   - 새 규칙의 고유한 이름은 "Dr Toni Ramos에 대한 규칙 암호화"입니다.
   - _SentTo_ 매개 변수는 메시지 받는 사람(이름, 전자 메일 주소, 고유 이름 등으로 식별)을 지정합니다. 이 예에서 받는 사람은 전자 메일 주소 "DrToniRamos@hotmail.com"로 식별됩니다.
   - _SentToScope_ 매개 변수는 메시지 받는 사람의 위치를 지정합니다. 이 예에서는 받는 사람의 사서함이 hotmail에 있으며 조직의 일부가 아니기 때문에 값이 `NotInOrganization` 사용됩니다.

   자세한 구문 및 매개변수 정보 [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/New-TransportRule)을 참조하세요.

### <a name="remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>새 OME 기능 없이 암호화된 전자 메일 응답에서 암호화 제거

전자 메일 사용자가 암호화된 메시지를 보내면 해당 메시지의 받는 사람은 암호화된 회신을 통해 응답을 할 수 있습니다. 조직의 전자 메일 사용자가 암호화 포털에 로그인하여 볼 수 있도록 응답에서 암호화를 자동으로 제거하는 메일 흐름 규칙을 만들 수 있습니다. EAC 또는 Windows PowerShell cmdlet을 사용하여 이러한 규칙을 정의할 수 있습니다. 조직 내에서 보낸 메시지나 조직 내에서 보낸 메시지에 대한 응답 메시지의 암호를 해독할 수 있습니다. 조직 외부에서 보낸 암호화된 메시지의 암호를 해독할 수는 없습니다.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>EAC를 사용하여 새 OME 기능 없이 암호화된 전자 메일 응답에서 암호화를 제거하는 규칙 만들기

1. 웹 브라우저에서 관리자 권한이 부여된 직장 또는 학교 계정을 사용하여 [Office 365에 로그인합니다.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. 관리 **타일을** 선택 합니다.

3. Microsoft 365 관리 센터에서 **관리 센터** \> **Exchange를 선택 합니다.**

4. EAC에서 메일 흐름 **규칙으로** 이동하고 새 새로 만들기 \>   ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **아이콘을 선택합니다.** EAC 사용에 대한 자세한 내용은 [Exchange Online의 Exchange 관리 센터를 참조하세요.](https://docs.microsoft.com/exchange/exchange-admin-center)

5. **이름에** 받는 메일에서 암호화 제거와 같은 규칙의 이름을 입력합니다.

6. 받는 **사람이 조직** 내부에 있는 경우와 같이 메시지에서  암호화를 제거해야 하는 조건을 선택하는 경우 이 규칙을 \> **적용합니다.**

7. In **The following,** select **Modify the message security** Remove the previous version of \> **OME.**

8. **저장** 을 선택합니다.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Exchange Online PowerShell을 사용하여 새로운 OME 기능 없이 암호화된 전자 메일 응답에서 암호화를 제거하는 규칙 만들기

1. Exchange Online PowerShell에 연결합니다. 자세한 내용은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)을 참조하세요.

2. **New-TransportRule** cmdlet을 사용하여 규칙을 만들고 _RemoveOME_ 매개 변수를 `$true` .로 설정

   이 예에서는 조직의 받는 사람에게 전송된 모든 메일에서 암호화를 제거합니다.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Where,

   - 새 규칙의 고유 이름은 "받는 메일에서 암호화 제거"입니다.
   - _SentToScope_ 매개 변수는 메시지 받는 사람의 위치를 지정합니다. 이 예제에서는 다음 중 하나를 나타내는 값 `InOrganization` 값이 사용됩니다.
     - 받는 사람이 조직의 사서함, 메일 사용자, 그룹 또는 메일 사용이 가능한 공용 폴더입니다.
     - 받는 사람의 전자 메일 주소가 조직의 내부 릴레이 도메인 또는 권한이 있는 도메인으로 구성된 허용 도메인에 있으며 _인증된_ 연결을 통해 메시지를 보내거나 받은 경우

자세한 구문 및 매개변수 정보 [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/New-TransportRule)을 참조하세요.

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>새 기능 없이 암호화된 메시지 보내기, 보기 및 회신

Office 365 메시지 암호화를 사용하는 경우 관리자가 정의한 규칙에 따라 전자 메일 메시지가 자동으로 암호화됩니다. 암호화된 메시지가 있는 전자 메일은 HTML 파일이 첨부된 받는 사람의 받은 편지함으로 도착합니다.
  
받는 사람은 메시지의 지침에 따라 첨부 파일을 열고 Microsoft 계정 또는 Office 365와 연결된 직장 또는 학교를 사용하여 인증합니다. 받는 사람의 계정이 없는 경우 암호화된 메시지를 보기 위해 로그인할 수 있는 Microsoft 계정을 만들 수 있습니다. 또는 받는 사람은 메시지를 보기 위한 일회성 코드를 받을 수 있습니다. 로그인하거나 일회용 암호를 사용한 후 받는 사람은 암호 해독된 메시지를 보고 암호화된 회신을 보낼 수 있습니다.
  
## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Office 365 메시지 암호화를 사용하여 암호화된 메시지 사용자 지정

Exchange Online 및 Exchange Online Protection 관리자는 암호화된 메시지를 사용자 지정할 수 있습니다. 예를 들어 회사의 브랜드 및 로고를 추가하고, 소개를 지정하고, 암호화된 메시지와 받는 사람이 암호화된 메시지를 볼 수 있는 포털에 고지 조항 텍스트를 추가할 수 있습니다. Windows PowerShell cmdlet을 사용하면 암호화된 전자 메일 메시지 받는 사람의 보기 환경에서 다음과 같은 요소를 사용자 지정할 수 있습니다.

- 암호화된 메시지를 포함하는 전자 메일의 소개 텍스트

- 암호화된 메시지를 포함하는 전자 메일의 고지 사항 텍스트

- 메시지 보기 포털에 표시되는 포털 텍스트

- 전자 메일 메시지와 보기 포털에 표시되는 로고

언제든지 기본 모양과 느낌으로 되돌릴 수 있습니다.
  
다음 예에서는 전자 메일 첨부 파일에 포함된 ContosoPharma의 사용자 지정 로고를 보여 줍니다.

> [!div class="mx-imgBorder"]
> ![암호화된 메시지 보기 페이지 예제](../media/TA-OME-3attachment2.jpg)
  
**조직의 브랜드를 사용하여 암호화 전자 메일 메시지 및 암호화 포털을 사용자 지정**
  
1. 원격 PowerShell을 사용하여 Exchange Online에 연결에 설명된 바와 같이 원격 [PowerShell을 사용하여 Exchange Online에 연결합니다.](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)

2. 여기에 설명된 Set-OMEConfiguration cmdlet을 사용하세요. [Set-OMEConfiguration](https://technet.microsoft.com/3ef0aec0-ce28-411d-abe8-7236f082af1b) 또는 지침은 다음 표를 사용하세요.

   **암호화 사용자 지정 옵션**

   | 암호화 환경에서 사용자 지정하려는 기능 | 사용할 Windows PowerShell 명령 |
   |:-----|:-----|
   |암호화된 전자 메일 메시지에 포함되는 기본 텍스트  <br/> 암호화된 메시지를 보기 위한 지침 위에 표시되는 기본 텍스트  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <br/> **예:**`Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"` <br/> |
   |암호화된 메시지를 포함하는 전자 메일의 고지 사항 설명문  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <br/> **예:**`Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"` <br/> |
   |암호화된 메일 보기 포털 위쪽에 표시되는 텍스트  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <br/> **예:**`Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"` <br/> |
   |로고  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <br/> **예:**`Set-OMEConfiguration -Identity "OME configuration" -Image (Get-Content "C:\Temp\contosologo.png" -Encoding byte)` <br/> 지원되는 파일 형식: .png, .jpg, .bmp 또는 .tiff  <br/> 로고 파일의 최적 크기: 40KB 미만  <br/> 최적 로그 이미지 크기: 170x70 픽셀  <br/> |

**암호화 전자 메일 메시지 및 암호화 포털에서 브랜드 사용자 지정을 제거하려면**
  
1. 원격 PowerShell을 사용하여 Exchange Online에 연결에 설명된 바와 같이 원격 [PowerShell을 사용하여 Exchange Online에 연결합니다.](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx)

2. 설명된 Set-OMEConfiguration cmdlet을 [사용하세요. Set-OMEConfiguration](https://technet.microsoft.com/3ef0aec0-ce28-411d-abe8-7236f082af1b). DisclaimerText, EmailText 및 PortalText 값에서 조직의 브랜드가 지정한 사용자 지정을 제거하려면 값을 빈 문자열로  `""` 설정하십시오. 로고와 같은 모든 이미지 값에 대해 값을  `"$null"` .로 설정

   **암호화 사용자 지정 옵션**

   | 암호화 환경의 이 기능을 기본 텍스트 및 이미지로 되돌리려면 | 사용할 Windows PowerShell 명령 |
   |:-----|:-----|
   |암호화된 전자 메일 메시지에 포함되는 기본 텍스트  <br/> 암호화된 메시지를 보기 위한 지침 위에 표시되는 기본 텍스트  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <br/> **예:**`Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""` <br/> |
   |암호화된 메시지를 포함하는 전자 메일의 고지 사항 설명문  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <br/> **예:**`Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""` <br/> |
   |암호화된 메일 보기 포털 위쪽에 표시되는 텍스트  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <br/> **기본값으로 되돌리기 예:**`Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""` <br/> |
   |로고  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <br/> **기본값으로 되돌리기 예:**`Set-OMEConfiguration -Identity "OME configuration" -Image $null` <br/> |

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>새 OME 기능을 릴리스하기 전에 레거시 Office 365 메시지 암호화에 대한 서비스 정보
<a name="LegacyServiceInfo"> </a>

다음 표에서는 새 OME 기능이 릴리스된 후 Office 365 메시지 암호화 서비스에 대한 기술 세부 정보를 제공합니다.
  
| 서비스 정보 | 설명 |
|:-----|:-----|
|클라이언트 장치 요구 사항  <br/> |양식 게시를 지원하는 최신 브라우저에서 HTML 첨부 파일을 열 수 있으면 모든 클라이언트 장치에서 암호화된 메시지를 확인할 수 있습니다.  <br/> |
|암호화 알고리즘 및 FIPS(Federal Information Processing Standard) 규정 준수  <br/> |Office 365 메시지 암호화에서는 Windows Azure IRM(정보 권한 관리)과 같은 암호화 키를 사용하며 암호화 모드 2(RSA용 2K 키 및 SHA-1 시스템용 256비트 키)가 지원됩니다. 주된 IRM 암호화 모드에 대한 자세한 내용은 [AD RMS 암호화 모드를 참조하세요.](https://technet.microsoft.com/library/hh867439%28WS.10%29.aspx)  <br/> |
|지원되는 메시지 유형  <br/> |Office 365 메시지 암호화는 메시지 클래스 ID가 **IPM.Note** 인 항목에 대해서만 지원됩니다. 자세한 내용은 항목 유형 및 [메시지 클래스를 참조하세요.](https://msdn.microsoft.com/library/office/ff861573.aspx)  <br/> |
|메시지 크기 제한  <br/> |Office 365 메시지 암호화는 최대 25MB의 메시지를 암호화할 수 있습니다. 메시지 크기 제한에 대한 자세한 내용은 [Exchange Online 제한을 참조하세요.](https://technet.microsoft.com/library/exchange-online-limits.aspx)  <br/> |
|Exchange Online 전자 메일 보존 정책  <br/> |Exchange Online은 암호화된 메시지를 저장하지 않습니다.  <br/> |
|Office 365 메시지 암호화에 대한 언어 지원  <br/> | Office 365 메시지 암호화는 다음과 같이 Microsoft 365 언어를 지원합니다.  <br/>  받는 전자 메일 메시지와 첨부된 HTML 파일은 보낸 사람 언어 설정에 따라 지역화됩니다.  <br/>  보기 포털은 받는 사람의 브라우저 설정에 따라 지역화됩니다.  <br/>  암호화된 메시지의 본문(내용)은 지역화되지 않습니다.  <br/> |
|OME 포털 및 OME 뷰어 앱에 대한 개인 정보 취급 방침 정보  <br/> |[Office 365 Messaging Encryption Portal privacy statement](https://privacy.microsoft.com/privacystatement)은 Microsoft가 귀하의 개인 정보로 수행하는 작업과 수행하지 않는 작업에 대한 자세한 정보를 제공합니다.  <br/> |

## <a name="frequently-asked-questions-about-legacy-ome"></a>레거시 OME에 대한 질문과 대답
<a name="LegacyServiceInfo"> </a>

Office 365 메시지 암호화에 대한 질문이 있나요? 다음은 몇 가지 답변입니다. 필요한 것을 찾을 수 없는 경우 [Office 365용 Microsoft 기술 커뮤니티 포럼을 확인하세요.](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365)
  
 **Q. 사용자가 조직 외부의 받는 사람에게 암호화된 전자 메일 메시지를 보냅니다. Office 365 메시지 암호화로 암호화된 전자 메일 메시지를 읽고 회신하기 위해 외부 받는 사람이 해야 할 일이 있나요?**
  
Microsoft 365 암호화된 메시지를 받는 조직 외부의 받는 사람은 다음 두 가지 방법 중 하나를 사용하여 메시지를 볼 수 있습니다.
  
- Microsoft 계정 또는 Office 365와 연결된 직장 또는 학교 계정으로 로그인합니다.

- 일회용 코드 사용

 **Q. Microsoft 365 암호화된 메시지가 클라우드 또는 Microsoft 서버에 저장되어 있나요?**
  
아니요. 암호화된 메시지는 받는 사람의 전자 메일 시스템에 보관되며 받는 사람이 메시지를 열면 Microsoft 서버에서 볼 수 위해 일시적으로 게시됩니다. 메시지가 여기에 저장되지 않습니다.
  
 **Q. 암호화된 전자 메일 메시지를 원하는 브랜드로 사용자 지정할 수 있나요?**
  
예. Windows PowerShell cmdlet을 사용하여 암호화된 전자 메일 메시지 위쪽에 표시되는 기본 텍스트, 고지 사항 텍스트, 그리고 전자 메일 메시지와 암호화 포털에 사용할 로고를 사용자 지정할 수 있습니다. 이 기능은 이제 OMEv2에서 사용할 수 있습니다. 자세한 내용은 [Add branding to encrypted messages](add-your-organization-brand-to-encrypted-messages.md)를 참조하세요.
  
 **Q. 서비스를 사용하려면 조직의 모든 사용자에게 라이선스가 필요하나요?**
  
암호화된 전자 메일을 보내는 조직의 모든 사용자에게는 라이선스가 있어야 합니다.
  
 **Q. 외부 받는 사람도 서비스를 구독해야 하나요?**
  
아니요. 외부 받는 사람은 서비스를 구독하지 않아도 암호화된 메시지를 읽거나 회신을 보낼 수 있습니다.
  
 **Q. Office 365 메시지 암호화는 RMS(권한 관리 서비스)와 어떻게 다른가요?**
  
RMS는 전달 금지 및 회사 기밀과 같은 기본 제공 템플릿을 제공하여 조직의 내부 전자 메일에 대한 정보 권한 보호 기능을 제공합니다. Office 365 메시지 암호화에서는 내부 받는 사람과 외부 받는 사람에게 보내는 메시지에 대해 전자 메일 메시지 암호화가 지원됩니다.
  
 **Q. Office 365 메시지 암호화는 S/MIME과 어떻게 다른가요?**
  
S/MIME은 기본적으로 클라이언트 쪽 암호화 기술이며, 사용하려면 복잡한 인증서 관리 및 게시 인프라가 필요합니다. Office 365 메시지 암호화는 메일 흐름 규칙(전송 규칙)을 사용하며 인증서 게시에 의존하지 않습니다.
  
 **Q. 모바일 장치에서 암호화된 메시지를 읽을 수 있나요?**
  
예, Google Play 스토어 및 Apple App 스토어에서 OME 뷰어 앱을 다운로드하여 Android 및 iOS에서 메시지를 볼 수 있습니다. OME 뷰어 앱에서 HTML 첨부 파일을 연 다음 지시에 따라 암호화된 메시지를 엽니다. 모바일 장치에서는 메일 클라이언트에서 폼 게시를 지원하는 경우 HTML 첨부 파일을 열 수 있습니다.
  
 **Q. 회신과 전달된 메시지도 암호화되나요?**
  
예. 스레드가 진행되는 동안에는 응답도 계속 암호화됩니다.
  
 **Q. Office 365 메시지 암호화가 지역화를 제공합니까?**
  
받는 전자 메일 및 HTML 콘텐츠는 보낸 사람의 전자 메일 설정에 따라 지역화됩니다. 보기 포털은 받는 사람의 브라우저 설정에 따라 지역화됩니다. 그러나 암호화된 메시지의 실제 본문(내용)은 지역화되지 않습니다.
  
 **Q. Office 365 메시지 암호화에 사용되는 암호화 방법은 무엇입니까?**
  
Office 365 메시지 암호화는 RMS(권한 관리 서비스)를 암호화 인프라로 사용합니다. 사용되는 암호화 방식은 메시지 암호화 및 암호 해독에 사용되는 RMS 키를 얻은 위치에 따라 다릅니다.
  
- Microsoft Azure RMS를 사용하여 키를 얻는 경우 암호화 모드 2가 사용됩니다. 암호화 모드 2는 업데이트된 향상된 AD RMS 암호화 구현입니다. 서명 및 암호화를 위해 RSA 2048을 지원하고 서명에 대해 SHA-256을 지원합니다.

- AD(Active Directory) RMS를 사용하여 키를 얻은 경우 암호화 모드 1 또는 암호화 모드 2가 사용됩니다. 사용되는 방법은 온-프레미스 AD RMS 배포에 따라 다릅니다. 암호화 모드 1은 원래 AD RMS 암호화 구현으로, 서명 및 암호화에 RSA 1024을 지원하고 서명에 SHA-1을 지원합니다. 이 모드는 RMS의 모든 현재 버전에서 계속 지원됩니다.

자세한 내용은 [AD RMS 암호화 모드를 참조하세요.](https://go.microsoft.com/fwlink/p/?LinkId=398616)
  
**Q. 일부 암호화된** 메시지에서 보낸 메시지라고 하는 이유는 Office365@messaging.microsoft.com?
  
암호화된 회신 암호화 포털에서 또는 OME 뷰어 앱을 통해 전송되는 경우 암호화된 메시지는 Microsoft 끝점을 통해 전송되므로 보내는 전자 메일 주소는 Office365@messaging.microsoft.com으로 설정됩니다. 이를 통해 암호화된 메시지가 스팸으로 표시되지 않도록 합니다. 암호화 포털 안의 주소 및 전자 메일에 표시되는 이름은 이 레이블을 지정으로 인해 변경되지 않습니다. 또한 다른 전자 메일 클라이언트를 통해서가 아니라 해당 포털을 통해 보낸 메시지에만 이 레이블 지정을 적용합니다.
  
 **Q. EHE(Exchange Hosted Encryption) 구독자입니다. Office 365 메시지 암호화로의 업그레이드에 대한 자세한 내용은 어디에서 알 수 있나요?**
  
모든 EHE 고객은 Office 365 메시지 암호화로 업그레이드되었습니다. 자세한 내용은 Exchange [Hosted Encryption Upgrade Center를 방문하세요.](https://go.microsoft.com/fwlink/p/?LinkID=511077)
  
 **Q. Office 365 메시지 암호화를 지원하려면 조직의 방화벽에서 URL, IP 주소 또는 포트를 열아야 하나요?**
  
예. Office 365 메시지 암호화로 암호화된 메시지에 대한 인증을 사용하도록 설정하려면 조직의 허용 목록에 Exchange Online의 URL을 추가해야 합니다. Exchange Online URL 목록은 Microsoft [365 URL 및 IP 주소 범위를 참조하세요.](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges)
  
 **Q. Microsoft 365 암호화 메시지를 보낼 수 있는 받는 사람 수**
  
받는 사람 제한은 메시지당 받는 사람 500명 또는 메일 목록 확장 후 결합될 경우 메시지의 받는 사람 필드에서 11,980자 중 가장 먼저 오는 문자입니다. 
  
 **Q. 특정 받는 사람에게 보낸 메시지를 취소할 수 있습니까?**
  
아니요. 메시지를 보낸 후 특정인에게 메시지를 해지할 수 없습니다.
  
 **Q. 받아서 읽은 암호화된 메시지에 대한 보고서를 볼 수 있습니까?**
  
암호화된 메시지가 표시되어 있는지 여부를 표시하는 보고서는 없지만 특정 메일 흐름 규칙(전송 규칙)에 일치하는 메시지 수를 확인하는 데 사용할 수 있는 Microsoft 365 보고서가 있습니다.
  
 **Q. Microsoft는 OME 포털 및 OME 뷰어 앱을 통해 제공한 정보로 어떤 작업을 수행하나요?**
  
[Office 365 메시징](https://privacy.microsoft.com/privacystatement) 암호화 포털 개인 정보 취급 방침은 Microsoft가 개인 정보로 하지 않는 일과 하지 않는 일에 대한 자세한 정보를 제공합니다.

**Q. 요청한 후 일회성 코드를 받지 못하면 어떻게 하나요?**

먼저 전자 메일 클라이언트에서 정크 또는 스팸 폴더를 확인합니다. 조직의 DKIM 및 DMARC 설정으로 인해 이러한 전자 메일이 스팸으로 필터링될 수 있습니다.

다음으로 보안 및 준수 센터에서 & 검사합니다. 일회성 코드, 특히 조직에서 처음 받는 코드를 포함하는 메시지는 종종 끊어지게 됩니다.
