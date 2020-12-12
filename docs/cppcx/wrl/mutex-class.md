---
description: '자세한 정보: Mutex 클래스'
title: Mutex 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: f69c14014a2283fe56ef8e7f705bebe5a5f6dc9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330844"
---
# <a name="mutex-class"></a>Mutex 클래스

공유 리소스를 단독으로 제어하는 동기화 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name       | 설명
---------- | ------------------------------------------------------
`SyncLock` | 동기 잠금을 지 원하는 클래스의 동의어입니다.

### <a name="public-constructor"></a>Public 생성자

Name                   | 설명
---------------------- | ------------------------------------------------
[Mutex:: Mutex](#mutex) | `Mutex` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-members"></a>Public 멤버

Name                 | 설명
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex:: Lock](#lock) | 현재 개체 또는 `Mutex` 지정 된 핸들과 연결 된 개체가 뮤텍스를 해제 하거나 지정 된 시간 제한 간격이 경과할 때까지 대기 합니다.

### <a name="public-operator"></a>Public 연산자

Name                                 | 설명
------------------------------------ | ---------------------------------------------------------------------------
[Mutex:: operator =](#operator-assign) | 지정 된 개체를 현재 개체로 할당 (이동) `Mutex` `Mutex` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Mutex`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="mutexlock"></a><a name="lock"></a> Mutex:: Lock

현재 개체 또는 `Mutex` 지정 된 핸들과 연결 된 개체가 뮤텍스를 해제 하거나 지정 된 시간 제한 간격이 경과할 때까지 대기 합니다.

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
개체의 핸들 `Mutex` 입니다.

### <a name="return-value"></a>반환 값

## <a name="mutexmutex"></a><a name="mutex"></a> Mutex:: Mutex

`Mutex` 클래스의 새 인스턴스를 초기화합니다.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
핸들 또는 개체에 대 한 rvalue 참조 `Mutex` 입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `Mutex` 지정 된 핸들에서 개체를 초기화 합니다. 두 번째 생성자는 `Mutex` 지정 된 핸들에서 개체를 초기화 한 다음 뮤텍스의 소유권을 현재 개체로 이동 합니다 `Mutex` .

## <a name="mutexoperator"></a><a name="operator-assign"></a> Mutex:: operator =

지정 된 개체를 현재 개체로 할당 (이동) `Mutex` `Mutex` 합니다.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
개체에 대 한 rvalue 참조 `Mutex` 입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조 `Mutex` 입니다.

### <a name="remarks"></a>설명

자세한 내용은 [Rvalue 참조 선언 자:  &&](../../cpp/rvalue-reference-declarator-amp-amp.md)의 **의미 체계 이동** 섹션을 참조 하세요.
