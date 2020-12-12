---
description: Bad_exception 클래스에 대해 자세히 알아보세요.
title: bad_exception 클래스
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 6b47facc751e1f16e033f26be284db1287e79ea8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321614"
---
# <a name="bad_exception-class"></a>bad_exception 클래스

이 클래스는 예기치 않은 처리기에서 throw할 수 있는 예외를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>설명

[unexpected](../standard-library/exception-functions.md#unexpected)는 함수의 throw 목록에 `bad_exception`이 포함된 경우 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)로 지정된 또 다른 함수를 종료하거나 호출하는 대신 `bad_exception`을 throw합니다.

에서 반환 하는 값은 `what` 구현 시 정의 된 C 문자열입니다. 멤버 함수는 예외를 발생시키지 않습니다.

`bad_exception` 클래스에 의해 상속된 멤버 목록은 [exception 클래스](../standard-library/exception-class.md)를 참조하세요.

## <a name="example"></a>예제

`bad_exception`을 throw하는 [unexpected](../standard-library/exception-functions.md#unexpected) 사용의 예는 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)를 참조하세요.
