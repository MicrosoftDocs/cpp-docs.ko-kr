---
description: '자세한 정보: 컴파일러 오류 C3709'
title: 컴파일러 오류 C3709
ms.date: 11/04/2016
f1_keywords:
- C3709
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
ms.openlocfilehash: 0c884801cc3c720df1018bf7c6d13b13465982a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241796"
---
# <a name="compiler-error-c3709"></a>컴파일러 오류 C3709

' function ': __hook/_unhook에서 이벤트를 지정 하기 위한 구문이 잘못 되었습니다. \_

[__Hook](../../cpp/hook.md) 또는 [__unhook](../../cpp/unhook.md)를 사용 하 여 이벤트 소스를 지정 하는 경우 첫 번째 매개 변수는 유효한 이벤트 메서드 여야 하 고 두 번째 매개 변수는 메서드가 아닌 유효한 이벤트 소스 개체 여야 합니다.

다음 샘플에서는 C3709를 생성 합니다.

```cpp
// C3709.cpp
// compile with: /LD
[event_source(native)]
class CEventSrc
{
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec
{
public:
   void handler1()
   {
   }

   void HookEvents(CEventSrc* pSrc)
   {
      __hook(bad, pSrc, CEventRec::handler1);   // C3709
      // Try the following line instead:
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc)
   {
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};
```
