---
title: DLP 정책 조건, 예외 및 작업(미리 보기)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: dlp 정책 조건 및 예외에 대한 자세한 정보
ms.openlocfilehash: 5c2c8e010047c2de05cc8422da1958e2fe5fc54c
ms.sourcegitcommit: d859ea36152c227699c1786ef08cda5805ecf7db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604218"
---
# <a name="dlp-policy-conditions-exceptions-and-actions-preview"></a>DLP 정책 조건, 예외 및 작업(미리 보기)

DLP 정책의 조건 및 예외는 정책이 적용되는 중요한 항목을 식별합니다. 동작은 예외가 충족되는 조건의 결과로 수행되는 작업을 정의합니다.

- 조건은 포함할 것을 정의합니다.
- 예외는 제외할 대상을 정의합니다.
- 동작은 조건 또는 예외가 충족된 결과로 수행되는 작업을 정의합니다.
 
대부분의 조건 및 예외에는 하나 이상의 값을 지원하는 속성이 하나 있습니다. 예를 들어 DLP 정책을 Exchange 전자 메일에 적용하는 경우 보낸 사람 조건은 메시지를 보낸 사람이 필요합니다. **The sender** Some conditions have two properties. 예를 들어 **A 메시지** 헤더에는 메시지 헤더 필드를 지정하는 속성 하나와 헤더 필드에서 검색할 텍스트를 지정하는 두 번째 속성이 필요합니다. 일부 조건 또는 예외에는 속성이 없습니다. 예를 들어 **첨부 파일은** 암호로 보호된 메시지의 첨부 파일을 간단히 하여 암호로 보호된 조건입니다.

작업에는 일반적으로 추가 속성이 필요합니다. 예를 들어 DLP 정책 규칙이 메시지를 리디렉션할 때 메시지를 리디렉션할 위치를 지정해야 합니다. 
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>DLP 정책에 대한 조건 및 예외

다음 섹션의 표에서는 DLP에서 사용할 수 있는 조건 및 예외에 대해 설명합니다.

- [보낸 사람](#senders)
- [받는 사람](#recipients)
- [메시지 제목 또는 본문](#message-subject-or-body)
- [첨부 파일](#attachments)
- [메시지 헤더](#message-headers)
- [메시지 속성](#message-properties)

### <a name="senders"></a>보낸 사람


|**DLP의 조건 또는 예외**  |**Microsoft 365 PowerShell의 조건/예외 매개 변수** |**속성 형식**  |**description**|
|---------|---------|---------|---------|
|보낸 사람 |조건: *From* <br/> 예외: *ExceptIfFrom*      |Addresses |     조직의 지정된 사서함, 메일 사용자, 메일 연락처 또는 Microsoft 365 그룹에서 보낸 메시지입니다.|
|보낸 사람 IP 주소는     |조건: *SenderIPRanges*<br/> 예외: *ExceptIfSenderIPRanges*         |  IPAddressRanges       | 보낸 사람 IP 주소가 지정된 IP 주소와 일치하거나 지정된 IP 주소 범위 내에 있는 메시지입니다.       |
|보낸 사람 주소에 단어 포함   | 조건: *FromAddressContainsWords* <br/> 예외: *ExceptIfFromAddressContainsWords*        |   단어      |   보낸 사람 전자 메일 주소에 지정된 단어가 포함된 메시지입니다.|
| 보낸 사람 주소가 패턴과 일치    | 조건: *FromAddressMatchesPatterns* <br/> 예외: *ExceptFromAddressMatchesPatterns*       |      패턴   |  보낸 사람 전자 메일 주소에 지정된 정규식과 일치하는 텍스트 패턴이 포함된 메시지입니다.  |
|보낸 사람 도메인  |  조건: *SenderDomainIs* <br/> 예외: *ExceptIfSenderDomainIs*       |DomainName         |     보낸 사람 전자 메일 주소의 도메인이 지정된 값과 일치하는 메시지입니다. 지정된 도메인(예: 도메인의 *contain* 하위 도메인)을 포함하는 보낸 사람 도메인을 찾아야 하는 경우 보낸 사람 주소가 **The sender address matches** 일치하는(FromAddressMatchesPatterns) 조건을 사용하고 다음 구문을 사용하여 도메인을 *FromAddressMatchesPatterns* \. 지정합니다. \.    |
|보낸 사람 범위    | 조건: *FromScope* <br/> 예외: *ExceptIfFromScope*    | UserScopeFrom    |    내부 또는 외부 보낸 사람이 보낸 메시지입니다.    |

### <a name="recipients"></a>받는 사람

|**DLP의 조건 또는 예외**| **Microsoft 365 PowerShell의 조건/예외 매개 변수** |    **속성 형식** | **description**|
|---------|---------|---------|---------|
|받는 사람은|  조건: *SentTo* <br/> 예외: *ExceptIfSentTo* | Addresses | 받는 사람 중 한 명이 조직의 지정된 사서함, 메일 사용자 또는 메일 연락처인 메시지입니다. 받는 사람은 메시지의 **To** 받는 **사람,Cc** 또는 **Bcc** 필드에 있을 수 있습니다.|
|받는 사람 도메인은|   조건: *RecipientDomainIs* <br/> 예외: *ExceptIfRecipientDomainIs* |   DomainName |    보낸 사람 전자 메일 주소의 도메인이 지정된 값과 일치하는 메시지입니다.|
|받는 사람 주소에 단어 포함|  조건: *RecipientAddressContainsWords* <br/> 예외: *ExceptIfRecipientAddressContainsWords*|    단어|  받는 사람의 전자 메일 주소에 지정된 단어가 포함된 메시지입니다. <br/>**참고**: 이 조건은 받는 사람 프록시 주소로 보낸 메시지는 고려하지 않습니다. 받는 사람의 기본 전자 메일 주소로 보낸 메시지만 일치시킵니다.|
|받는 사람 주소가 패턴과 일치| 조건: *RecipientAddressMatchesPatterns* <br/> 예외: *ExceptIfRecipientAddressMatchesPatterns*|   패턴    |받는 사람의 전자 메일 주소에 지정된 정규식과 일치하는 텍스트 패턴이 포함된 메시지입니다. <br/> **참고**: 이 조건은 받는 사람 프록시 주소로 보낸 메시지는 고려하지 않습니다. 받는 사람의 기본 전자 메일 주소로 보낸 메시지만 일치시킵니다.|
|구성원에게 전송| 조건: *SentToMemberOf* <br/> 예외: *ExceptIfSentToMemberOf*|  Addresses|  지정된 메일 그룹, 메일 사용이 가능한 보안 그룹 또는 Microsoft 365 그룹의 구성원인 받는 사람이 포함된 메시지입니다. 그룹은 메시지의 **To,** **Cc** 또는 **Bcc** 필드에 있을 수 있습니다.|

### <a name="message-subject-or-body"></a>메시지 제목 또는 본문

|**DLP의 조건 또는 예외** | **Microsoft 365 PowerShell의 조건/예외 매개 변수** |**속성 형식**| **description**|
|---------|---------|---------|---------|
|제목에 단어 또는 구가 들어 있습니다.| 조건: *SubjectContainsWords* <br/> 예외: *ExceptIf SubjectContainsWords*| 단어   |제목 필드에 지정된 단어가 있는 메시지입니다.|
|제목 일치 패턴|조건: *SubjectMatchesPatterns* <br/> 예외: *SubjectMatchesPatterns 제외*|패턴   |제목 필드에 지정된 정규식과 일치하는 텍스트 패턴이 포함된 메시지입니다.|
|콘텐츠에 다음 포함|  조건: *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*| SensitiveInformationTypes|  DLP(데이터 손실 방지) 정책에 정의된 중요한 정보를 포함하는 메시지 또는 문서입니다.|
| 제목 또는 본문 일치 패턴    | 조건: *SubjectOrBodyMatchesPatterns* <br/> 예외: *ExceptIfSubjectOrBodyMatchesPatterns*    | 패턴    | 제목 필드 또는 메시지 본문에 지정된 정규식과 일치하는 텍스트 패턴이 포함된 메시지입니다.    |
| 제목 또는 본문에 단어 포함    | 조건: *SubjectOrBodyContainsWords* <br/> 예외: *ExceptIfSubjectOrBodyContainsWords*    | 단어    | 제목 필드 또는 메시지 본문에 지정된 단어가 있는 메시지    |


### <a name="attachments"></a>첨부 파일

|**DLP의 조건 또는 예외**| **Microsoft 365 PowerShell의 조건/예외 매개 변수**| **속성 형식**   |**description**|
|---------|---------|---------|---------|
|첨부 파일이 암호로 보호됨|조건: *DocumentIsPasswordProtected* <br/> 예외: *ExceptIfDocumentIsPasswordProtected*|없음| 첨부 파일이 암호로 보호되어 검사할 수 없는 메시지입니다. 암호 검색은 Office 문서, .zip 파일 및 .7z 파일에만 작동합니다.|
|첨부 파일의 파일 확장명은|조건: *ContentExtensionMatchesWords* <br/> 예외: *ExceptIfContentExtensionMatchesWords*|  단어   |첨부 파일의 파일 확장명이 지정된 단어와 일치하는 메시지입니다.|
|전자 메일 첨부 파일 콘텐츠를 검색할 수 없습니다.|조건: *DocumentIsUnsupported* <br/>예외: *ExceptIf DocumentIsUnsupported*|   해당 없음|    첨부 파일이 Exchange Online에서 기본적으로 인식되지 않는 메시지입니다.|
|전자 메일 첨부 파일 콘텐츠가 검색을 완료하지 못했습니다.|   조건: *ProcessingLimitExceeded* <br/> 예외: *ExceptIfProcessingLimitExceeded*|    해당 없음 |규칙 엔진이 첨부 파일 검색을 완료할 수 없는 메시지입니다. 이 조건을 사용하여 콘텐츠를 완전히 검색할 수 없는 메시지를 식별하고 처리하기 위해 함께 작동되는 규칙을 만들 수 있습니다.|
|문서 이름에 단어 포함|조건: *DocumentNameMatchesWords* <br/> 예외: *ExceptIfDocumentNameMatchesWords* |단어  |첨부 파일의 파일 이름이 지정된 단어와 일치하는 메시지입니다.|
|문서 이름이 패턴과 일치|조건: *DocumentNameMatchesPatterns* <br/> 예외: *ExceptIfDocumentNameMatchesPatterns*|    패턴    |첨부 파일의 파일 이름에 지정된 정규식과 일치하는 텍스트 패턴이 포함된 메시지입니다.|
|문서 속성은|조건: *ContentPropertyContainsWords* <br/> 예외: *ExceptIfContentPropertyContainsWords* |단어| 첨부 파일의 파일 확장명이 지정된 단어와 일치하는 메시지 또는 문서입니다.|
|문서 크기가 같거나 보다 크거나 같은 경우| 조건: *DocumentSizeOver* <br/> 예외: *ExceptIfDocumentSizeOver*|    크기    |첨부 파일이 지정된 값보다 크거나 같은 메시지입니다.|

### <a name="message-headers"></a>메시지 헤더

|**DLP의 조건 또는 예외**| **Microsoft 365 PowerShell의 조건/예외 매개 변수**| **속성 형식**|  **description**|
|---------|---------|---------|---------|
|헤더에 단어 또는 구가 포함되어 있습니다.|조건: *HeaderContainsWords* <br/> 예외: *ExceptIfHeaderContainsWords*|  해시 테이블  |지정한 헤더 필드가 포함된 메시지와 해당 헤더 필드의 값에 지정된 단어가 들어 있습니다.|
|헤더가 패턴과 일치|   조건: *HeaderMatchesPatterns* <br/> 예외: *ExceptIfHeaderMatchesPatterns*|    해시 테이블  |지정한 헤더 필드를 포함하는 메시지와 해당 헤더 필드 값에 지정된 정규식이 포함되어 있습니다.|

### <a name="message-properties"></a>메시지 속성

|**DLP의 조건 또는 예외**| **Microsoft 365 PowerShell의 조건/예외 매개 변수**| **속성 형식**   |**description**|
|---------|---------|---------|---------|
|메시지 크기 이상|조건: *MessageSizeOver* <br/> 예외: *ExceptIfMessageSizeOver*| 크기    |전체 크기(메시지 및 첨부 파일)가 지정된 값보다 크거나 같은 메시지입니다. <br/>**참고:** 사서함의 메시지 크기 제한은 메일 흐름 규칙 전에 평가됩니다. 사서함에 대해 너무 큰 메시지는 이 조건이 있는 규칙이 메시지에 대해 처리되기 전에 거부됩니다.|
| 중요도    | 조건: *WithImportance* <br/> 예외: *ExceptIfWithImportance*    | 중요도    | 지정된 중요도 수준으로 표시된 메시지입니다.    |
| 콘텐츠 문자 집합에 단어 포함    | 조건: *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*    | CharacterSets    | 지정된 문자 집합 이름이 있는 메시지입니다.    |
| 보낸 사람에 대한 다시 정당성    | 조건: *HasSenderOverride* <br/> 예외: *ExceptIfHasSenderOverride*    | 해당 없음    | 보낸 사람이 DLP(데이터 손실 방지) 정책을 다시 적용하기로 선택한 메시지입니다. DLP 정책에 대한 자세한 내용은 데이터 손실 [방지를 참조하십시오.](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)   |
| 메시지 유형이 일치    | 조건: *MessageTypeMatches* <br/> 예외: *ExceptIfMessageTypeMatches*    | MessageType    | 지정한 유형의 메시지입니다.    |

## <a name="actions-for-dlp-policies"></a>DLP 정책에 대한 작업

다음 표에서는 DLP에서 사용할 수 있는 작업에 대해 설명합니다.


|**DLP의 작업**|**Microsoft 365 PowerShell의 작업 매개 변수**|**속성 형식**|**description**|
|---------|---------|---------|---------|
|Set 헤더|SetHeader|첫 번째 속성: *헤더 이름* </br> 두 번째 속성: *헤더 값*|SetHeader 매개 변수는 메시지 헤더의 헤더 필드와 값을 추가하거나 수정하는 DLP 규칙에 대한 작업을 지정합니다. 이 매개 변수는 "HeaderName:HeaderValue" 구문을 사용합니다. 여러 헤더 이름과 값 쌍을 콤보로 구분하여 지정할 수 있습니다.|
|헤더 제거| RemoveHeader| 첫 번째 속성: *MessageHeaderField*</br> 두 번째 속성: *String*|  RemoveHeader 매개 변수는 메시지 헤더에서 헤더 필드를 제거하는 DLP 규칙에 대한 작업을 지정합니다. 이 매개 변수는 "HeaderName" 또는 "HeaderName:HeaderValue" 구문을 사용합니다. 여러 헤더 이름 또는 헤더 이름 및 값 쌍을 콤보로 구분하여 지정할 수 있습니다.|
|특정 사용자에게 메시지 리디렉션|*RedirectMessageTo*|Addresses| 메시지를 지정된 받는 사람에게 리디렉션합니다. 원래 받는 사람에게 메시지가 배달되지 않으며, 보낸 사람이나 원래 받는 사람에게 알림이 전송되지 않습니다.|
|승인을 위해 보낸 사람 관리자에게 메시지 전달| 보통|첫 번째 속성: *ModerateMessageByManager*</br> 두 번째 속성: *부울*|Moderate 매개 변수는 중재자에 전자 메일 메시지를 보내는 DLP 규칙에 대한 작업을 지정합니다. 이 매개 변수는 @{ModerateMessageByManager = <$true \| $false>.|
|특정 승인자에 대한 승인을 위해 메시지 전달| 보통|첫 번째 속성: *ModerateMessageByUser*</br>두 번째 속성: *Addresses*|Moderate 매개 변수는 중재자에 전자 메일 메시지를 보내는 DLP 규칙에 대한 작업을 지정합니다. 이 매개 변수는 @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")} 구문을 사용합니다.|
|받는 사람 추가|AddRecipients|첫 번째 속성: *Field*</br>두 번째 속성: *Addresses*| 메시지의 받는 사람/Cc/Bcc 필드에 하나 이상의 받는 사람을 추가합니다. 이 매개 변수는 @{<AddToRecipients \| CopyTo \| BlindCopyTo> = "emailaddress"} 구문을 사용합니다.|
|보낸 사람의 관리자를 받는 사람으로 추가|AddRecipients | 첫 번째 속성: *AddedManagerAction*</br>두 번째 속성: *Field* | 보낸 사람의 관리자를 지정된 받는 사람 유형(받는 사람,Cc, Bcc)으로 메시지에 추가하거나 보낸 사람 또는 받는 사람에게 알리지 않고 메시지를 보낸 사람의 관리자로 리디렉션합니다. 이 작업은 보낸 사람 관리자 특성이 Active Directory에 정의된 경우만 작동합니다. 이 매개 변수는 @{AddManagerAsRecipientType = "<To \| Cc \| Bcc>"} 구문을 사용합니다.|    
제목 추가    |PrependSubject    |문자열    |지정한 텍스트를 메시지의 제목 필드 시작에 추가합니다. 공백 또는 콜론(:) 를 지정한 텍스트의 마지막 문자로 사용하여 원래 제목 텍스트와 차별화합니다.</br>제목에 이미 포함된 텍스트(예: 답장)에 동일한 문자열이 추가되지 않도록 규칙에 "제목에 단어 포함"(ExceptIfSubjectContainsWords) 예외를 추가합니다.    |
HTML 고지 조항 적용    |ApplyHtmlDisclaimer    |첫 번째 속성: *Text*</br>두 번째 속성: *Location*</br>세 번째 속성: *Fallback 작업*    |지정한 HTML 고지 조항을 메시지의 필수 위치에 적용합니다.</br>이 매개 변수는 @{ Text = " 구문을 사용합니다. Location = <추가 \| 추가>; FallbackAction = <Wrap \| \| Ignore Reject> }




