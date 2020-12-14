---
description: '자세한 정보: 컴파일러 오류 C3712'
title: 컴파일러 오류 C3712
ms.date: 11/04/2016
f1_keywords:
- C3712
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
ms.openlocfilehash: 530666d72ff72abef1286d594922dc877907b4e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241666"
---
# <a name="compiler-error-c3712"></a>컴파일러 오류 C3712

' method ': 이벤트 처리기 메서드는 ' method ' 소스와 같은 형식을 반환 해야 합니다.

원본 이벤트 메서드와 동일한 형식을 반환 하지 않는 이벤트 처리기 메서드를 정의 했습니다. 이 오류를 해결 하려면 이벤트 처리기 메서드를 소스 이벤트 메서드와 동일한 반환 형식으로 지정 합니다.

다음 샘플에서는 C3712를 생성 합니다.

```cpp
// C3712.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   int handler1() { return 0; }
   // try the following line instead
   // void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
};
```
