---
description: Lock_guard 클래스에 대해 자세히 알아보세요.
title: lock_guard 클래스
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: d8965f1e781d99f0b84c58dcc3288a4532e4351c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277728"
---
# <a name="lock_guard-class"></a>lock_guard 클래스

소멸자가 `mutex`의 잠금을 해제하는 개체를 만들기 위해 인스턴스화할 수 있는 템플릿을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>설명

템플릿 인수 `Mutex`는 *뮤텍스 형식* 의 이름을 지정해야 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`lock_guard::mutex_type`|템플릿 인수 `Mutex`에 대한 동의어입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[lock_guard](#lock_guard)|`lock_guard` 개체를 생성합니다.|
|[lock_guard::~lock_guard 소멸자](#dtorlock_guard_destructor)|생성자에 전달된 `mutex`를 잠금 해제합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<mutex>

**네임스페이스:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a> lock_guard:: lock_guard 생성자

`lock_guard` 개체를 생성합니다.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>매개 변수

*Mtx.exe*\
*뮤텍스 형식* 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 형식의 개체를 생성 `lock_guard` 하 고 *mtx.exe* 를 잠급니다. *Mtx.exe* 가 재귀 뮤텍스가 아니면이 생성자가 호출 될 때 잠금 해제 되어야 합니다.

두 번째 생성자는 *mtx.exe* 을 잠그지 않습니다. 이 생성자가 호출 될 때 *mtx.exe* 가 잠겨 있어야 합니다. 생성자는 예외를 throw하지 않습니다.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a> lock_guard:: ~ lock_guard 소멸자

생성자에 전달된 `mutex`를 잠금 해제합니다.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>설명

소멸자가 실행될 때 `mutex`가 없으면 동작이 정의되지 않습니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
