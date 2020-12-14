---
description: Context_self_unblock 클래스에 대해 자세히 알아보세요.
title: context_self_unblock 클래스
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 51fae67530e2836b92a6ab7a13e2b136f1d438c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188978"
---
# <a name="context_self_unblock-class"></a>context_self_unblock 클래스

이 클래스는 동일한 컨텍스트에서 `Context` 개체의 `Unblock` 메서드를 호출하는 경우 발생하는 예외를 설명합니다. 자신을 차단 해제하려는 지정된 컨텍스트의 시도를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[context_self_unblock](#ctor)|오버로드됨. `context_self_unblock` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`context_self_unblock`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="context_self_unblock"></a><a name="ctor"></a> context_self_unblock

`context_self_unblock` 개체를 생성합니다.

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
