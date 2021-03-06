---
description: '자세한 정보: 컴파일러 오류 C3719'
title: 컴파일러 오류 C3719
ms.date: 11/04/2016
f1_keywords:
- C3719
helpviewer_keywords:
- C3719
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
ms.openlocfilehash: a05e6cf7ee1aa67f3e8aa3e1fab737b9f5bc2969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239079"
---
# <a name="compiler-error-c3719"></a>컴파일러 오류 C3719

' interface ': 인터페이스 기반 이벤트 소스는 COM 이벤트에만 사용할 수 있습니다.

COM이 아닌 컨텍스트에서 인터페이스를 선언 했습니다.

다음 샘플에서는 C3719를 생성 합니다.

```cpp
// C3719a.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];

[object]
__interface I {
   HRESULT func1();
};

[event_source(native), coclass]
struct A {
   __event __interface I;   // C3719

   // try the following line instead
   // __event func2();
};

int main() {
}
```

이 오류를 해결 하려면 [object](../../windows/attributes/object-cpp.md), [coclass](../../windows/attributes/coclass.md), [event_source](../../windows/attributes/event-source.md)및 [event_receiver](../../windows/attributes/event-receiver.md) 특성을 적절 하 게 적용 하 여 인터페이스 COM 클래스를 사용 하는 클래스를 만듭니다. 예를 들어:

```cpp
// C3719b.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="xx")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f();
};

[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]
struct MyStruct {
   __event __interface I;
};

[event_receiver(com)]
struct MyStruct2 {
   void f() {
   }
   MyStruct2(I* pB) {
      __hook(&I::f, pB, &MyStruct2::f);
   }
};

int main()
{
}
```
