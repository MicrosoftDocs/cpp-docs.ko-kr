---
title: 컴파일러 오류 C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: e551fa3dbf67d2158081bea9d19051d4703d9c43
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501304"
---
# <a name="compiler-error-c3741"></a>컴파일러 오류 C3741

' class ': event_receiver = true의 ' layout_dependent ' 매개 변수를 사용할 경우 coclass 여야 합니다.

`layout_dependent=true` [Event_receiver](../../windows/attributes/event-receiver.md) 클래스의 경우 클래스에 [coclass](../../windows/attributes/coclass.md) 특성도 있어야 합니다.

다음 샘플에서는 C3741를 생성 합니다.

```cpp
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```
