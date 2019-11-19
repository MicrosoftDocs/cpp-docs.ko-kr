---
title: 컴파일러 경고 (수준 1) C4533
ms.date: 11/04/2016
f1_keywords:
- C4533
helpviewer_keywords:
- C4533
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
ms.openlocfilehash: 6ee88af66238497216d7e5dab497394a58a55805
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965760"
---
# <a name="compiler-warning-level-1-c4533"></a>컴파일러 경고 (수준 1) C4533

' variable ' 초기화는 ' 명령 '에 의해 생략 됩니다.

프로그램의 명령이 제어 흐름을 변경 하 여 변수를 초기화 한 명령이 실행 되지 않았습니다. 다음 샘플에서는 C4533를 생성 합니다.

```cpp
// C4533.cpp
// compile with: /W1
#include <stdio.h>

struct A
{
   int m_data;
};

int main()
{
   if (1)
   {
      goto Label;
   }

   A a = { 100 };

   Label:   // C4533
      printf("\n%d", a.m_data);   // prints an uninitialized value
}
```