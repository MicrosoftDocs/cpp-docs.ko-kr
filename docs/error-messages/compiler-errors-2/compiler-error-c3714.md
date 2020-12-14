---
description: '자세한 정보: 컴파일러 오류 C3714'
title: 컴파일러 오류 C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: a01544558a156b746c16e731584e30bab7a77825
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241627"
---
# <a name="compiler-error-c3714"></a>컴파일러 오류 C3714

' method ': 이벤트 처리기 메서드는 ' method ' 소스와 같은 호출 규칙을 포함 해야 합니다.

원본 이벤트 메서드와 동일한 호출 규칙을 사용 하지 않는 이벤트 처리기 메서드를 정의 했습니다. 이 오류를 해결 하려면 이벤트 처리기 메서드에 소스 이벤트 메서드와 동일한 호출 규칙을 제공 합니다. 예를 들어 아래 코드에서의 호출 규칙을 `handler1` 및 `event1` 일치 ([__cdecl](../../cpp/cdecl.md) 또는 [__stdcall](../../cpp/stdcall.md) 또는 기타)로 설정 합니다. 두 선언 모두에서 호출 규칙 키워드를 제거 하면 문제가 해결 되 고 `event1` 및가 `handler1` [thiscall](../../cpp/thiscall.md) 호출 규칙을 기본값으로 수행 합니다. 자세한 내용은 [호출 규칙](../../cpp/calling-conventions.md) 을 참조 하세요.

다음 샘플에서는 C3714를 생성 합니다.

```cpp
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```
