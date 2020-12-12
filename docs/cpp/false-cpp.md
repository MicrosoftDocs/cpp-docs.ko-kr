---
description: '자세한 정보: false (c + +)'
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 73f1f07c858f0a578cc2d3135e560cc8e0cb9d32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319458"
---
# <a name="false-c"></a>false (C++)

키워드는 [bool](../cpp/bool-cpp.md) 형식의 변수 또는 조건식 (이제 조건식이 **`true`** 부울 식) 인 두 값 중 하나입니다. 예를 들어 `i` 가 형식의 변수인 경우 **`bool`** `i = false;` 문은 **`false`** 에를 할당 `i` 합니다.

## <a name="example"></a>예제

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)
