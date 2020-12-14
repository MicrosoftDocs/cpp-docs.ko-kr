---
description: Nested_scheduler_missing_detach 클래스에 대해 자세히 알아보세요.
title: nested_scheduler_missing_detach 클래스
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: 3d1232b8f9b807835f5b4b1e19c6049d049f12f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202108"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach 클래스

이 클래스는 동시성 런타임에서 `Scheduler` 개체의 `Attach` 메서드를 사용하여 두 번째 스케줄러에 연결된 컨텍스트에 대해 `CurrentScheduler::Detach` 메서드를 호출하지 않은 것을 감지하는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|오버로드됨. `nested_scheduler_missing_detach` 개체를 생성합니다.|

## <a name="remarks"></a>설명

이 예외는 다른 스케줄러에서 이미 소유하고 있거나 다른 스케줄러에 연결된 컨텍스트에서 `Attach` 개체의 `Scheduler` 메서드를 호출함으로써 다른 컨텍스트 내에 한 스케줄러를 중첩할 때만 throw됩니다. 동시성 런타임는 문제를 찾기 위한 도움으로 시나리오를 검색할 수 있는 경우이 예외를 대해 선택적으로에 throw 합니다. 메서드를 호출 하는 하지 않는의 모든 인스턴스가 `CurrentScheduler::Detach` 이 예외를 throw 할 수 있는 것은 아닙니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="nested_scheduler_missing_detach"></a><a name="ctor"></a> nested_scheduler_missing_detach

`nested_scheduler_missing_detach` 개체를 생성합니다.

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)
