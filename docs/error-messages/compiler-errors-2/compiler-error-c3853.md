---
description: '자세한 정보: 컴파일러 오류 C3853'
title: 컴파일러 오류 C3853
ms.date: 11/04/2016
f1_keywords:
- C3853
helpviewer_keywords:
- C3853
ms.assetid: 5b71805d-52b4-44ec-80ae-37c68d876f6a
ms.openlocfilehash: c10306fd8626475a0ac3dbb7b9e14b7773e4157b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328185"
---
# <a name="compiler-error-c3853"></a>컴파일러 오류 C3853

' = ': 함수 참조를 통해 참조 또는 할당을 다시 초기화할 수 없습니다.

함수는 lvalue가 아니므로 함수를 통해 참조에 할당할 수 없습니다.

다음 샘플에서는 C3853를 생성 합니다.

```cpp
// C3853.cpp
// compile with: /EHsc
#include <iostream>
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   rf = afunc;   // C3853, can't reassign to a ref that's an lvalue
   int i = 99;
   int & ri = i;
   std::cout << i << std::endl;
   ri = 0;   // OK, i = 88;
   std::cout << i << std::endl;
}
```
