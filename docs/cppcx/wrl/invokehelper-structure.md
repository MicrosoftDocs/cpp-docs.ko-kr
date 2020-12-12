---
description: '자세히 알아보기: InvokeHelper Structure'
title: InvokeHelper 구조체
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 0b9bb8abb59cce5a3c25d795d0946ffbe88d0076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299022"
---
# <a name="invokehelper-structure"></a>InvokeHelper 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>매개 변수

*TDelegateInterface*<br/>
대리자 인터페이스 형식입니다.

*TCallback*<br/>
이벤트 처리기 함수의 형식입니다.

*argCount*<br/>
특수화의 인수 개수 `InvokeHelper` 입니다.

## <a name="remarks"></a>설명

`Invoke()`지정 된 인수 개수 및 형식을 기반으로 하는 메서드의 구현을 제공 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name     | 설명
-------- | -----------------------------------------------------------------------------
`Traits` | 각 이벤트 처리기 인수의 형식을 정의 하는 클래스의 동의어입니다.

### <a name="public-constructors"></a>Public 생성자

이름                                        | 설명
------------------------------------------- | -------------------------------------------------------
[InvokeHelper:: InvokeHelper](#invokehelper) | `InvokeHelper` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                            | 설명
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper:: Invoke](#invoke) | 지정 된 수의 인수를 포함 하는 시그니처를 가진 이벤트 처리기를 호출 합니다.

### <a name="public-data-members"></a>공용 데이터 멤버

Name                                 | 설명
------------------------------------ | ----------------------------------------------------------
[InvokeHelper:: callback_](#callback) | 이벤트가 발생할 때 호출할 이벤트 처리기를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`InvokeHelper`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="invokehelpercallback_"></a><a name="callback"></a> InvokeHelper:: callback_

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>설명

이벤트가 발생할 때 호출할 이벤트 처리기를 나타냅니다.

`TCallback`템플릿 매개 변수는 이벤트 처리기의 유형을 지정 합니다.

## <a name="invokehelperinvoke"></a><a name="invoke"></a> InvokeHelper:: Invoke

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>매개 변수

*arg1*<br/>
인수 1.

*arg2*<br/>
인수 2.

*arg3*<br/>
인수 3.

*arg4*<br/>
인수 4.

*arg5*<br/>
인수 5.

*arg6*<br/>
인수 6.

*arg7*<br/>
인수 7.

*arg8*<br/>
인수 8.

*arg9*<br/>
인수 9.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류를 설명 하는 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 수의 인수를 포함 하는 시그니처를 가진 이벤트 처리기를 호출 합니다.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a> InvokeHelper:: InvokeHelper

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>매개 변수

*콜백(callback)*<br/>
이벤트 처리기입니다.

### <a name="remarks"></a>설명

`InvokeHelper` 클래스의 새 인스턴스를 초기화합니다.

`TCallback`템플릿 매개 변수는 이벤트 처리기의 유형을 지정 합니다.
