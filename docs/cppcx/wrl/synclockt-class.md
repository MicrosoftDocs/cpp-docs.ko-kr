---
description: '자세히 알아보기: SyncLockT 클래스'
title: SyncLockT 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 289a31d87ce395be2d2a72a8fe062c9c0bfa8f56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135111"
---
# <a name="synclockt-class"></a>SyncLockT 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>매개 변수

*SyncTraits*<br/>
리소스의 소유권을 가져올 수 있는 형식입니다.

## <a name="remarks"></a>설명

리소스의 전용 또는 공유 소유권을 가져올 수 있는 형식을 나타냅니다.

예를 들어 `SyncLockT` 클래스는 [Srwlock](srwlock-class.md) 클래스를 구현 하는 데 도움이 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                      | 설명
----------------------------------------- | ----------------------------------------------------
[SyncLockT:: SyncLockT](#synclockt)        | `SyncLockT` 클래스의 새 인스턴스를 초기화합니다.
[SyncLockT:: ~ SyncLockT](#tilde-synclockt) | 클래스의 인스턴스를 초기화 하지 `SyncLockT` 않습니다.

### <a name="protected-constructors"></a>Protected 생성자

Name                               | 설명
---------------------------------- | ----------------------------------------------------
[SyncLockT:: SyncLockT](#synclockt) | `SyncLockT` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                             | 설명
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT:: IsLocked](#islocked) | 현재 `SyncLockT` 개체가 리소스를 소유 하 고 있는지 여부를 나타냅니다. 즉, `SyncLockT` 개체가 *잠겨* 있는지 여부를 나타냅니다.
[SyncLockT:: Unlock](#unlock)     | 현재 개체가 보유 하 고 있는 경우 해당 리소스의 제어 `SyncLockT` 를 해제 합니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                      | 설명
------------------------- | -------------------------------------------------------------------
[SyncLockT:: sync_](#sync) | 클래스로 표시 되는 기본 리소스를 보유 합니다 `SyncLockT` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SyncLockT`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼::D etails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a> SyncLockT:: ~ SyncLockT

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>설명

클래스의 인스턴스를 초기화 하지 `SyncLockT` 않습니다.

이 소멸자는 또한 현재 인스턴스의 잠금을 해제 `SyncLockT` 합니다.

## <a name="synclocktislocked"></a><a name="islocked"></a> SyncLockT:: IsLocked

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>반환 값

**`true`**`SyncLockT`개체가 잠겨 있으면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

현재 `SyncLockT` 개체가 리소스를 소유 하 고 있는지 여부를 나타냅니다. 즉, `SyncLockT` 개체가 *잠겨* 있는지 여부를 나타냅니다.

## <a name="synclocktsync_"></a><a name="sync"></a> SyncLockT:: sync_

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>설명

클래스로 표시 되는 기본 리소스를 보유 합니다 `SyncLockT` .

## <a name="synclocktsynclockt"></a><a name="synclockt"></a> SyncLockT:: SyncLockT

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 개체에 대 한 rvalue 참조 `SyncLockT` 입니다.

*동기화*<br/>
다른 개체에 대 한 참조 `SyncLockWithStatusT` 입니다.

### <a name="remarks"></a>설명

`SyncLockT` 클래스의 새 인스턴스를 초기화합니다.

첫 번째 생성자는 `SyncLockT` `SyncLockT` *다른* 매개 변수로 지정 된 다른 개체에서 현재 개체를 초기화 한 다음 다른 개체를 무효화 합니다 `SyncLockT` . 두 번째 생성자는이 **`protected`** 고 현재 개체를 `SyncLockT` 잘못 된 상태로 초기화 합니다.

## <a name="synclocktunlock"></a><a name="unlock"></a> SyncLockT:: Unlock

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void Unlock();
```

### <a name="remarks"></a>설명

현재 개체가 보유 하 고 있는 경우 해당 리소스의 제어 `SyncLockT` 를 해제 합니다.
