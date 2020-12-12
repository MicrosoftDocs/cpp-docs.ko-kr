---
description: '자세한 정보: 컴파일러 오류 C3724'
title: 컴파일러 오류 C3724
ms.date: 11/04/2016
f1_keywords:
- C3724
helpviewer_keywords:
- C3724
ms.assetid: cab8aba7-14fc-406f-8cc6-32744c8f31c1
ms.openlocfilehash: 509467b964f8b4db35d3823ff9f89be0223061f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326590"
---
# <a name="compiler-error-c3724"></a>컴파일러 오류 C3724

이벤트에 \<windows.h> 다중 스레딩을 사용 하려면 #include 해야 함

이벤트에 다중 스레딩을 사용 하는 경우에는 windows .h 파일이 필요 합니다. 이 오류를 해결 하려면 `#include <windows.h>` 이벤트 원본 및 이벤트 수신기가 정의 된 파일의 맨 위에를 추가 합니다.

```cpp
// C3724.cpp
// uncomment the following line to resolve
// #include <windows.h>

[event_source(native), threading(apartment)]
class CEventSrc {
public:
   __event void event1();   // C3724
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
