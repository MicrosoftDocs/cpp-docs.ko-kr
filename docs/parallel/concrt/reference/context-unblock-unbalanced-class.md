---
description: Context_unblock_unbalanced 클래스에 대해 자세히 알아보세요.
title: context_unblock_unbalanced 클래스
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: d262ff52a675935f95664d2f7ddd69aa159aa0bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188965"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced 클래스

이 클래스는 동일한 컨텍스트에서 `Context` 개체의 `Block` 및 `Unblock` 메서드 호출 쌍이 잘못된 경우 발생하는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|오버로드됨. `context_unblock_unbalanced` 개체를 생성합니다.|

## <a name="remarks"></a>설명

`Block` `Unblock` 개체의 및 메서드에 대 한 호출은 `Context` 항상 적절 하 게 쌍을 이루어야 합니다. 동시성 런타임를 사용 하 여 작업을 순서에 따라 수행할 수 있습니다. 예를 들어 `Block` 호출 다음에 `Unblock` 호출이 오거나 그 반대가 될 수 있습니다. 예를 들어, `Unblock` `Context` 차단 되지 않은 개체에 대해 한 행에서 메서드를 두 번 호출 하는 경우이 예외가 throw 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="context_unblock_unbalanced"></a><a name="ctor"></a> context_unblock_unbalanced

`context_unblock_unbalanced` 개체를 생성합니다.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
