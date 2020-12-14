---
description: Unsupported_os 클래스에 대해 자세히 알아보세요.
title: unsupported_os 클래스
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 1f9ee74db42d2b34c1b4e24a1951d84a442224bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188094"
---
# <a name="unsupported_os-class"></a>unsupported_os 클래스

이 클래스는 지원되지 않는 운영 체제를 사용할 때 throw되는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[unsupported_os](#ctor)|오버로드됨. `unsupported_os` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`unsupported_os`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="unsupported_os"></a><a name="ctor"></a> unsupported_os

`unsupported_os` 개체를 생성합니다.

### <a name="syntax"></a>구문

```cpp
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
