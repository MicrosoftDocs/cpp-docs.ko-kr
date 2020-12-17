---
description: 'Microsoft C/c + + 내장 함수에 대해 자세히 알아보기: __noop'
title: __noop
ms.date: 12/16/2020
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 5fd300ca8d68305a12e6b5540be05aa60a042a44
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645087"
---
# `__noop`

**Microsoft 전용** **`__noop`** 내장 함수는 함수를 무시 하도록 지정 합니다. 인수 목록은 구문 분석 되지만 인수에 대해서는 코드가 생성 되지 않습니다. 컴파일러는 컴파일러 경고 C4100 및 유사한 분석을 위해 인수를 참조 된 것으로 간주 합니다. 내장 함수는 `__noop` 가변 개수의 인수를 사용 하는 전역 디버그 함수에서 사용 하기 위한 것입니다.

컴파일러는 **`__noop`** 컴파일 타임에 내장 함수를 0으로 변환 합니다.

## <a name="example"></a>예

다음 코드에서는를 사용 하는 방법을 보여 줍니다 **`__noop`** .

```cpp
// compiler_intrinsics__noop.cpp
// compile using: cl /EHsc /W4 compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

#define IGNORE(x) { __noop(x); }

int main(int argv, char ** argc)
{
   IGNORE(argv);
   IGNORE(argc);
   PRINT("\nDEBUG is defined\n");
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[키워드](../cpp/keywords-cpp.md)
