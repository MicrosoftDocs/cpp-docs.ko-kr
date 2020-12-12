---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4460'
title: 컴파일러 경고(수준 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: 68f38ad1ad65b27f35b79495bb2edd930c25d732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334835"
---
# <a name="compiler-warning-level-4-c4460"></a>컴파일러 경고(수준 4) C4460

WinRT 또는 CLR 연산자 'operator'에는 참조에 의해 전달되는 매개 변수가 있습니다. WinRT 또는 CLR 연산자 'operator'의 의미 체계는 C++ 연산자 'operator'의 의미 체계와 다릅니다. 값으로 전달하려고 했나요?

사용자 정의 Windows 런타임 또는 CLR 연산자에 값을 참조로 전달했습니다. 함수 내부에서 값이 변경되면 함수 호출 후에 반환된 값에는 함수의 반환 값이 할당됩니다. 표준 C++에서 변경된 값은 함수 호출 후에 반영됩니다.

## <a name="example"></a>예제

다음 샘플에서는 C4460 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```
