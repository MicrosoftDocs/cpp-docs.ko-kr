---
description: '다음에 대 한 자세한 정보: ArgTraits 구조'
title: ArgTraits 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: b44cd1ff8d5aa4355385629cc08321dfe353e24c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175913"
---
# <a name="argtraits-structure"></a>ArgTraits 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>매개 변수

*TMemberFunction*<br/>
메서드 시그니처와 일치 시킬 수 없는 ArgTraits 구조체의 Typename 매개 변수 `Invoke` 입니다.

*TDelegateInterface*<br/>
대리자 인터페이스입니다.

*TArg1*<br/>
메서드의 첫 번째 인수 형식입니다 `Invoke` .

*TArg2*<br/>
메서드의 두 번째 인수 형식입니다 `Invoke` .

*TArg3*<br/>
메서드의 세 번째 인수 형식입니다 `Invoke` .

*TArg4*<br/>
메서드의 네 번째 인수 형식입니다 `Invoke` .

*TArg5*<br/>
메서드의 다섯 번째 인수 형식입니다 `Invoke` .

*TArg6*<br/>
메서드의 여섯 번째 인수 형식입니다 `Invoke` .

*TArg7*<br/>
메서드의 일곱 번째 인수 형식입니다 `Invoke` .

*TArg8*<br/>
메서드의 여덟 번째 인수 형식입니다 `Invoke` .

*TArg9*<br/>
메서드의 아홉 번째 인수 형식입니다 `Invoke` .

## <a name="remarks"></a>설명

구조체는 지정 된 `ArgTraits` 대리자 인터페이스와 지정 된 수의 매개 변수를 포함 하는 익명 멤버 함수를 선언 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name       | 설명
---------- | ----------------------
`Arg1Type` | TArg1에 대 한 typedef입니다.
`Arg2Type` | TArg2에 대 한 typedef입니다.
`Arg3Type` | TArg3에 대 한 typedef입니다.
`Arg4Type` | TArg4에 대 한 typedef입니다.
`Arg5Type` | TArg5에 대 한 typedef입니다.
`Arg6Type` | TArg6에 대 한 typedef입니다.
`Arg7Type` | TArg7에 대 한 typedef입니다.
`Arg8Type` | TArg8에 대 한 typedef입니다.
`Arg9Type` | TArg9에 대 한 typedef입니다.

### <a name="public-constants"></a>공용 상수

Name                     | 설명
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits:: args](#args) | 대리자 인터페이스의 메서드에 매개 변수 개수를 유지 `Invoke` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ArgTraits`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="argtraitsargs"></a><a name="args"></a> ArgTraits:: args

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>설명

대리자 인터페이스의 메서드에 매개 변수 개수를 유지 `Invoke` 합니다. `args`가-1 이면 메서드 시그니처와 일치 하는 항목이 없을 수 있습니다 `Invoke` .
