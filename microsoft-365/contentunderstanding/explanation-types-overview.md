---
title: 설명 유형
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
localization_priority: Priority
description: Microsoft SharePoint Syntex에서 설명 유형에 대해 자세히 알아보세요.
ms.openlocfilehash: f01529199bf4dea0a14c7dc30b39fcaa5078931b
ms.sourcegitcommit: e7bf23df4852b78912229d1d38ec475223597f34
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49087646"
---
# <a name="introduction-to-explanation-types"></a>설명 유형 소개

설명은 Microsoft SharePoint Syntex의 모델에 대한 이해를 바탕으로 문서에 표시하고 추출하고자 하는 정보를 정의하는데 도움을 줍니다. 설명을 만들 때는 설명 유형을 선택해야 합니다. 이 문서는 다양한 설명 유형과 사용 방법을 이해하는 데 도움이 됩니다. 

   ![설명 유형](../media/content-understanding/explanation-types.png) 
   
다음과 같은 설명 유형을 사용할 수 있습니다.

- **구 목록**: 추출하려는 문서나 정보에 사용할 수 있는 단어, 구, 숫자 또는 기타 문자의 목록입니다. 예를 들어 **의사 추천** 이란 텍스트 문자열은 파악할 수 있는 모든 의료 리퍼럴 문서에 있습니다.</br>

- **패턴 목록**: 추출하려는 정보를 식별하는 데 사용되는 숫자, 문자 또는 기타 문자의 패턴 목록입니다. 예를 들어 식별되는 모든 의학 조회 문서에서 **전화 번호** 를 추출할 수 있습니다.</br>

- **근접**: 각각의 설명이 서로 얼마나 근접한지 설명합니다. 예를 들어 *번지 수* 의 패턴 목록은 *길 이름* 바로 전에 나오고 토큰은 둘 사이에 존재하지 않습니다.(토큰에 대한 자세한 정보는 본 문서의 뒷부분에 나옵니다.) 근사 유형을 사용하려면 모델에 두 개 이상의 설명이 있어야 하고, 그렇지 않으면 해당 옵션을 사용할 수 없습니다. 
 
## <a name="phrase-list"></a>구 목록

일반적으로 구 목록 설명 형식은 모델을 통해 문서를 식별하고 분류하는 데 사용됩니다. *의사 추천* 레이블 예제에 설명된 바와 같이, 확인 중인 문서에서 일관되게 나타나는 일련의 단어, 구, 숫자 또는 문자입니다.

요구 사항은 아니지만, 캡처링하는 구가 문서의 일관된 위치에 있는 경우 설명의 성공을 높일 수 있습니다. 예를 들어, *의사 추천* 이란 레이블이 문서의 첫 번째 문단에 일관되게 배치되어 있을 수 있습니다.

레이블을 식별하는데 대/소문자 구분이 필요하다면, 구 목록 유형을 사용하하면 **정확한 대소문자 사용** 체크박스를 선택하여 이를 설명에 지정할 수 있습니다.

   ![대/소문자 구분](../media/content-understanding/case-sensitivity.png) 

## <a name="pattern-lists"></a>패턴 목록

패턴 목록 유형은 문서에서 정보를 식별하고 추출하는 설명을 만드는 경우에 특히 유용합니다. 일반적으로 날짜, 전화 번호, 신용카드 번호와 같은 다양한 형식으로 표시 됩니다. 예를 들어 날짜의 경우 다양한 형식(2020/1/1, 2020-1-1, 20/01/01, 2020/01/01, 2020년 1월 1일 등)으로 표시될 수 있습니다. 패턴 목록을 정의하면 식별하고 추출하려는 데이터의 가능한 모든 변형을 캡처하여 더 효율적으로 설명을 만들 수 있습니다. 

**전화 번호** 샘플의 경우, 모델이 식별하는 모든 의학 조회 문서에서 각각 추천하는 의사의 전화 번호를 추출합니다. 설명을 만들 때 패턴 목록 유형을 선택하면 돌아올 수 있는 다양한 형식을 사용할 수 있습니다.

   ![전화 번호 패턴 목록](../media/content-understanding/pattern-list.png)

이 예에서는 **0-9 사이의 임의의 수** 확인란을 선택하여 패턴 목록에 사용된 각 "0" 값을 0부터 9까지의 숫자로 인식합니다.

   ![0부터 9 사이 아무 숫자](../media/content-understanding/digit-identity.png)

마찬가지로 텍스트 문자를 포함하는 패턴 목록을 만들 경우 **a-z 사이의 임의의 문자** 확인란을 선택하여 패턴 목록에 사용된 각 "a" 문자를 "a"에서 "z"까지의 문자로 인식합니다.

예를 들어 **날짜** 패턴 목록을 만들 때 *2020년 1월 1일* 과 같은 날짜 서식이 인식되도록 하려면 다음을 수행해야 합니다.
- *0000 aaa 0* 과 *0000 aaa 00* 을 패턴 목록에 추가합니다.
- **a부터 z 사이 아무 문자** 를 선택했는지 확인합니다.

   ![a부터 z 사이 아무 문자](../media/content-understanding/any-letter.png)

또한 패턴 목록에 대문자화 요구 사항이 있는 경우에는 **정확한 대소문자 사용** 옵션을 선택할 수 있습니다. 날짜 예제의 경우 달의 첫 글자를 대문자로 표기하는 경우 다음을 수행 해야 합니다.

- *0000 Aaa 0* 과 *0000 Aaa 00* 을 패턴 목록에 추가합니다.
- **정확한 대소문자 사용** 이 선택되어 있는지 확인합니다.

   ![정확한 대소문자 사용](../media/content-understanding/exact-caps.png)

> [!NOTE]
> 패턴 목록 설명을 수동으로 만드는 대신 [설명 라이브러리](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview#use-explanation-templates)를 사용하여 *날짜*, *전화 번호*, *신용카드 번호* 등 일반 패턴 목록의 서식파일을 사용할 수 있습니다.

## <a name="proximity"></a>근접 

근접 설명 유형은 사용자의 모델이 각각의 데이터가 서로 얼마나 근접해 있는지를 규정할 수 있도록 도와줍니다. 예를 들어 모델에서 고객의 *거리 주소 번호* 와 *전화 번호* 를 둘 다 표시하는 두 개의 설명을 규정합니다. 

또한 고객 전화 번호는 항상 거리 주소 번호 앞에 표시된다는 것을 파악했습니다. 

Alex Wilburn<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

근접 설명을 사용하여 전화 번호 설명이 문서에서 거리 주소 번호를 식별해내기에 근접하지 않은 설명이라는 것을 규정할 수 있습니다.

   ![근접 설명](../media/content-understanding/proximity.png)</br>

#### <a name="what-are-tokens"></a>토큰이란?

근사 설명 유형을 사용하려면 근접 설명이 두 개의 설명 간의 거리를 어떻게 측정하는지 토큰의 수로 알 수 있으므로 토큰이 무엇인지를 이해해야 합니다. 토큰은 문자와 숫자의 연속 범위(공백이나 문장 부호 제외)입니다. 

다음 표는 한 개의 구에서 토큰 수를 확인하는 방법에 대해 예를 보여 줍니다.

|구|토큰 수|설명|
|--|--|--|
|`Dog`|1|문장 부호나 공백이 없는 단일 단어입니다.|
|`RMT33W`|1|레코드 로케이터 번호 숫자와 문자가 포함될 수 있지만 문장 부호는 포함되어 있지 않습니다.|
|`425-555-5555`|5|전화 번호 각 문장 부호 기호는 단일 토큰이므로 `425-555-5555`의 경우 5개의 토큰이 될 수 있습니다.<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555` |
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`<br>|

#### <a name="configure-the-proximity-explanation-type"></a>근접 설명 유형 구성

샘플에 대한 근접 설정을 구성하여 *거리 주소 번호* 설명으로부터 *전화 번호* 설명의 토큰 수 범위를 알 수 있습니다. 전화 번호와 거리 주소 번호 사이에는 토큰이 없기 때문에 최소 범위는 "0" 이라는 것을 알 수 있습니다.

그러나 샘플 문서의 일부 전화 번호에는 *(휴대폰)* 이 추가되어 있습니다.

Nestor Wilke<br>
111-111-1111(휴대폰)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

*(휴대폰)* 에는 세 개의 토큰이 있습니다.

|구|토큰 수|
|--|--|
|(|1|
|휴대폰|2|
|)|3|

근접 설정이 0에서 3의 범위를 갖도록 구성합니다.

   ![근접의 예](../media/content-understanding/proximity-example.png)</br>

## <a name="use-explanation-templates"></a>설명 서식 파일 사용

설명에 대한 다양한 패턴 목록 값을 수동으로 추가할 수 있지만, 설명 라이브러리에서 미리 작성된 서식 파일을 찾아 사용하는 것이 훨씬 쉬울 수 있습니다.

예를 들어 *날짜* 에 대한 모든 변형을 수동으로 추가하는 대신 이미 여러 패턴 목록 값을 포함하고 있는 *날짜* 패턴 목록 서식 파일을 사용할 수 있습니다.</br>

   ![설명 라이브러리](../media/content-understanding/explanation-template.png)</br>
 
설명 라이브러리에는 다음을 비롯하여 일반적으로 사용되는 몇 가지 패턴 목록 설명이 포함되어 있습니다.</br>

- 날짜</br>
- 날짜(숫자)</br>
- 시간</br>
- 숫자</br>
- 전화 번호</br>
- 우편 번호</br>
- 문장의 첫 번째 단어</br>
- 신용카드</br>
- 주민등록번호</br>

또한 설명 라이브러리에는 다음을 포함한 구 목록 설명의 서식 파일도 포함하고 있습니다.
- 문장의 끝
- 통화

#### <a name="to-use-a-template-from-the-explanation-library"></a>설명 라이브러리에서 서식 파일을 사용하려면

1. 모델의 **교육** 페이지의 **설명** 구역에서 **신규** 를 선택한 다음 **서식 파일 사용** 을 선택합니다.</br>

   ![서식 파일로 만들기](../media/content-understanding/from-template.png)</br>

2.  **설명 서식 파일** 페이지에서 사용하려는 설명을 선택하고 **추가** 를 선택합니다.</br>

       ![서식 파일 선택](../media/content-understanding/phone-template.png)</br>

3. 선택한 서식 파일에 대한 정보는 **설명 만들기** 페이지에 나와 있습니다. 필요한 경우 설명 이름을 편집하고 패턴 목록에서 항목을 추가 또는 제거합니다. </br> 

   ![서식 파일 편집](../media/content-understanding/phone-template-live.png)</br>

4. 작업을 끝낸 후 **저장** 을 선택합니다.
