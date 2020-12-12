---
description: Unsupported_feature 클래스에 대해 자세히 알아보세요.
title: unsupported_feature 클래스
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 22cbc193de2a42e76ead4097d1e39351693ef706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314505"
---
# <a name="unsupported_feature-class"></a>unsupported_feature 클래스

지원 되지 않는 기능을 사용할 때 throw 되는 예외입니다.

## <a name="syntax"></a>구문

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[unsupported_feature 생성자](#unsupported_feature)|예외의 새 인스턴스를 생성 `unsupported_feature` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a><a name="unsupported_feature"></a> unsupported_feature

  예외의 새 인스턴스를 생성 `unsupported_feature` 합니다.

### <a name="syntax"></a>구문

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류에 대한 설명입니다.

### <a name="return-value"></a>반환 값

`unsupported_feature` 개체

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임스페이스:** 동시성

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
