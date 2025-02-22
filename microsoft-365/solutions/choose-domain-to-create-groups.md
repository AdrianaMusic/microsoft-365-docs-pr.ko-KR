---
title: Microsoft 365 그룹을 만들 때 사용할 도메인 선택
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
description: PowerShell을 사용하여 전자 메일 주소 정책을 구성하여 Microsoft 365 그룹을 만들 때 사용할 도메인을 선택하는 방법을 학습합니다.
ms.openlocfilehash: 1e56268c3994b1ac822869d154be826326039bfc
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49612943"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Microsoft 365 그룹을 만들 때 사용할 도메인 선택

일부 조직에서는 별도의 전자 메일 도메인을 사용하여 비즈니스의 여러 부분을 분류합니다. 사용자가 Microsoft 365 그룹을 만들 때 사용할 도메인을 지정할 수 있습니다.
  
조직에서 사용자가 비즈니스의 기본 허용 도메인이 다른 도메인에 그룹을 만들어야 하는 경우 PowerShell을 사용하여 EAP(전자 메일 주소 정책)를 구성하여 이를 허용할 수 있습니다.

PowerShell cmdlet을 실행하려면 먼저 조직과 대화할 수 있는 모듈을 다운로드하여 설치합니다. 원격 [PowerShell을 사용하여 Exchange Online에 연결합니다.](https://go.microsoft.com/fwlink/p/?LinkId=785881)

## <a name="example-scenarios"></a>예제 시나리오

비즈니스의 주 도메인이 기본 도메인으로 설정되어 있는 경우를 Contoso.com. 그러나 조직의 기본 허용 도메인은 service.contoso.com. 즉, 그룹이 service.contoso.com(예: jimsteam@service.contoso.com).
  
조직에 하위 도메인도 구성했다고 하자. 이러한 도메인에서 그룹을 만들 수 있습니다.
  
- students.contoso.com 위한 지원
    
- faculty.contoso.com 구성원용 관리
    
다음 두 시나리오에서는 이 작업을 어떻게 수행할지 설명합니다.

> [!NOTE]
> MULITPLEEAP가 있는 경우 우선 순위 순서대로 평가됩니다. 값이 1이면 우선 순위가 가장 높은 것입니다. EAP가 일치하면 더 이상 EAP가 평가되는 것이 아니며 그룹에서 스탬프가 매칭되는 주소는 일치하는 EAP에 따라 사용됩니다. > 조건과 일치하는EAP가 없는 경우 조직의 기본 허용 도메인에서 그룹이 프로비전됩니다. 허용 [도메인을](https://go.microsoft.com/fwlink/p/?LinkId=785428) 추가하는 방법에 대한 자세한 내용은 Exchange Online에서 허용 도메인 관리를 참조하세요.
  
### <a name="scenario-1"></a>시나리오 1

다음 예에서는 조직의 모든 Microsoft 365 그룹을 조직 도메인에 프로비전하는 groups.contoso.com 보여줍니다.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>시나리오 2

Microsoft 365 그룹이 생성되는 하위 도메인을 제어하려는 경우를 제어합니다. 당신은 원합니다:
  
- 학생(Department가 학생으로  설정된 사용자)이 students.groups.contoso.com 그룹입니다.  다음 명령을 사용하세요.
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- 교직원 도메인에서 교직원(부서가 교직원으로 설정되어 있는 사용자 또는 전자 메일 주소에 **faculty.contoso.com)에** 의해 faculty.groups.contoso.com 그룹입니다.  다음 명령을 사용하세요.
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- 다른 사용자가 만든 그룹은 groups.contoso.com 도메인에 만들어집니다. 다음 명령을 사용하세요.
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>전자 메일 주소 정책 변경

기존 EAP의 우선 순위 또는 전자 메일 주소 템플릿을 변경하기 위해 Set-EmailAddressPolicy cmdlet을 사용하세요.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

EAP를 변경하는 경우 이미 프로비전된 그룹에는 영향이 없습니다.
  
## <a name="delete-email-address-policies"></a>전자 메일 주소 정책 삭제

EAP를 삭제하려면 Remove-EmailAddressPolicy cmdlet을 사용 합니다.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

EAP를 변경하는 경우 이미 프로비전된 그룹에는 영향이 없습니다.
  
## <a name="hybrid-requirements"></a>하이브리드 요구 사항

조직이 하이브리드 시나리오에서 구성된 경우 조직이 [Microsoft 365](https://docs.microsoft.com/exchange/hybrid-deployment/set-up-microsoft-365-groups) 그룹을 만들기 위한 요구 사항을 충족하는지 확인하도록 Microsoft 365 그룹 구성을(를) 확인할 수 있습니다. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>전자 메일 주소 정책 그룹 사용에 대한 추가 정보:

알아야 할 몇 가지 사항도 있습니다.
  
- 그룹이 만들어지는 속도는 조직에 구성된EAP 수에 따라 달라 졌습니다.
    
- 관리자와 사용자는 그룹을 만들 때 도메인을 수정할 수도 있습니다.
    
- 사용자 그룹은 이미 사용 가능한 표준 쿼리(사용자 속성)를 사용하여 결정됩니다. 지원되는 필터링 가능한 속성에 [대해 -RecipientFilter 매개](https://docs.microsoft.com/powershell/exchange/recipientfilter-properties) 변수에 대해 필터링할 수 있는 속성을 체크 아웃합니다. 
    
- 그룹에 대해 EAP를 구성하지 않은 경우 그룹 만들기를 위해 기본 허용 도메인이 선택됩니다.
    
- 허용 도메인을 제거하면 먼저 EAP를 업데이트해야 합니다. 그렇지 않으면 그룹 프로비전이 영향을 하게 됩니다.
    
- 조직에 대해 최대 100개 전자 메일 주소 정책을 구성할 수 있습니다.
    
## <a name="related-articles"></a>관련 문서

[공동 작업 거버넌스 계획 단계별](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[공동 작업 거버넌스 계획 만들기](collaboration-governance-first.md)

[관리 센터에서 Microsoft 365 그룹 만들기](https://docs.microsoft.com/microsoft-365/admin/create-groups/create-groups)
