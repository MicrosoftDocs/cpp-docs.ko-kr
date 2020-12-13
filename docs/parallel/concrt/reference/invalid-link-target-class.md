---
description: Invalid_link_target 클래스에 대해 자세히 알아보세요.
title: invalid_link_target 클래스
ms.date: 11/04/2016
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
ms.openlocfilehash: d080886c3aab0ecc120d4ce13f5f75f2eecfea8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334586"
---
# <a name="invalid_link_target-class"></a>invalid_link_target 클래스

이 클래스는 메시징 블록의 `link_target` 메서드를 호출하고 메시징 블록이 대상에 연결할 수 없는 경우 발생하는 예외를 설명합니다. 메시징 블록에 허용되는 링크 수를 초과했거나 동일한 소스에 특정 대상을 두 번 연결하려고 시도한 결과일 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class invalid_link_target : public std::exception;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[invalid_link_target](#ctor)|오버로드됨. `invalid_link_target` 개체를 생성합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`exception`

`invalid_link_target`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="invalid_link_target"></a><a name="ctor"></a> invalid_link_target

`invalid_link_target` 개체를 생성합니다.

```cpp
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>매개 변수

*_Message*<br/>
오류 설명 메시지입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)
