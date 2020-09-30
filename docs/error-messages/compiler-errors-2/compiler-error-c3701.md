---
title: 컴파일러 오류 C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: c15cd9ce841d79787b3be9829c76038803b54d4d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508057"
---
# <a name="compiler-error-c3701"></a>컴파일러 오류 C3701

' function ': event_source에 이벤트가 없습니다.

이벤트 메서드가 없는 클래스에서 [event_source](../../windows/attributes/event-source.md) 를 사용 하려고 했습니다. 이 오류를 해결 하려면 하나 이상의 이벤트를 클래스에 추가 합니다.

다음 샘플에서는 C3701를 생성 합니다.

```cpp
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```
