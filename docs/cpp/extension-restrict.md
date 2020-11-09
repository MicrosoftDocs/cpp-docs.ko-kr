---
title: '`__restrict`'
description: Microsoft Visual C++ 키워드에 대해 설명 합니다 `__restrict` .
ms.date: 11/6/2020
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.openlocfilehash: f23574f49712928e0095f29a3b88b0c05b185eab
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381573"
---
# `__restrict`

**`__declspec` ( [`restrict`](../cpp/restrict.md) )** 한정자와 같이 **`__restrict`** 키워드 (두 개의 선행 밑줄 ' _ ')는 기호가 현재 범위에서 별칭이 지정 되지 않음을 나타냅니다. **`__restrict`** 키워드는 `__declspec (restrict)` 다음과 같은 점에서 한정자와 다릅니다.

- **`__restrict`** 키워드는 변수에만 유효 하며 `__declspec (restrict)` 함수 선언 및 정의에만 사용할 수 있습니다.

- **`__restrict`** 는 [`restrict`](../c-language/type-qualifiers.md#restrict) C99에서 시작 하는 c의 경우와 유사 하지만 **`__restrict`** c + + 및 c 프로그램에서 모두 사용할 수 있습니다.

- **`__restrict`** 을 사용 하는 경우 컴파일러는 변수의 별칭 없음 속성을 전파 하지 않습니다. 즉, 변수가 아닌 변수에 변수를 할당 하는 경우 **`__restrict`** **`__restrict`** 컴파일러는 아직 __restrict 되지 않은 변수를 별칭으로 지정할 수 있습니다. 이는 C99 C 언어 키워드의 동작과 다릅니다 **`restrict`** .

일반적으로 전체 함수의 동작에 영향을 주려면 **`__declspec (restrict)`** 키워드 대신를 사용 합니다.

이전 버전과의 호환성을 위해 **`_restrict`** 는 **`__restrict`** 컴파일러 옵션 [ `/Za` \( 언어 확장 사용 안 함](../build/reference/za-ze-disable-language-extensions.md) 을 지정 하지 않는 경우의 동의어입니다.

Visual Studio 2015 이상 버전에서는 **`__restrict`** c + + 참조에를 사용할 수 있습니다.

> [!NOTE]
> 키워드를 포함 하는 변수에 사용 하는 경우가 [`volatile`](../cpp/volatile-cpp.md) **`volatile`** 우선적으로 적용 됩니다.

## <a name="example"></a>예제

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)
