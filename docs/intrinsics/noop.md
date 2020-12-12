---
description: '다음에 대 한 자세한 정보: __noop'
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 4b140141e0f773f01cd666dd67f77244d7aef8a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222465"
---
# <a name="__noop"></a>__noop

**Microsoft 전용**

**`__noop`** 내장 함수는 함수를 무시 하도록 지정 합니다. 인수 목록은 구문 분석 되지만 인수에 대해서는 코드가 생성 되지 않습니다. 가변 개수의 인수를 사용 하는 전역 디버그 함수에서 사용 하기 위한 것입니다.

컴파일러는 **`__noop`** 컴파일 타임에 내장 함수를 0으로 변환 합니다.

## <a name="example"></a>예제

다음 코드에서는를 사용 하는 방법을 보여 줍니다 **`__noop`** .

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[키워드](../cpp/keywords-cpp.md)
