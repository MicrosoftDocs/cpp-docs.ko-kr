---
description: Improper_scheduler_reference 클래스에 대해 자세히 알아보세요.
title: improper_scheduler_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 4857418e14908b2d085d52249236d6395284b98a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334600"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference 클래스

이 클래스는 스케줄러에 속하지 않는 컨텍스트에서 종료되는 `Scheduler` 개체에 대해 `Reference` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|오버로드됨. `improper_scheduler_reference` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="improper_scheduler_reference"></a><a name="ctor"></a> improper_scheduler_reference

`improper_scheduler_reference` 개체를 생성합니다.

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)
