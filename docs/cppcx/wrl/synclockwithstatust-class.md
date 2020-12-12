---
description: '자세히 알아보기: SyncLockWithStatusT 클래스'
title: SyncLockWithStatusT 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 6a19ae22253fddd48c7baaf29e4b88a4863b89bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186157"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>매개 변수

*SyncTraits*<br/>
리소스의 전용 또는 공유 소유권을 가져올 수 있는 형식입니다.

## <a name="remarks"></a>설명

리소스의 전용 또는 공유 소유권을 가져올 수 있는 형식을 나타냅니다.

`SyncLockWithStatusT`클래스는 [뮤텍스](mutex-class.md) 및 [세마포](semaphore-class.md) 클래스를 구현 하는 데 사용 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                             | 설명
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT:: SyncLockWithStatusT](#synclockwithstatust) | `SyncLockWithStatusT` 클래스의 새 인스턴스를 초기화합니다.

### <a name="protected-constructors"></a>Protected 생성자

Name                                                             | 설명
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT:: SyncLockWithStatusT](#synclockwithstatust) | `SyncLockWithStatusT` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                         | 설명
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT:: GetStatus](#getstatus) | 현재 개체의 대기 상태를 검색 합니다 `SyncLockWithStatusT` .
[SyncLockWithStatusT:: IsLocked](#islocked)   | 현재 `SyncLockWithStatusT` 개체가 리소스를 소유 하 고 있는지 여부를 나타냅니다. 즉, `SyncLockWithStatusT` 개체가 *잠겨* 있는지 여부를 나타냅니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                                    | 설명
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT:: status_](#status) | 현재 개체를 기반으로 하는 개체에 대 한 잠금 작업 후 기본 대기 작업의 결과를 포함 합니다 `SyncLockWithStatusT` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼::D etails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a> SyncLockWithStatusT:: GetStatus

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>반환 값

`SyncLockWithStatusT` [뮤텍스](mutex-class.md) 또는 [세마포](semaphore-class.md)와 같이 클래스를 기반으로 하는 개체에 대 한 대기 작업의 결과입니다. 영 (0)은 대기 작업이 신호를 받은 상태를 반환 했음을 나타냅니다. 그렇지 않으면 시간 제한 값과 같은 다른 상태가 발생 합니다.

### <a name="remarks"></a>설명

현재 개체의 대기 상태를 검색 합니다 `SyncLockWithStatusT` .

GetStatus () 함수는 기본 [status_](#status) 데이터 멤버의 값을 검색 합니다. 클래스를 기반으로 하는 개체가 `SyncLockWithStatusT` 잠금 작업을 수행 하면 개체는 먼저 개체를 사용할 수 있을 때까지 대기 합니다. 해당 대기 작업의 결과는 데이터 멤버에 저장 됩니다 `status_` . 데이터 멤버의 가능한 값은 `status_` 대기 작업의 반환 값입니다. 자세한 내용은 함수의 반환 값을 참조 하세요 [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) .

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a> SyncLockWithStatusT:: IsLocked

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>설명

현재 `SyncLockWithStatusT` 개체가 리소스를 소유 하 고 있는지 여부를 나타냅니다. 즉, `SyncLockWithStatusT` 개체가 *잠겨* 있는지 여부를 나타냅니다.

### <a name="return-value"></a>반환 값

**`true`**`SyncLockWithStatusT`개체가 잠겨 있으면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a> SyncLockWithStatusT:: status_

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
DWORD status_;
```

### <a name="remarks"></a>설명

현재 개체를 기반으로 하는 개체에 대 한 잠금 작업 후 기본 대기 작업의 결과를 포함 합니다 `SyncLockWithStatusT` .

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a> SyncLockWithStatusT:: SyncLockWithStatusT

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 개체에 대 한 rvalue 참조 `SyncLockWithStatusT` 입니다.

*동기화*<br/>
다른 개체에 대 한 참조 `SyncLockWithStatusT` 입니다.

*status*<br/>
*다른* 매개 변수 또는 *sync* 매개 변수의 [status_](#status) 데이터 멤버 값입니다.

### <a name="remarks"></a>설명

`SyncLockWithStatusT` 클래스의 새 인스턴스를 초기화합니다.

첫 번째 생성자는 다른 `SyncLockWithStatusT` 매개 변수를 통해 지정 된 다른에서 현재 개체를 초기화 한 `SyncLockWithStatusT` 다음 다른 개체를 무효화 합니다  `SyncLockWithStatusT` . 두 번째 생성자는이 **`protected`** 고 현재 개체를 `SyncLockWithStatusT` 잘못 된 상태로 초기화 합니다.
