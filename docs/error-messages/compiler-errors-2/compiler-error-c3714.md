---
title: 컴파일러 오류 C3714 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7102378acc2fe12335f1f2b3579f93cf02161b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109654"
---
# <a name="compiler-error-c3714"></a>컴파일러 오류 C3714

'method': '이벤트 처리기 메서드를 같은 호출 규칙의 원본으로 메서드가 있어야 '

원본 이벤트 메서드와 같은 호출 규칙을 사용 하지 않는 이벤트 처리기 메서드를 정의 합니다. 이 오류를 해결 하려면 이벤트 처리기 메서드를 원본 이벤트 메서드와와 동일한 호출 규칙을 제공 합니다. 예를 들어 아래 코드의 호출 규칙을 만들 `handler1` 하 고 `event1` 일치 ([__cdecl](../../cpp/cdecl.md) 또는 [__stdcall](../../cpp/stdcall.md) 등). 제거 규칙 키워드 () 선언 모두에서 호출 또한 문제를 해결 하 고 발생할 `event1` 하 고 `handler1` 를 기본값으로 합니다 [thiscall](../../cpp/thiscall.md) 호출 규칙. 참조 [호출 규칙](../../cpp/calling-conventions.md) 자세한 내용은 합니다.

다음 샘플에서는 C3714 오류가 생성 됩니다.

```
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