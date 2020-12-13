---
description: Invalid_scheduler_policy_thread_specification 클래스에 대해 자세히 알아보세요.
title: invalid_scheduler_policy_thread_specification 클래스
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: 97a3910fc83e741c54ece51ed8e20686bbd6c66b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334507"
---
# <a name="invalid_scheduler_policy_thread_specification-class"></a>invalid_scheduler_policy_thread_specification 클래스

이 클래스는 `MinConcurrency` 키의 값이 `MaxConcurrency` 키의 값보다 작도록 `SchedulerPolicy` 개체의 동시성 제한을 설정하려고 시도하는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification] (잘못 된-스케줄러-정책-값-클래스. md # ctor|오버로드됨. `invalid_scheduler_policy_value` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="invalid_scheduler_policy_thread_specification"></a><a name="ctor"></a> invalid_scheduler_policy_thread_specification

`invalid_scheduler_policy_value` 개체를 생성합니다.

```cpp
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[SchedulerPolicy 클래스](schedulerpolicy-class.md)
