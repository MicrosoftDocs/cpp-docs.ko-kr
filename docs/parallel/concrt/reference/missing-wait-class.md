---
description: Missing_wait 클래스에 대해 자세히 알아보세요.
title: missing_wait 클래스
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: bfbfdf4c2a52573d08c048bac278386aed1dc5a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202186"
---
# <a name="missing_wait-class"></a>missing_wait 클래스

이 클래스는 개체의 소멸자를 실행할 때 `task_group` 또는 `structured_task_group` 개체에 여전히 예약된 작업이 있는 경우 발생하는 예외를 설명합니다. 예외의 결과로 스택 해제 때문에 소멸자에 도달한 경우에는 이 예외가 발생하지 않습니다.

## <a name="syntax"></a>구문

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[missing_wait](#ctor)|오버로드됨. `missing_wait` 개체를 생성합니다.|

## <a name="remarks"></a>설명

예외 흐름이 `wait` `run_and_wait` 없는 경우 또는 개체의 또는 메서드를 호출 하 여 `task_group` `structured_task_group` 해당 개체의 소멸을 허용 해야 합니다. 런타임에서는 또는 메서드를 호출 하지 않았음을 나타내는 것으로이 예외를 throw 합니다 `wait` `run_and_wait` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`missing_wait`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="missing_wait"></a><a name="ctor"></a> missing_wait

`missing_wait` 개체를 생성합니다.

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[task_group 클래스](task-group-class.md)<br/>
[대기한](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 클래스](structured-task-group-class.md)
