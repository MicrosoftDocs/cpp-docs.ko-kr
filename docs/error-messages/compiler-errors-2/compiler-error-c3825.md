---
title: 컴파일러 오류 C3825
ms.date: 11/04/2016
f1_keywords:
- C3825
helpviewer_keywords:
- C3825
ms.assetid: 18e204a1-f26e-42c6-8d74-2b49cc95f940
ms.openlocfilehash: ddb665dab303b3133d4018910c2142a20a889bb0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390583"
---
# <a name="compiler-error-c3825"></a>컴파일러 오류 C3825

'class': WinRTclass 또는 관리 되는 관리 되는 지원 또는 WinRTevents만 있습니다.

관리되는 클래스에서는 .NET 이벤트만 지원됩니다. Windows 런타임 클래스에서는 Windows 런타임 이벤트만 지원됩니다. 관리 코드에서 이 오류를 해결하려면 `event_source` 및 `event_receiver`의 형식 매개 변수를 `native`에서 `managed`로 변경합니다. 또는 특성을 제거합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3825를 생성하고 해결 방법을 보여 줍니다.

```
// C3825a.cpp
// compile with: /clr
public delegate void del1();

[event_source(native)]           // To fix, change 'native' to 'managed' or delete this line
ref class CEventSrc
{
public:
   event del1^ event1;       // C3825

   void FireEvents() {
      event1();
   }
};

[event_receiver(native)]         // To fix, change 'native' to 'managed' or delete this line
ref class CEventRec
{
public:
   void handler1()
   {
      System::Console::WriteLine("Executing handler1().\n");
   }
   void HookEvents(CEventSrc^ pSrc)
   {
      pSrc->event1 += gcnew del1(this, &CEventRec::handler1);
   }
   void UnhookEvents(CEventSrc^ pSrc)
   {
      pSrc->event1 -= gcnew del1(this, &CEventRec::handler1);
   }
};

int main()
{
   CEventSrc^ pEventSrc = gcnew CEventSrc;
   CEventRec^ pEventRec = gcnew CEventRec;
   pEventRec->HookEvents(pEventSrc);
   pEventSrc->FireEvents();
   pEventRec->UnhookEvents(pEventSrc);
}
```