---
description: '자세한 정보: 세마포 클래스'
title: Semaphore 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 0cf99ff0a0e5263b3ed924ec5ac69b7edb0bd1f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186235"
---
# <a name="semaphore-class"></a>Semaphore 클래스

제한된 사용자 수를 지원할 수 있는 공유 리소스를 제어하는 동기화 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name       | 설명
---------- | ------------------------------------------------------
`SyncLock` | 동기 잠금을 지 원하는 클래스의 동의어입니다.

### <a name="public-constructors"></a>Public 생성자

이름                               | 설명
---------------------------------- | ----------------------------------------------------
[세마포:: 세마포](#semaphore) | `Semaphore` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                     | 설명
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[세마포:: Lock](#lock) | 현재 개체 또는 지정 된 핸들과 연결 된 개체가 신호를 받은 상태 이거나 지정 된 시간 제한 간격이 경과할 때까지 대기 합니다.

### <a name="public-operators"></a>Public 연산자

Name                                     | 설명
---------------------------------------- | ---------------------------------------------------------------------------------------
[세마포:: operator =](#operator-assign) | 지정 된 핸들을 개체에서 `Semaphore` 현재 `Semaphore` 개체로 이동 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Semaphore`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="semaphorelock"></a><a name="lock"></a> 세마포:: Lock

현재 개체 또는 `Semaphore` 지정 된 핸들과 연결 된 개체가 신호를 받은 상태 이거나 지정 된 시간 제한 간격이 경과할 때까지 대기 합니다.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>매개 변수

*milliseconds*<br/>
제한 시간 간격(밀리초)입니다. 기본값은 INFINITE으로, 무제한 대기합니다.

*h*<br/>
개체에 대 한 핸들 `Semaphore` 입니다.

### <a name="return-value"></a>반환 값

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="semaphoreoperator"></a><a name="operator-assign"></a> 세마포:: operator =

지정 된 핸들을 개체에서 `Semaphore` 현재 `Semaphore` 개체로 이동 합니다.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
Rvalue-개체에 대 한 참조 `Semaphore` 입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조 `Semaphore` 입니다.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a> 세마포:: 세마포

`Semaphore` 클래스의 새 인스턴스를 초기화합니다.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
개체에 대 한 핸들 또는 rvalue 참조 `Semaphore` 입니다.
