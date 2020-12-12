---
description: '자세한 정보: Platform:: Box 클래스'
title: Platform::Box 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: cbfe8ec70f2ef4c58bf2c9459f2d0c4722817810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284059"
---
# <a name="platformbox-class"></a>Platform::Box 클래스

같은 값 형식이 `Windows::Foundation::DateTime` 나와 같은 스칼라 형식을 **`int`** 형식에 저장할 수 있도록 `Platform::Object` 합니다. 값 형식을 `Box` 으로 캐스팅할 때 boxing이 암시적으로 발생하므로 일반적으로 `Object^`를 명시적으로 사용할 필요가 없습니다.

### <a name="syntax"></a>Syntax

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>요구 사항

**헤더:** vccorlib.h

**네임스페이스:** Platform

### <a name="members"></a>멤버

|멤버|설명|
|------------|-----------------|
|[Box](#ctor) | 지정된 형식의 값을 캡슐화할 수 있는 `Box`를 만듭니다. |
|[연산자 상자 &lt; Const T&gt;^](#box-const-t) | **`const`** 값 클래스 `T` 또는 **`enum`** 클래스에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` . |
|[연산자 상자 &lt; const Volatile T&gt;^](#box-const-volatile-t) | **`const volatile`** 값 클래스 `T` 또는 **`enum`** 형식에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` . |
|[연산자 상자 &lt; T&gt;^](#box-t) | 값 클래스 `T`를 `Box<T>`로 boxing 변환할 수 있습니다. |
|[연산자 Box &lt; 휘발성 T&gt;^](#box-volatile-t) | **`volatile`** 값 클래스 `T` 또는 **`enum`** 형식에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` . |
|[Box:: operator T](#t) | 값 클래스 또는 클래스에서로 boxing 변환할 수 있습니다 `T` **`enum`** `T` `Box<T>` . |
|[Value 속성](#value) | `Box` 개체에 캡슐화된 값을 반환합니다. |

## <a name="boxbox-constructor"></a><a name="ctor"></a> Box:: Box 생성자

지정된 형식의 값을 캡슐화할 수 있는 `Box`를 만듭니다.

### <a name="syntax"></a>구문

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>매개 변수

*이상*<br/>
Boxing 할 값의 형식입니다 (예:,, **`int`** **`bool`** ,) `float64` `DateTime` .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a> Box:: operator Box &lt; Const T &gt; ^ 연산자

**`const`** 값 클래스 `T` 또는 **`enum`** 클래스에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` .

### <a name="syntax"></a>구문

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
모든 값 클래스, 값 구조체 또는 열거형 형식입니다. [기본 네임 스페이스](../cppcx/default-namespace.md)에 기본 제공 형식을 포함 합니다.

### <a name="return-value"></a>반환 값

`Platform::Box<T>^`Ref 클래스에서 boxing 된 원래 값을 나타내는 인스턴스입니다.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a> Box:: operator Box &lt; const Volatile T &gt; ^ 연산자

**`const volatile`** 값 클래스 `T` 또는 **`enum`** 형식에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` .

### <a name="syntax"></a>구문

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
모든 열거형 형식, 값 클래스 또는 값 구조체입니다. [기본 네임 스페이스](../cppcx/default-namespace.md)에 기본 제공 형식을 포함 합니다.

### <a name="return-value"></a>반환 값

`Platform::Box<T>^`Ref 클래스에서 boxing 된 원래 값을 나타내는 인스턴스입니다.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a> Box:: operator Box &lt; T &gt; ^ 연산자

값 클래스 `T`를 `Box<T>`로 boxing 변환할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
모든 열거형 형식, 값 클래스 또는 값 구조체입니다. [기본 네임 스페이스](../cppcx/default-namespace.md)에 기본 제공 형식을 포함 합니다.

### <a name="return-value"></a>반환 값

`Platform::Box<T>^`Ref 클래스에서 boxing 된 원래 값을 나타내는 인스턴스입니다.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a> Box:: operator Box &lt; Volatile T &gt; ^ 연산자

**`volatile`** 값 클래스 `T` 또는 **`enum`** 형식에서 `T` 로 boxing 변환할 수 있습니다 `Box<T>` .

### <a name="syntax"></a>구문

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
모든 열거형 형식, 값 클래스 또는 값 구조체입니다. [기본 네임 스페이스](../cppcx/default-namespace.md)에 기본 제공 형식을 포함 합니다.

### <a name="return-value"></a>반환 값

`Platform::Box<T>^`Ref 클래스에서 boxing 된 원래 값을 나타내는 인스턴스입니다.

## <a name="boxoperator-t-operator"></a><a name="t"></a> Box:: operator T 연산자

값 클래스 또는 클래스에서로 boxing 변환할 수 있습니다 `T` **`enum`** `T` `Box<T>` .

### <a name="syntax"></a>구문

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
모든 열거형 형식, 값 클래스 또는 값 구조체입니다. [기본 네임 스페이스](../cppcx/default-namespace.md)에 기본 제공 형식을 포함 합니다.

### <a name="return-value"></a>반환 값

`Platform::Box<T>^`Ref 클래스에서 boxing 된 원래 값을 나타내는 인스턴스입니다.

## <a name="boxvalue-property"></a><a name="value"></a> Box:: Value 속성

`Box` 개체에 캡슐화된 값을 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Return Value

boxing되기 전 형식의 boxed 값을 반환합니다.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)<br/>
[boxing](../cppcx/boxing-c-cx.md)
