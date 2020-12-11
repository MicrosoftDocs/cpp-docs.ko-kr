---
description: '자세한 정보: 컴파일러 오류 C2647'
title: 컴파일러 오류 C2647
ms.date: 11/04/2016
f1_keywords:
- C2647
helpviewer_keywords:
- C2647
ms.assetid: 1034589e-bc3e-41a6-831f-2a1a4b8a2500
ms.openlocfilehash: df434adde457ea9a3300291ec6fac2f49d806699
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160794"
---
# <a name="compiler-error-c2647"></a>컴파일러 오류 C2647

' operator ': ' type2 '에서 ' type1 '을 역 참조할 수 없습니다.

멤버 포인터 연산자 (또는)의 왼쪽 피연산자는 `->*` `.*` 오른쪽 연산자와 관련 된 형식으로 암시적으로 변환할 수 없습니다.

다음 샘플에서는 C2647를 생성 합니다.

```cpp
// C2647.cpp
class C {};
class D {};

int main() {
   D d, *pd;
   C c, *pc = 0;
   int C::*pmc = 0;
   pd->*pmc = 0;   // C2647
   d.*pmc = 0;   // C2647

   // OK
   pc->*pmc = 0;
   c.*pmc = 0;
}
```
