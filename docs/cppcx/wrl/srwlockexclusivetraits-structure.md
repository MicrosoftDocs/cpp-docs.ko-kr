---
description: '자세히 알아보기: SRWLockExclusiveTraits Structure'
title: SRWLockExclusiveTraits 구조체
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: 135d4f866d1ca32ee9170ef9844cb0bf8d38c29a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186209"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 구조체

배타 잠금 모드의 클래스에 대 한 일반적인 특성에 대해 설명 합니다 `SRWLock` .

## <a name="syntax"></a>구문

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name   | 설명
------ | --------------------------------------------------------------------------
`Type` | [Srwlock](srwlock-class.md) 클래스에 대 한 포인터의 동의어입니다.

### <a name="public-methods"></a>Public 메서드

이름                                                        | 설명
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits:: GetInvalidValue](#getinvalidvalue) | `SRWLockExclusiveTraits`항상 유효 하지 않은 개체를 검색 합니다.
[SRWLockExclusiveTraits:: Unlock](#unlock)                   | 지정 된 개체의 단독 제어를 해제 `SRWLock` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SRWLockExclusiveTraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> SRWLockExclusiveTraits:: GetInvalidValue

`SRWLockExclusiveTraits`항상 유효 하지 않은 개체를 검색 합니다.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>반환 값

빈 `SRWLockExclusiveTraits` 개체입니다.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a> SRWLockExclusiveTraits:: Unlock

지정 된 개체의 단독 제어를 해제 `SRWLock` 합니다.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>매개 변수

*srwlock*<br/>
개체에 대 한 핸들 `SRWLock` 입니다.
