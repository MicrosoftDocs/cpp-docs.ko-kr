---
description: '자세히 알아보기: 함수 템플릿의 부분 순서 지정 (c + +)'
title: 함수 템플릿의 부분 순서 지정 (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 701c97aa819d0294f69f2fe2a71ffb9bf0210afa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145901"
---
# <a name="partial-ordering-of-function-templates-c"></a>함수 템플릿의 부분 순서 지정 (C++)

함수 호출의 인수 목록과 일치하는 다양한 함수 템플릿을 사용할 수 있습니다. C++에서는 호출해야 하는 함수를 지정하는 함수 템플릿의 부분 정렬을 정의합니다. 정렬이 부분적인 이유는 동일하게 특수화된 것으로 간주되는 일부 템플릿이 있을 수 있기 때문입니다.

컴파일러는 가능한 일치 함수 템플릿 중에서 가장 특수화된 것을 선택합니다. 예를 들어 함수 템플릿이 형식을 사용 하 고를 `T` 사용 하는 다른 함수 템플릿을 `T*` 사용할 수 있는 경우 `T*` 버전은 보다 특수화 된 것으로 간주 됩니다. `T`인수가 포인터 형식일 때마다 제네릭 버전 보다 우선적으로 사용할 수 있습니다.

더욱 특수화된 함수 템플릿 후보를 확인하려면 다음 프로세스를 사용합니다.

1. 두 함수 템플릿 T1과 T2를 살펴보십시오.

1. T1의 매개 변수를 가상의 고유 형식 X로 대체합니다.

1. T1의 매개 변수 목록을 이용하여 T2가 그 매개 변수 목록에 대해 유효한 템플릿인지 확인합니다. 암시적 변환을 무시합니다.

1. T1과 T2를 반대로 바꿔 동일한 프로세스를 반복합니다.

1. 한 템플릿이 다른 템플릿에 대 한 유효한 템플릿 인수 목록이 고 그 반대의 경우는 그렇지 않으면 해당 템플릿은 다른 템플릿 보다 특수화 되지 않은 것으로 간주 됩니다. 이전 단계를 사용 하는 경우 두 템플릿이 서로에 대해 유효한 인수를 구성 하 고,이를 사용 하려고 할 때 모호한 호출 결과와 동일 하 게 특수화 된 것으로 간주 됩니다.

1. 다음의 규칙을 사용합니다.

   1. 특정 형식으로 특수화된 템플릿은 제네릭 형식 인수를 사용한 템플릿보다 특수화됩니다.

   1. `T*` `T` 가상 형식이 `X*` 템플릿 인수에 대 한 유효한 인수 `T` 이지만 `X` 템플릿 인수에 대 한 유효한 인수가 아니기 때문에만 취하는 템플릿은 보다 특수 한 방법입니다 `T*` .

   1. `const T``T` `const X` 는 템플릿 인수에 대 한 유효한 인수 `T` 이지만는 `X` 템플릿 인수에 대 한 유효한 인수가 아니기 때문에 보다 특수화 되어 `const T` 있습니다.

   1. `const T*``T*` `const X*` 는 템플릿 인수에 대 한 유효한 인수 `T*` 이지만는 `X*` 템플릿 인수에 대 한 유효한 인수가 아니기 때문에 보다 특수화 되어 `const T*` 있습니다.

## <a name="example"></a>예제

다음 샘플은 표준에 지정 된 대로 작동 합니다.

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>출력

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>참조

[함수 템플릿](../cpp/function-templates.md)
