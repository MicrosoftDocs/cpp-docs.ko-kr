---
title: Mutex 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 597b84bf963957d4dd03c83f64044cb21b9a2607
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48239853"
---
# <a name="mutex-class"></a>Mutex 클래스

공유 리소스를 단독으로 제어하는 동기화 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

이름       | 설명
---------- | ------------------------------------------------------
`SyncLock` | 동기 잠금을 지 원하는 클래스에 대 한 동의어입니다.

### <a name="public-constructor"></a>Public 생성자

이름                   | 설명
---------------------- | ------------------------------------------------
[Mutex:: mutex](#mutex) | `Mutex` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-members"></a>공용 멤버

이름                 | 설명
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex:: lock](#lock) | 현재 개체를 때까지 대기 또는 `Mutex` 지정된 된 핸들, 뮤텍스 또는 지정 된 시간 제한 간격이 경과 하는 릴리스를 사용 하 여 연결 된 개체입니다.

### <a name="public-operator"></a>Public 연산자

이름                                 | 설명
------------------------------------ | ---------------------------------------------------------------------------
[Mutex:: operator =](#operator-assign) | 할당 된 (이동) `Mutex` 개체를 현재 `Mutex` 개체입니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`Mutex`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="lock"></a>Mutex:: lock

현재 개체를 때까지 대기 또는 `Mutex` 지정된 된 핸들, 뮤텍스 또는 지정 된 시간 제한 간격이 경과 하는 릴리스를 사용 하 여 연결 된 개체입니다.

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

*시간 (밀리초)*<br/>
제한 시간 간격(밀리초)입니다. 기본값은 INFINITE으로, 무제한 대기합니다.

*h*<br/>
핸들을 `Mutex` 개체입니다.

### <a name="return-value"></a>반환 값

## <a name="mutex"></a>Mutex:: mutex

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
핸들 또는 rvalue 참조 핸들을를 `Mutex` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 초기화를 `Mutex` 지정된 된 핸들에서 개체입니다. 두 번째 생성자는 초기화 된 `Mutex` 현재 개체와 지정 된 핸들을 다음 뮤텍스의 소유권 이동 `Mutex` 개체입니다.

## <a name="operator-assign"></a>Mutex:: operator =

할당 된 (이동) `Mutex` 개체를 현재 `Mutex` 개체입니다.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
rvalue 참조는 `Mutex` 개체입니다.

### <a name="return-value"></a>반환 값

현재에 대 한 참조 `Mutex` 개체입니다.

### <a name="remarks"></a>설명

자세한 내용은 참조는 **이동 의미 체계** 부분 [Rvalue 참조 선언 자: & &](../cpp/rvalue-reference-declarator-amp-amp.md)합니다.
