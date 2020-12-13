---
description: '자세히 알아보기: SemaphoreTraits Structure'
title: SemaphoreTraits 구조체
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 5779a30d22fd2d32e57f96f752bb52e2bf469cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135228"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 구조체

개체의 공통 특성을 정의 `Semaphore` 합니다.

## <a name="syntax"></a>구문

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

이름                               | 설명
---------------------------------- | --------------------------------------
[SemaphoreTraits:: Unlock](#unlock) | 공유 리소스의 제어를 해제 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a> SemaphoreTraits:: Unlock

공유 리소스의 제어를 해제 합니다.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
개체에 대 한 핸들 `Semaphore` 입니다.

### <a name="remarks"></a>설명

잠금 해제 작업이 실패 하면에서 오류의 `Unlock()` 원인을 나타내는 오류를 내보냅니다.
