---
description: '자세한 정보: 컴파일러 오류 C3717'
title: 컴파일러 오류 C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: fecd417af1eceb40ef8b8e48fda40b3ec5e5b36a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189433"
---
# <a name="compiler-error-c3717"></a>컴파일러 오류 C3717

' method ': 이벤트를 발생 시키는 메서드를 정의할 수 없습니다.

구현을 포함 하는 이벤트 메서드를 선언 했습니다. [__Event](../../cpp/event.md) 메서드 선언에는 정의를 사용할 수 없습니다. 이 오류를 해결 하려면 이벤트 메서드 선언에 정의가 포함 되지 않도록 합니다. 예를 들어 아래 코드에서 주석으로 표시 된 선언에서 함수 본문을 제거 합니다 `event1` .

다음 샘플에서는 C3717를 생성 합니다.

```cpp
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
