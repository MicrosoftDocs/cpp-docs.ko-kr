---
description: '다음에 대 한 자세한 정보: SRWLock 클래스'
title: SRWLock 클래스
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: 10bc3dc700f90d5154ece1546cdf3ec464ea6e56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135189"
---
# <a name="srwlock-class"></a>SRWLock 클래스

슬림 판독기/작성기 잠금을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class SRWLock;
```

## <a name="remarks"></a>설명

슬림형 판독기/writer 잠금은 스레드 간 액세스를 개체 또는 리소스에 동기화 하는 데 사용 됩니다. 자세한 내용은 [동기화 함수](/windows/win32/Sync/synchronization-functions)를 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name                | 설명
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | `SRWLock`Exclusive 모드로 획득 된 개체의 동의어입니다.
`SyncLockShared`    | `SRWLock`공유 모드로 획득 된 개체의 동의어입니다.

### <a name="public-constructors"></a>Public 생성자

이름                                     | 설명
---------------------------------------- | --------------------------------------------------
[SRWLock:: SRWLock](#srwlock-constructor) | `SRWLock` 클래스의 새 인스턴스를 초기화합니다.
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | 클래스의 인스턴스를 초기화 하지 `SRWLock` 않습니다.

### <a name="public-methods"></a>Public 메서드

이름                                           | 설명
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock:: LockExclusive](#lockexclusive)       | `SRWLock`단독 모드에서 개체를 가져옵니다.
[SRWLock:: LockShared](#lockshared)             | `SRWLock`공유 모드에서 개체를 가져옵니다.
[SRWLock:: TryLockExclusive](#trylockexclusive) | `SRWLock`현재 또는 지정 된 개체에 대해 배타 모드로 개체를 가져오려고 시도 `SRWLock` 합니다.
[SRWLock:: TryLockShared](#trylockshared)       | `SRWLock`현재 또는 지정 된 개체에 대해 공유 모드에서 개체를 가져오려고 시도 `SRWLock` 합니다.

### <a name="protected-data-member"></a>보호 된 데이터 멤버

Name                                      | 설명
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock:: SRWLock_](#srwlock-data-member) | 현재 개체에 대 한 기본 잠금 변수를 포함 합니다 `SRWLock` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SRWLock`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a> SRWLock:: ~ SRWLock

클래스의 인스턴스를 초기화 하지 `SRWLock` 않습니다.

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a> SRWLock:: LockExclusive

`SRWLock`단독 모드에서 개체를 가져옵니다.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
개체에 대 한 포인터 `SRWLock` 입니다.

### <a name="return-value"></a>반환 값

`SRWLock`Exclusive 모드의 개체입니다.

## <a name="srwlocklockshared"></a><a name="lockshared"></a> SRWLock:: LockShared

`SRWLock`공유 모드에서 개체를 가져옵니다.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
개체에 대 한 포인터 `SRWLock` 입니다.

### <a name="return-value"></a>반환 값

`SRWLock`공유 모드의 개체입니다.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a> SRWLock:: SRWLock

`SRWLock` 클래스의 새 인스턴스를 초기화합니다.

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a> SRWLock:: SRWLock_

현재 개체에 대 한 기본 잠금 변수를 포함 합니다 `SRWLock` .

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a> SRWLock:: TryLockExclusive

`SRWLock`현재 또는 지정 된 개체에 대해 배타 모드로 개체를 가져오려고 시도 `SRWLock` 합니다. 호출에 성공 하면 호출 스레드는 잠금의 소유권을 갖습니다.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
개체에 대 한 포인터 `SRWLock` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 `SRWLock` 전용 모드의 개체와 호출 스레드가 잠금의 소유권을 갖습니다. 그렇지 않으면 `SRWLock` 상태가 잘못 된 개체입니다.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a> SRWLock:: TryLockShared

`SRWLock`현재 또는 지정 된 개체에 대해 공유 모드에서 개체를 가져오려고 시도 `SRWLock` 합니다.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
개체에 대 한 포인터 `SRWLock` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 `SRWLock` 공유 모드의 개체와 호출 스레드가 잠금의 소유권을 갖습니다. 그렇지 않으면 `SRWLock` 상태가 잘못 된 개체입니다.
