---
description: Operation_timed_out 클래스에 대해 자세히 알아보세요.
title: operation_timed_out 클래스
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 476dfc2d7f29b2769c076ff525f3d0eb1e20a8f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236557"
---
# <a name="operation_timed_out-class"></a>operation_timed_out 클래스

이 클래스는 작업이 시간 초과된 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class operation_timed_out : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[operation_timed_out](#ctor)|오버로드됨. `operation_timed_out` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`operation_timed_out`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="operation_timed_out"></a><a name="ctor"></a> operation_timed_out

`operation_timed_out` 개체를 생성합니다.

```cpp
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
