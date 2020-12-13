---
description: '자세한 정보: 컴파일러 오류 C2162'
title: 컴파일러 오류 C2162
ms.date: 11/04/2016
f1_keywords:
- C2162
helpviewer_keywords:
- C2162
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
ms.openlocfilehash: 39b7cc4828cad50e9ac5056e489de319a7eb7db8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177967"
---
# <a name="compiler-error-c2162"></a>컴파일러 오류 C2162

매크로 정식 매개 변수가 필요 합니다.

문자열 화 연산자 (#) 뒤에 있는 토큰은 정식 매개 변수 이름이 아닙니다.

## <a name="example"></a>예제

다음 샘플에서는 C2162를 생성 합니다.

```cpp
// C2162.cpp
// compile with: /c
#include <stdio.h>

#define print(a) printf_s(b)   // OK
#define print(a) printf_s(#b)    // C2162
```
