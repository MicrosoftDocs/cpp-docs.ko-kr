---
title: 컴파일러 오류 C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 8a12bdfaf0931fb0a94dafc289f9ae39aef61f23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757239"
---
# <a name="compiler-error-c3765"></a>컴파일러 오류 C3765

' event ': event_receiver로 표시 된 ' type ' 클래스/구조체에서 이벤트를 정의할 수 없습니다.

클래스가 [event_receiver](../../windows/event-receiver.md) 특성으로 표시 되는 경우 클래스는 [__event](../../cpp/event.md) 선언을 포함할 수 없습니다.

다음 샘플에서는 C3765를 생성 합니다.

```cpp
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```
