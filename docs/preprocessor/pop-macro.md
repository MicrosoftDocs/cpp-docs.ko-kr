---
description: pragmaMicrosoft C/c + +의 pop_macro 지시문에 대해 자세히 알아보세요.
title: pop_macro pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragma, pop_macro
no-loc:
- pragma
ms.openlocfilehash: 99b0567838bac2a683f2a31fe13dd423e2efe651
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713365"
---
# <a name="pop_macro-no-locpragma"></a>`pop_macro` pragma

*매크로 이름* 매크로의 값을이 매크로의 스택 맨 위에 있는 값으로 설정 합니다.

## <a name="syntax"></a>구문

> **`#pragma pop_macro(`** "*매크로-이름*" **`)`**

## <a name="remarks"></a>설명

를 [`push_macro`](../preprocessor/push-macro.md) 수행 하려면 먼저 for *macro 이름을* 실행 해야 합니다 **`pop_macro`** .

## <a name="example"></a>예제

```cpp
// pragma_directives_pop_macro.cpp
// compile with: /W1
#include <stdio.h>
#define X 1
#define Y 2

int main() {
   printf("%d",X);
   printf("\n%d",Y);
   #define Y 3   // C4005
   #pragma push_macro("Y")
   #pragma push_macro("X")
   printf("\n%d",X);
   #define X 2   // C4005
   printf("\n%d",X);
   #pragma pop_macro("X")
   printf("\n%d",X);
   #pragma pop_macro("Y")
   printf("\n%d",Y);
}
```

```Output
1
2
1
2
1
3
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
