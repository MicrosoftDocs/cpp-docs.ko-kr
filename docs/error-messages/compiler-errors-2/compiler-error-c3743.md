---
title: 컴파일러 오류 C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: b4bb198ae883e53e7947ce7f123bb0d3f092aaf3
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500402"
---
# <a name="compiler-error-c3743"></a>컴파일러 오류 C3743

event_receiver의 ' layout_dependent ' 매개 변수가 true 인 경우에만 전체 인터페이스를 후크/언 후크 할 수 있습니다.

[__Unhook](../../cpp/unhook.md) 함수는 `layout_dependent` [event_receiver](../../windows/attributes/event-receiver.md) 클래스의 매개 변수에 전달 된 값에 따라 소요 되는 매개 변수의 수에 따라 달라 집니다.

다음 샘플에서는 C3743를 생성 합니다.

```cpp
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```
