---
description: Scheduler_worker_creation_error 클래스에 대해 자세히 알아보세요.
title: scheduler_worker_creation_error 클래스
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: f0fbb0aed19738bb88e4cbfe3a72580627c4fca9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188718"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error 클래스

이 클래스는 동시성 런타임에서 작업자 실행 컨텍스트를 만들지 못해 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|오버로드됨. `scheduler_worker_creation_error` 개체를 생성합니다.|

## <a name="remarks"></a>설명

이 예외는 일반적으로 동시성 런타임 내에서 실행 컨텍스트를 생성하기 위한 운영 체제 호출이 실패할 때 throw됩니다. 실행 컨텍스트는 동시성 런타임에서 작업을 실행하는 스레드입니다. Win32 메서드 `GetLastError`에 대한 호출에서 일반적으로 반환되는 오류 코드는 `HRESULT` 형식의 값으로 변환되므로 기본 클래스 메서드인 `get_error_code`를 사용하여 검색할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="scheduler_worker_creation_error"></a><a name="ctor"></a> scheduler_worker_creation_error

`scheduler_worker_creation_error` 개체를 생성합니다.

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

*_Hresult*<br/>
`HRESULT`예외를 발생 시킨 오류의 값입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
