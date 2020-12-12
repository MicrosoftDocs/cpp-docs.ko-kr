---
description: '자세한 정보: bool (c + +)'
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: ea3af17260f21d3724f05b8bbad54091b23203e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229589"
---
# <a name="bool-c"></a>bool (C++)

이 키워드는 기본 제공 형식입니다. 이 형식의 변수는 및 값을 가질 수 있습니다 [`true`](../cpp/true-cpp.md) [`false`](../cpp/false-cpp.md) . 조건식은 형식 이므로 **`bool`** 형식의 값을 갖습니다 **`bool`** . 예를 들어 `i != 0` 이제는 **`true`** **`false`** 의 값에 따라 또는를 가집니다 `i` .

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): 후 위 또는 전위 증가 또는 감소 연산자의 피연산자는 형식일 수 없습니다 **`bool`** . 즉, 형식의 변수가 지정 된 경우 `b` **`bool`** 이러한 식은 더 이상 허용 되지 않습니다.

```cpp
    b++;
    ++b;
    b--;
    --b;
```

및 값에는 **`true`** **`false`** 다음과 같은 관계가 있습니다.

```cpp
!false == true
!true == false
```

다음 문에서

```cpp
if (condexpr1) statement1;
```

`condexpr1`가 이면 **`true`** 가 `statement1` 항상 실행 되 고, `condexpr1` 가 이면가 **`false`** `statement1` 실행 되지 않습니다.

후 위 또는 접두사 **`++`** 연산자를 형식의 변수에 적용 하면 **`bool`** 변수가로 설정 됩니다 **`true`** .

**Visual Studio 2017 버전 15.3 이상**: `operator++` 용 **`bool`** 이 언어에서 제거 되었으며 더 이상 지원 되지 않습니다.

후 위 또는 접두사 **`--`** 연산자를이 형식의 변수에 적용할 수 없습니다.

**`bool`** 형식은 기본 정수 계열 승격에 참여 합니다. 형식의 r 값은 **`bool`** **`int`** **`false`** 0이 되 고 1이 되도록 형식의 r 값으로 변환할 수 있습니다 **`true`** . 는 고유 형식으로 **`bool`** 오버 로드 확인에 참여 합니다.

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[기본 제공 형식](../cpp/fundamental-types-cpp.md)
