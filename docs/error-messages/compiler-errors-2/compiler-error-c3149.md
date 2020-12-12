---
description: '자세한 정보: 컴파일러 오류 C3149'
title: 컴파일러 오류 C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 596a8d2728e7598a737da4aa5a1650df669db969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322092"
---
# <a name="compiler-error-c3149"></a>컴파일러 오류 C3149

' type ': 최상위 ' char ' 없이는 여기에이 형식을 사용할 수 없습니다.

선언이 올바르게 지정 되지 않았습니다.

예를 들어 전역 범위에서 CLR 형식을 정의 하 고 해당 형식의 변수를 정의의 일부로 만들려고 했을 수 있습니다. CLR 형식의 전역 변수를 사용할 수 없기 때문에 컴파일러에서 C3149을 생성 합니다.

이 오류를 해결 하려면 함수 또는 형식 정의 내에 CLR 형식의 변수를 선언 합니다.

다음 샘플에서는 C3149를 생성 합니다.

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

다음 샘플에서는 C3149를 생성 합니다.

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
