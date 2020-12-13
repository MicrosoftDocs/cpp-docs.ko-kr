---
description: '자세한 정보: MakeAllocator 클래스'
title: MakeAllocator 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: c4e550dec37096a5ff6a41eccd4eb41968721a7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344525"
---
# <a name="makeallocator-class"></a>MakeAllocator 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
형식 이름.

*hasWeakReferenceSupport*<br/>
**`true`** 약한 참조를 지 원하는 개체에 대해 메모리를 할당 하려면 **`false`** 약한 참조를 지원 하지 않는 개체에 대해 메모리를 할당 합니다.

## <a name="remarks"></a>설명

약한 참조 지원을 사용 하거나 사용 하지 않고 활성화 가능한 클래스에 대해 메모리를 할당 합니다.

클래스를 재정의 `MakeAllocator` 하 여 사용자 정의 메모리 할당 모델을 구현 합니다.

`MakeAllocator` 는 일반적으로 생성 중에 개체가 throw 되는 경우 메모리 누수를 방지 하는 데 사용 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                  | 설명
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator:: MakeAllocator](#makeallocator)        | `MakeAllocator` 클래스의 새 인스턴스를 초기화합니다.
[MakeAllocator:: ~ MakeAllocator](#tilde-makeallocator) | 클래스의 현재 인스턴스를 초기화 `MakeAllocator` 합니다.

### <a name="public-methods"></a>Public 메서드

이름                                 | 설명
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator:: Allocate](#allocate) | 메모리를 할당 하 고 현재 개체와 연결 `MakeAllocator` 합니다.
[MakeAllocator::D etach](#detach)     | 현재 개체에서 [Allocate](#allocate) 메서드에 의해 할당 된 메모리를 분리 `MakeAllocator` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`MakeAllocator`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="makeallocatorallocate"></a><a name="allocate"></a> MakeAllocator:: Allocate

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>반환 값

성공 하면 할당 된 메모리에 대 한 포인터입니다. 그렇지 않으면 **`nullptr`** 입니다.

### <a name="remarks"></a>설명

메모리를 할당 하 고 현재 개체와 연결 `MakeAllocator` 합니다.

할당 된 메모리의 크기는 현재 템플릿 매개 변수에 지정 된 형식의 크기입니다 `MakeAllocator` .

개발자는 메서드를 재정의 하 여 `Allocate()` 다른 메모리 할당 모델을 구현 해야 합니다.

## <a name="makeallocatordetach"></a><a name="detach"></a> MakeAllocator::D etach

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>설명

현재 개체에서 [Allocate](#allocate) 메서드에 의해 할당 된 메모리를 분리 `MakeAllocator` 합니다.

를 호출 하는 경우 `Detach()` 메서드에서 제공 하는 메모리를 삭제 해야 `Allocate` 합니다.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a> MakeAllocator:: MakeAllocator

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>설명

`MakeAllocator` 클래스의 새 인스턴스를 초기화합니다.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a> MakeAllocator:: ~ MakeAllocator

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>설명

클래스의 현재 인스턴스를 초기화 `MakeAllocator` 합니다.

또한이 소멸자는 필요한 경우 할당 된 기본 메모리를 삭제 합니다.
