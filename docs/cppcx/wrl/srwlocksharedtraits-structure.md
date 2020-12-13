---
description: '다음에 대 한 자세한 정보: SRWLockSharedTraits 구조'
title: SRWLockSharedTraits 구조체
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: 2cdfbd584adeffc9dedd8504d9183d6c5d4c1a95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135124"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 구조체

공유 잠금 모드의 클래스에 대 한 일반적인 특성을 설명 `SRWLock` 합니다.

## <a name="syntax"></a>구문

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name   | 설명
------ | --------------------------------------------------------------------------
`Type` | [Srwlock](srwlock-class.md) 클래스에 대 한 포인터의 동의어입니다.

### <a name="public-methods"></a>Public 메서드

이름                                                     | 설명
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits:: GetInvalidValue](#getinvalidvalue) | `SRWLockSharedTraits`항상 유효 하지 않은 개체를 검색 합니다.
[SRWLockSharedTraits:: Unlock](#unlock)                   | 지정 된 개체의 단독 제어를 해제 `SRWLock` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SRWLockSharedTraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> SRWLockSharedTraits:: GetInvalidValue

`SRWLockSharedTraits`항상 유효 하지 않은 개체를 검색 합니다.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>반환 값

개체에 대 한 핸들 `SRWLockSharedTraits` 입니다.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a> SRWLockSharedTraits:: Unlock

지정 된 개체의 단독 제어를 해제 `SRWLock` 합니다.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>매개 변수

*srwlock*<br/>
개체에 대 한 핸들 `SRWLock` 입니다.
