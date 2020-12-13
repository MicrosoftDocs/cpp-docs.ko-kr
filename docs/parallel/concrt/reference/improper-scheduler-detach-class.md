---
description: Improper_scheduler_detach 클래스에 대해 자세히 알아보세요.
title: improper_scheduler_detach 클래스
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: 62def23a4a3459c4cb8268b3b0f4df4a77025668
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334609"
---
# <a name="improper_scheduler_detach-class"></a>improper_scheduler_detach 클래스

이 클래스는 `Scheduler` 개체의 `Attach` 메서드를 사용하여 스케줄러에 연결되지 않은 컨텍스트에 대해 `CurrentScheduler::Detach` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|오버로드됨. `improper_scheduler_detach` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="improper_scheduler_detach"></a><a name="ctor"></a> improper_scheduler_detach

`improper_scheduler_detach` 개체를 생성합니다.

```cpp
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)
