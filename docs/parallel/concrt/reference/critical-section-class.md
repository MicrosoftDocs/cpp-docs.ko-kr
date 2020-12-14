---
description: Critical_section 클래스에 대해 자세히 알아보세요.
title: critical_section 클래스
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: d781ce467123197521bf92dd4d932a665e55c6a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188939"
---
# <a name="critical_section-class"></a>critical_section 클래스

동시성 런타임을 명시적으로 인식하는 재진입성이 아닌 뮤텍스입니다.

## <a name="syntax"></a>구문

```cpp
class critical_section;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`native_handle_type`|`critical_section` 개체에 대한 참조입니다.|

### <a name="public-classes"></a>public 클래스

|Name|설명|
|----------|-----------------|
|[critical_section::scoped_lock 클래스](#critical_section__scoped_lock_class)|개체에 대 한 예외 안전 RAII 래퍼입니다 `critical_section` .|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[critical_section](#ctor)|새 임계 영역을 생성 합니다.|
|[~ critical_section 소멸자](#dtor)|임계 영역을 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|이 임계 영역을 가져옵니다.|
|[native_handle](#native_handle)|플랫폼 특정 네이티브 핸들 (있는 경우)을 반환 합니다.|
|[try_lock](#try_lock)|차단 하지 않고 잠금을 가져오려고 시도 합니다.|
|[try_lock_for](#try_lock_for)|특정 기간(밀리초) 동안 차단하지 않고 잠금을 가져오려고 시도합니다.|
|[잠금을](#unlock)|임계 영역을 잠금 해제 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [동기화 데이터 구조](../../../parallel/concrt/synchronization-data-structures.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`critical_section`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="critical_section"></a><a name="ctor"></a> critical_section

새 임계 영역을 생성 합니다.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a> ~ critical_section

임계 영역을 소멸 시킵니다.

```cpp
~critical_section();
```

### <a name="remarks"></a>설명

소멸자가 실행 될 때 잠금이 더 이상 유지 되지 않을 것으로 예상 됩니다. 임계 영역에서 잠금으로 소멸 되도록 허용 하면 정의 되지 않은 동작이 발생 합니다.

## <a name="lock"></a><a name="lock"></a> 잠기지

이 임계 영역을 가져옵니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

일반적으로 [scoped_lock](#critical_section__scoped_lock_class) 구문을 활용 하 여 예외 안전 방식으로 개체를 가져오고 해제 하는 것이 더 안전 `critical_section` 합니다.

호출 컨텍스트에서 잠금이 이미 유지 되 고 있으면 [improper_lock](improper-lock-class.md) 예외가 throw 됩니다.

## <a name="native_handle"></a><a name="native_handle"></a> native_handle

플랫폼 특정 네이티브 핸들 (있는 경우)을 반환 합니다.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>반환 값

임계 영역에 대 한 참조입니다.

### <a name="remarks"></a>설명

`critical_section`개체는 Windows 운영 체제에 대 한 플랫폼별 네이티브 핸들과 연결 되지 않습니다. 메서드는 단순히 개체 자체에 대 한 참조를 반환 합니다.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a> critical_section:: scoped_lock 클래스

개체에 대 한 예외 안전 RAII 래퍼입니다 `critical_section` .

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a> scoped_lock:: scoped_lock

개체를 생성 `scoped_lock` 하 고 `critical_section` 매개 변수에 전달 된 개체를 가져옵니다 `_Critical_section` . 다른 스레드에서 임계 영역을 보유 하 고 있으면이 호출은 차단 됩니다.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>매개 변수

*_Critical_section*<br/>
잠글 임계 영역입니다.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

개체를 소멸 시키고 `scoped_lock` 해당 생성자에 제공 된 임계 영역을 해제 합니다.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

차단 하지 않고 잠금을 가져오려고 시도 합니다.

```cpp
bool try_lock();
```

### <a name="return-value"></a>반환 값

잠금을 획득 한 경우 값 **`true`** 이 고, 그렇지 않으면 값 **`false`** 입니다.

## <a name="try_lock_for"></a><a name="try_lock_for"></a> try_lock_for

특정 기간(밀리초) 동안 차단하지 않고 잠금을 가져오려고 시도합니다.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>매개 변수

*_Timeout*<br/>
시간이 초과되기 전에 대기하는 기간(밀리초)입니다.

### <a name="return-value"></a>반환 값

잠금을 획득 한 경우 값 **`true`** 이 고, 그렇지 않으면 값 **`false`** 입니다.

## <a name="unlock"></a><a name="unlock"></a> 잠금을

임계 영역을 잠금 해제 합니다.

```cpp
void unlock();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[reader_writer_lock 클래스](reader-writer-lock-class.md)
