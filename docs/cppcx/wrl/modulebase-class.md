---
description: '다음에 대 한 자세한 정보: ModuleBase 클래스'
title: ModuleBase 클래스
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 6540068cee62da5d1a9039a15bcb5bd53ff3aea2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186248"
---
# <a name="modulebase-class"></a>ModuleBase 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class ModuleBase;
```

## <a name="remarks"></a>설명

[모듈](module-class.md) 클래스의 기본 클래스를 나타냅니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                         | 설명
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase:: ModuleBase](#modulebase)        | `Module` 클래스의 인스턴스를 초기화합니다.
[ModuleBase:: ~ ModuleBase](#tilde-modulebase) | 클래스의 현재 인스턴스를 초기화 `Module` 합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                      | 설명
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::D ecrementObjectCount](#decrementobjectcount) | 구현 시 모듈에서 추적 하는 개체 수를 줄입니다.
[ModuleBase:: IncrementObjectCount](#incrementobjectcount) | 구현 시 모듈에서 추적 하는 개체 수를 늘립니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ModuleBase`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a> ModuleBase:: ~ ModuleBase

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>설명

클래스의 현재 인스턴스를 초기화 `ModuleBase` 합니다.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a> ModuleBase::D ecrementObjectCount

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>반환 값

감소 작업 전 수입니다.

### <a name="remarks"></a>설명

구현 시 모듈에서 추적 하는 개체 수를 줄입니다.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a> ModuleBase:: IncrementObjectCount

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>반환 값

증가 연산 전 수입니다.

### <a name="remarks"></a>설명

구현 시 모듈에서 추적 하는 개체 수를 늘립니다.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a> ModuleBase:: ModuleBase

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ModuleBase();
```

### <a name="remarks"></a>설명

`Module` 클래스의 인스턴스를 초기화합니다.
