---
description: '자세히 알아보기: MutexTraits Structure'
title: MutexTraits 구조체
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: e3dfcee1251794734ed5cf787096361403d80c7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330825"
---
# <a name="mutextraits-structure"></a>MutexTraits 구조체

[뮤텍스](mutex-class.md) 클래스의 공통 특성을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

이름                           | 설명
------------------------------ | ------------------------------------------------
[MutexTraits:: Unlock](#unlock) | 공유 리소스에 대 한 단독 제어를 해제 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a> MutexTraits:: Unlock 메서드

공유 리소스에 대 한 단독 제어를 해제 합니다.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
뮤텍스 개체에 대 한 핸들입니다.
