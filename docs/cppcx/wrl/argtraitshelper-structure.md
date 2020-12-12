---
description: '자세히 알아보기: ArgTraitsHelper Structure'
title: ArgTraitsHelper 구조체
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: a749c48c72c837eb0898d32ddd08410b87918871
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175861"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>매개 변수

*TDelegateInterface*<br/>
대리자 인터페이스입니다.

## <a name="remarks"></a>설명

대리자 인수의 일반적인 특성을 정의 하는 데 도움이 됩니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name         | 설명
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)`의 동의어입니다.
`Traits`     | `ArgTraits<methodType>`의 동의어입니다.

### <a name="public-constants"></a>공용 상수

Name                           | 설명
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper:: args](#args) | [Argtraits:: args](#args) 대리자 인터페이스의 메서드에 있는 매개 변수 개수를 유지 `Invoke` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ArgTraitsHelper`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="argtraitshelperargs"></a><a name="args"></a> ArgTraitsHelper:: args

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>설명

`ArgTraitsHelper::args`대리자 인터페이스의 메서드에 대 한 매개 변수 개수를 유지 하는 데 도움이 됩니다 `Invoke` .
