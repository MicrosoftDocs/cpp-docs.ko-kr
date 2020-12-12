---
description: Bad_target 클래스에 대해 자세히 알아보세요.
title: bad_target 클래스
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 0bade57ef06ee1ecf675d69531da918fc2a3510f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172247"
---
# <a name="bad_target-class"></a>bad_target 클래스

이 클래스는 수행되는 작업에 잘못된 대상에 대한 포인터가 메시징 블록에 제공되는 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[bad_target](#ctor)|오버로드됨. `bad_target` 개체를 생성합니다.|

## <a name="remarks"></a>설명

이 예외는 일반적으로 다른 대상에 대해 예약 된 메시지를 사용 하려고 시도 하는 대상 또는 보유 하지 않는 예약을 해제 하는 것과 같은 이유로 throw 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`bad_target`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="bad_target"></a><a name="ctor"></a> bad_target

`bad_target` 개체를 생성합니다.

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)
