---
description: '자세한 정보: 컴파일러 오류 C3920'
title: 컴파일러 오류 C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: b4cb793744126ee7bc91d18692d25439880fc672
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326575"
---
# <a name="compiler-error-c3920"></a>컴파일러 오류 C3920

' operator ' ': 후 위 증가/감소 WinRT 또는 CLR 연산자를 정의할 수 없습니다. 후 위 WinRT 또는 CLR 연산자를 호출 하면 해당 접두사 WinRT 또는 CLR 연산자 (op_Increment/op_Decrement)가 호출 되지만 후 위 의미 체계가 사용 됩니다.

Windows 런타임 및 CLR은 후위 연산자를 지원하지 않으며, 사용자 정의 후위 연산자는 허용되지 않습니다.  전위 연산자를 정의할 수 있으며, 그러면 전위 연산자가 전위 증가 작업 및 후위 증가 작업에 모두 사용됩니다.

다음 샘플에서는 C3920 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};
```
