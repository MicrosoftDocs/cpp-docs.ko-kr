---
description: '자세한 정보: 컴파일러 오류 C2513'
title: 컴파일러 오류 C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: d1238acd8dc2d56e4757ffb986d4db47c047e76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212898"
---
# <a name="compiler-error-c2513"></a>컴파일러 오류 C2513

' type ': ' = ' 앞에 변수를 선언 하지 않았습니다.

형식 지정 자가 변수 식별자가 없는 선언에 나타납니다.

다음 샘플에서는 C2513를 생성 합니다.

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

이 오류는 Visual Studio .NET 2003에 대 한 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. typedef의 초기화는 더 이상 허용 되지 않습니다. Typedef의 초기화는 표준에서 허용 되지 않으며 이제 컴파일러 오류가 생성 됩니다.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

대신 **`typedef`** 집계 이니셜라이저 목록을 사용 하 여 변수를 정의 하기 위해를 삭제 하는 것이 좋습니다 .이는 형식과 동일한 이름의 변수를 만들고 형식 이름을 숨기 므로 사용 하지 않는 것이 좋습니다.
