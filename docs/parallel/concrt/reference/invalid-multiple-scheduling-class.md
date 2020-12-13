---
description: Invalid_multiple_scheduling 클래스에 대해 자세히 알아보세요.
title: invalid_multiple_scheduling 클래스
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: 23d89d93c953a3c01a6e0e698cfa7489effd2986
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334551"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling 클래스

이 클래스는 `wait` 또는 `run_and_wait` 메서드에 대한 중간 호출 없이 `task_group` 또는 `structured_task_group` 개체의 `run` 메서드를 사용하여 `task_handle` 개체가 여러 번 예약하는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|오버로드됨. `invalid_multiple_scheduling` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="invalid_multiple_scheduling"></a><a name="ctor"></a> invalid_multiple_scheduling

`invalid_multiple_scheduling` 개체를 생성합니다.

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[task_handle 클래스](task-handle-class.md)<br/>
[task_group 클래스](task-group-class.md)<br/>
[실행할지](task-group-class.md)<br/>
[대기한](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 클래스](structured-task-group-class.md)
