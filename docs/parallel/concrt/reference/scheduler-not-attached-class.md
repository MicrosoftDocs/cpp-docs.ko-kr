---
description: Scheduler_not_attached 클래스에 대해 자세히 알아보세요.
title: scheduler_not_attached 클래스
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: 1d412ffecea288d4ecad1d0c2949e7444adfd913
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188861"
---
# <a name="scheduler_not_attached-class"></a>scheduler_not_attached 클래스

이 클래스는 스케줄러가 현재 컨텍스트에 연결되어야 하는 작업을 수행하는데 연결된 스케줄러가 없는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|오버로드됨. `scheduler_not_attached` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="scheduler_not_attached"></a><a name="ctor"></a> scheduler_not_attached

`scheduler_not_attached` 개체를 생성합니다.

```cpp
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)
