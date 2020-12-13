---
description: Invalid_oversubscribe_operation 클래스에 대해 자세히 알아보세요.
title: invalid_oversubscribe_operation 클래스
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 435e3ce0eba29188711c51aa9253060fc08ac62c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334523"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation 클래스

이 클래스는 매개 `Context::Oversubscribe` `_BeginOversubscription` 변수를 **`false`** `Context::Oversubscribe` 로 설정 하 여 메서드를 이전에 호출 하지 않고 매개 변수를로 설정 `_BeginOversubscription` **`true`** 하 여 메서드를 호출할 때 throw 되는 예외를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|오버로드됨. `invalid_oversubscribe_operation` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="invalid_oversubscribe_operation"></a><a name="ctor"></a> invalid_oversubscribe_operation

`invalid_oversubscribe_operation` 개체를 생성합니다.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
