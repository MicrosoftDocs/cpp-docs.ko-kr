---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4197'
title: 컴파일러 경고 (수준 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: f52c37e28ce681b96158b7e1f10fef3e9f121522
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344213"
---
# <a name="compiler-warning-level-3-c4197"></a>컴파일러 경고 (수준 3) C4197

' type ': 캐스트의 최상위 volatile은 무시 됩니다.

컴파일러가 [volatile](../../cpp/volatile-cpp.md)로 정규화 된 r 값 형식에 대 한 캐스트 또는 volatile로 정규화 된 형식에 대 한 r 값 형식의 캐스트를 검색 했습니다. C 표준 (6.5.3)에 따라 정규화 된 형식과 연결 된 속성은 l-value 식에만 의미가 있습니다.

다음 샘플에서는 C4197를 생성 합니다.

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```
