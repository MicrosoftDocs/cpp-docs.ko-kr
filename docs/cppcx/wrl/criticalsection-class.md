---
description: '자세히 알아보기: CriticalSection 클래스'
title: CriticalSection 클래스
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: e570dfaef8fcf16084792d205fc3e322cf8be908
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273035"
---
# <a name="criticalsection-class"></a>CriticalSection 클래스

임계 영역 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class CriticalSection;
```

## <a name="members"></a>멤버

### <a name="constructor"></a>생성자

Name                                                        | 설명
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: CriticalSection](#criticalsection)        | 뮤텍스 개체와 유사하지만 단일 프로세스의 스레드에만 사용할 수 있는 동기화 개체를 초기화합니다.
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | 현재 개체를 초기화 및 소멸 시킵니다 `CriticalSection` .

### <a name="public-methods"></a>Public 메서드

이름                                 | 설명
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: IsValid](#isvalid) | 현재 임계 영역이 유효한지 여부를 나타냅니다.
[CriticalSection:: Lock](#lock)       | 지정된 임계 영역 개체의 소유권을 기다립니다. 함수가 호출 스레드가 소유권을 부여받는 시기를 반환합니다.
[CriticalSection:: Trlock](#trylock) | 차단 하지 않고 임계 영역을 입력 하려고 합니다. 호출에 성공 하면 호출 스레드는 임계 영역에 대 한 소유권을 갖습니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                        | 설명
--------------------------- | ----------------------------------------
[CriticalSection:: cs_](#cs) | 임계 영역 데이터 멤버를 선언합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CriticalSection`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a> CriticalSection:: ~ CriticalSection

현재 개체를 초기화 및 소멸 시킵니다 `CriticalSection` .

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a> CriticalSection:: CriticalSection

뮤텍스 개체와 유사하지만 단일 프로세스의 스레드에만 사용할 수 있는 동기화 개체를 초기화합니다.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>매개 변수

*spincount*<br/>
임계 영역 개체의 스핀 수입니다. 기본값은 0입니다.

### <a name="remarks"></a>설명

임계 영역 및 스핀에 대 한 자세한 내용은 `InitializeCriticalSectionAndSpinCount` `Synchronization` Windows API 설명서의 섹션에서 함수를 참조 하세요.

## <a name="criticalsectioncs_"></a><a name="cs"></a> CriticalSection:: cs_

임계 영역 데이터 멤버를 선언합니다.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>설명

이 데이터 멤버가 보호됩니다.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a> CriticalSection:: IsValid

현재 임계 영역이 유효한지 여부를 나타냅니다.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>반환 값

기본적으로는 항상를 반환 **`true`** 합니다.

## <a name="criticalsectionlock"></a><a name="lock"></a> CriticalSection:: Lock

지정된 임계 영역 개체의 소유권을 기다립니다. 함수가 호출 스레드가 소유권을 부여받는 시기를 반환합니다.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>매개 변수

*양방향*<br/>
사용자가 지정한 임계 영역 개체입니다.

### <a name="return-value"></a>반환 값

현재 임계 영역의 잠금을 해제하는 데 사용할 수 있는 잠금 개체입니다.

### <a name="remarks"></a>설명

첫 번째 `Lock` 함수는 현재 임계 영역 개체에 영향을 미칩니다. 두 번째 `Lock` 함수는 사용자가 지정한 임계 영역에 영향을 미칩니다.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a> CriticalSection:: Trlock

차단 하지 않고 임계 영역을 입력 하려고 합니다. 호출에 성공 하면 호출 스레드는 임계 영역에 대 한 소유권을 갖습니다.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>매개 변수

*양방향*<br/>
사용자가 지정한 임계 영역 개체입니다.

### <a name="return-value"></a>반환 값

임계 영역을 성공적으로 입력 했거나 현재 스레드가 임계 영역을 이미 소유 하 고 있는 경우 0이 아닌 값입니다. 다른 스레드가 임계 영역을 이미 소유 하 고 있으면 0입니다.

### <a name="remarks"></a>설명

첫 번째 `TryLock` 함수는 현재 임계 영역 개체에 영향을 미칩니다. 두 번째 `TryLock` 함수는 사용자가 지정한 임계 영역에 영향을 미칩니다.
