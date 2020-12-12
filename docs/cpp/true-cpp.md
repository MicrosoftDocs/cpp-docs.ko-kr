---
description: '자세한 정보: true (c + +)'
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: 6f3a9a183a30057ab3a013dad6e03458e6532658
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186456"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>구문

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>설명

이 키워드는 [bool](../cpp/bool-cpp.md) 형식의 변수 또는 조건식의 두 값 중 하나입니다. 조건식은 이제 진정한 부울 식입니다. `i`가 형식이 면 **`bool`** 문은 `i = true;` **`true`** 를에 할당 `i` 합니다.

## <a name="example"></a>예제

```cpp
// bool_true.cpp
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
