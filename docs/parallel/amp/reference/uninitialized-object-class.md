---
description: Uninitialized_object 클래스에 대해 자세히 알아보세요.
title: uninitialized_object 클래스
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 4929de9e865492c9fb468f5fac336f67fb307efb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326392"
---
# <a name="uninitialized_object-class"></a>uninitialized_object 클래스

초기화 되지 않은 개체를 사용할 때 throw 되는 예외입니다.

## <a name="syntax"></a>구문

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[uninitialized_object 생성자](#uninitialized_object)|`uninitialized_object` 클래스의 새 인스턴스를 초기화합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임스페이스:** 동시성

## <a name="uninitialized_object"></a><a name="uninitialized_object"></a> uninitialized_object

예외의 새 인스턴스를 생성 `uninitialized_object` 합니다.

### <a name="syntax"></a>구문

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류에 대한 설명입니다.

### <a name="return-value"></a>반환 값

`uninitialized_object`예외 개체입니다.

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
