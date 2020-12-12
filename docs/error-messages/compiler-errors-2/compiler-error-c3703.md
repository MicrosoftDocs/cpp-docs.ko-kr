---
description: '자세한 정보: 컴파일러 오류 C3703'
title: 컴파일러 오류 C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 9d7f24785225cff6623ac2046823a7fa7cf39786
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119933"
---
# <a name="compiler-error-c3703"></a>컴파일러 오류 C3703

' event handler ': 이벤트 처리기 메서드는 ' event ' 소스와 동일한 저장소 클래스를 포함 해야 합니다.

[이벤트](../../cpp/event-handling.md) 에 후크 되는 이벤트 처리기와 다른 저장소 클래스가 있습니다. 예를 들어 이벤트 처리기가 정적 멤버 함수이 고 이벤트가 static이 아닌 경우이 오류가 발생 합니다. 이 오류를 해결 하려면 이벤트와 이벤트 처리기에 동일한 저장소 클래스를 지정 합니다.

다음 샘플에서는 C3703를 생성 합니다.

```cpp
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```
