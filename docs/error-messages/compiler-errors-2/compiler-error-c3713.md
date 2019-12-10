---
title: 컴파일러 오류 C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: d78d1fb3028e8618035c1c6f7bb3eb0f65409dd2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753356"
---
# <a name="compiler-error-c3713"></a>컴파일러 오류 C3713

' method ': 이벤트 처리기 메서드는 ' method ' 소스와 같은 함수 매개 변수를 포함 해야 합니다.

원본 이벤트 메서드와 동일한 매개 변수를 사용 하지 않는 이벤트 처리기 메서드를 정의 했습니다. 이 오류를 해결 하려면 이벤트 처리기 메서드에 원본 이벤트 메서드와 동일한 매개 변수를 지정 합니다.

다음 샘플에서는 C3713를 생성 합니다.

```cpp
// C3713.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1(int nValue);
   // try the following line instead
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713
   }
};
```
