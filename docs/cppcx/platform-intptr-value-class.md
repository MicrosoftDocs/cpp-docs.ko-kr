---
title: Platform::IntPtr 값 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: eda65255aa76d6a801bdc0f80c437a9dc975d8f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449142"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr 값 클래스

플랫폼(32비트 또는 64비트)에 맞는 크기의 부호 있는 포인터 또는 핸들을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
public value struct IntPtr
```

### <a name="members"></a>멤버

IntPtr에는 다음과 같은 멤버가 있습니다.

|멤버|설명|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|IntPtr의 새 인스턴스를 초기화합니다.|
|[IntPtr::op_explicit 연산자](#op-explicit)|지정된 매개 변수를 IntPtr 또는 IntPtr 값에 대한 포인터로 변환합니다.|
|[IntPtr::ToInt32](#toint32)|현재 IntPtr을 32비트 정수로 변환합니다.|

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타데이터:** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr 생성자

지정된 값을 사용하여 IntPtr의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>매개 변수

*값*<br/>
64비트 핸들이나 포인터, 64비트 값 포인터 또는 64비트 값으로 변환할 수 있는 32비트 값입니다.

## <a name="op-explicit"> </a> IntPtr::op_explicit 연산자

지정된 매개 변수를 IntPtr 또는 IntPtr 값에 대한 포인터로 변환합니다.

### <a name="syntax"></a>구문

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>매개 변수

*Value1*<br/>
핸들 또는 IntPtr에 대한 포인터입니다.

*Value2*<br/>
IntPtr로 변환될 수 있는 32비트 정수입니다.

*value3*<br/>
IntPtr입니다.

### <a name="return-value"></a>반환 값

첫 번째 및 두 번째 연산자는 IntPtr을 반환합니다. 세 번째 연산자는 현재 IntPtr이 나타내는 값에 대한 포인터를 반환합니다.

## <a name="toint32"> </a> IntPtr::ToInt32 메서드

현재 IntPtr 값을 32비트 정수로 변환합니다.

### <a name="syntax"></a>구문

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>반환 값

32비트 정수입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](../cppcx/platform-namespace-c-cx.md)