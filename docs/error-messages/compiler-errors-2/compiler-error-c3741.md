---
description: '자세한 정보: 컴파일러 오류 C3741'
title: 컴파일러 오류 C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: 158555995449416da23120cafe16262cbb1a6208
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340257"
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
