---
title: 단항 연산자 오버 로드 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f737e262d39b99c2c33b7c91bc3d1e234a9f47db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018628"
---
# <a name="overloading-unary-operators"></a>단항 연산자 오버로드

오버로드할 수 있는 단항 연산자는 다음과 같습니다.

1. `!` ([논리적 NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([주소](../cpp/address-of-operator-amp.md))

1. `~` ([1의 보수](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([포인터 역참조](../cpp/indirection-operator-star.md))

1. `+` ([단항 더하기](../cpp/additive-operators-plus-and.md))

1. `-` ([단항 부정 연산자](../cpp/additive-operators-plus-and.md))

1. `++` ([증가](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([감소](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. conversion operators

후 위 증가 및 감소 연산자 (`++` 하 고 `--`)에서 별도로 처리 됩니다 [증가 및 감소](../cpp/increment-and-decrement-operator-overloading-cpp.md)합니다.

변환 연산자도 별도 항목;의 설명 참조 [사용자 정의 형식 변환](../cpp/user-defined-type-conversions-cpp.md)합니다.

다음 규칙은 다른 모든 단항 연산자에 적용됩니다. 단항 연산자 함수를 비정적 멤버로 선언하려면 해당 함수를 다음 형식으로 선언해야 합니다.

> *만료 유형* **연산자** *op* **)**

여기서 *ret 형식당* 반환 형식 및 *op* 연산자 중 하나 앞의 표에 나열 됩니다.

단항 연산자 함수를 전역 함수로 선언하려면 해당 함수를 다음 형식으로 선언해야 합니다.

> *만료 유형* **연산자** *op* **(** *arg* **)**

여기서 *ret 형식* 및 *op* 는 멤버 연산자 함수로 설명 되는 *arg* 연산을 수행할 클래스 형식의 인수입니다.

> [!NOTE]
>  단항 연산자의 반환 형식에 대한 제한은 없습니다. 예를 들어 논리 NOT(`!`)에서 정수 계열 값을 반환하는 것이 적합하지만 이는 적용되지 않습니다.

## <a name="see-also"></a>참고자료

[연산자 오버로드](../cpp/operator-overloading.md)