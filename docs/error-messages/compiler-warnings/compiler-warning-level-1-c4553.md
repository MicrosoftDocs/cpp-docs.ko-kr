---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4553'
title: 컴파일러 경고(수준 1) C4553
ms.date: 11/04/2016
f1_keywords:
- C4553
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
ms.openlocfilehash: 93d775e1a91f8306240824f99da1fae107963696
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265898"
---
# <a name="compiler-warning-level-1-c4553"></a>컴파일러 경고(수준 1) C4553

' operator ': 연산자는 영향을 주지 않습니다. ' operator '를 의도 했습니까?

식 문에 부작용이 없는 연산자가 있는 경우에는 실수가 될 수 있습니다.

다음 샘플에서는 C4553를 생성 합니다.

```cpp
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```
