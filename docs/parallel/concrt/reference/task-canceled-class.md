---
description: Task_canceled 클래스에 대해 자세히 알아보세요.
title: task_canceled 클래스
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: 223a1168464e312c272f770247b3574311ff97ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188406"
---
# <a name="task_canceled-class"></a>task_canceled 클래스

이 클래스는 현재 작업을 강제 취소하도록 PPL 작업 레이어에서 throw된 예외를 설명합니다. 또한 `get()` 취소 된 작업에 대해 [작업](/visualstudio/extensibility/debugger/task-class-internal-members)의 메서드에서 throw 됩니다.

## <a name="syntax"></a>구문

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[task_canceled](#ctor)|오버로드됨. `task_canceled` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`task_canceled`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="task_canceled"></a><a name="ctor"></a> task_canceled

`task_canceled` 개체를 생성합니다.

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
