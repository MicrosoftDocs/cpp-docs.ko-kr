---
description: Out_of_memory 클래스에 대해 자세히 알아보세요.
title: out_of_memory 클래스
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: bb7ba1db5be5921111b1fba2e12ea5cf6a5bea1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329922"
---
# <a name="out_of_memory-class"></a>out_of_memory 클래스

시스템이 나 장치 메모리 부족으로 인해 메서드가 실패 하는 경우 throw 되는 예외입니다.

## <a name="syntax"></a>구문

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[out_of_memory 생성자](#ctor)|`out_of_memory` 클래스의 새 인스턴스를 초기화합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임스페이스:** 동시성

## <a name="out_of_memory"></a><a name="ctor"></a> out_of_memory

클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류에 대한 설명입니다.

### <a name="return-value"></a>반환 값

`out_of_memory` 클래스의 새 인스턴스입니다.

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
