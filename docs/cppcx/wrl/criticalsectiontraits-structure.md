---
description: '자세히 알아보기: CriticalSectionTraits Structure'
title: CriticalSectionTraits 구조체
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 20e4b7dd47acf6f632c888c9bfdedeb3f4e60270
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272944"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 구조체

잘못 된 `CriticalSection` 임계 영역을 지 원하는 개체 또는 임계 영역을 해제 하는 함수를 특수화 합니다.

## <a name="syntax"></a>구문

```
struct CriticalSectionTraits;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name   | 설명
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | **`typedef`** 임계 영역에 대 한 포인터를 정의 하는입니다. `Type`는 `typedef CRITICAL_SECTION* Type;`으로 정의됩니다.

### <a name="public-methods"></a>Public 메서드

이름                                                       | 설명
---------------------------------------------------------- | -----------------
[CriticalSectionTraits:: GetInvalidValue](#getinvalidvalue) | 템플릿이 `CriticalSection` 항상 유효 하지 않도록 템플릿을 전문적으로 만듭니다.
[CriticalSectionTraits:: Unlock](#unlock)                   | 지정 된 `CriticalSection` 임계 영역 개체의 소유권 해제를 지원 하도록 템플릿을 특수화 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CriticalSectionTraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> CriticalSectionTraits:: GetInvalidValue

템플릿이 `CriticalSection` 항상 유효 하지 않도록 템플릿을 전문적으로 만듭니다.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>반환 값

는 항상 잘못 된 임계 영역에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

`Type`한정자는로 정의 됩니다 `typedef CRITICAL_SECTION* Type;` .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a> CriticalSectionTraits:: Unlock

지정 된 `CriticalSection` 임계 영역 개체의 소유권 해제를 지원 하도록 템플릿을 특수화 합니다.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>매개 변수

*양방향*<br/>
임계 영역 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`Type`한정자는로 정의 됩니다 `typedef CRITICAL_SECTION* Type;` .

자세한 내용은 Windows API 설명서의 **동기화 함수** 섹션에서 **LeaveCriticalSection 함수** 를 참조 하세요.
