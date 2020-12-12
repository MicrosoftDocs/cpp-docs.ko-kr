---
description: '자세한 정보: 컴파일러 오류 C3854'
title: 컴파일러 오류 C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: f6c2399ff4c38cfbb306bd90e5bb5e96b34220eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328163"
---
# <a name="compiler-error-c3854"></a>컴파일러 오류 C3854

' = ' 왼쪽의 식이 함수로 계산 됩니다. 함수에 할당할 수 없습니다. 함수는 l-value가 아닙니다.

참조를 다시 초기화할 수 없습니다. 함수에 대 한 참조를 역참조 하면 할당할 수 없는 rvalue 인 함수를 생성 합니다. 따라서 함수에 대 한 참조를 통해 할당할 수 없습니다.

다음 샘플에서는 C3854를 생성 합니다.

```cpp
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```
