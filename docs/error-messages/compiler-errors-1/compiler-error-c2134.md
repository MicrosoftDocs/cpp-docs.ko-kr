---
description: '자세한 정보: 컴파일러 오류 C2134'
title: 컴파일러 오류 C2134
ms.date: 11/04/2016
f1_keywords:
- C2134
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
ms.openlocfilehash: 16149c3b3f28720670c26f0fae2a89d1b7b6f8b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323113"
---
# <a name="compiler-error-c2134"></a>컴파일러 오류 C2134

' function ': 호출이 상수 식을 생성 하지 않습니다.

Constexpr로 선언 된 함수는 constexpr로 선언 된 다른 함수만 호출할 수 있습니다.

다음 샘플에서는 C2134를 생성 합니다.

```cpp
// C2134.cpp
// compile with: /c
int A() {
    return 42;
};

constexpr int B() {
    return A();  // Error C2134: 'A': call does not result in a constant expression.
}
```

해결 방법:

```cpp
// C2134b.cpp
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.
    return 42;
};

constexpr int B() {
    return A();  // No error
}
```
