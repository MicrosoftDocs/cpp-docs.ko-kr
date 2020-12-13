---
description: '자세한 정보: 컴파일러 오류 C3739'
title: 컴파일러 오류 C3739
ms.date: 11/04/2016
f1_keywords:
- C3739
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
ms.openlocfilehash: dd08b171503d7c5c4c7d46b9d06d4372513e2e73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340296"
---
# <a name="compiler-error-c3739"></a>컴파일러 오류 C3739

' class ': event_receiver의 ' layout_dependent ' 매개 변수가 true 인 경우에만 구문이 지원 됩니다.

전체 이벤트 인터페이스를 후크 하려고 했지만 `layout_dependent` [event_receiver](../../windows/attributes/event-receiver.md) 특성이 true가 아닙니다. 단일 이벤트를 한 번에 후크 해야 합니다.

다음 샘플에서는 C3739를 생성 합니다.

```cpp
// C3739.cpp
struct A
{
   __event void e();
};

// event_receiver is implied
// [ event_receiver(layout_dependent=false)]

// use the following line instead
// [event_receiver(com, layout_dependent=true), coclass ]
struct B
{
   void f();
   B(A* a)
   {
      __hook(A, a, &B::f);   // C3739
      // use the following line instead to hook a single event
      // __hook(&A::e, a, &B::f);
   }
};

int main()
{
}
```
