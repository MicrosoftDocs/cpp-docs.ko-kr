---
description: '자세한 정보: 컴파일러 오류 C3710'
title: 컴파일러 오류 C3710
ms.date: 11/04/2016
f1_keywords:
- C3710
helpviewer_keywords:
- C3710
ms.assetid: 18bec009-5b6f-464a-a21e-5d58a6936504
ms.openlocfilehash: 6e9e146f5ec7370043756998cd162c3e57839671
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241705"
---
# <a name="compiler-error-c3710"></a>컴파일러 오류 C3710

' function ': __hook/_unhook에서 이벤트 처리기를 지정 하기 위한 구문이 잘못 되었습니다. \_

[__Hook](../../cpp/hook.md) 또는 [__unhook](../../cpp/unhook.md)를 사용 하 여 이벤트 처리기를 지정 하는 경우 처리기는 유효한 방법 이어야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3710를 생성 합니다.

```cpp
// C3710.cpp
// compile with: /link /opt:noref
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>
#include <stdio.h>

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
        printf_s("Executing handler1().\n");
    }

    void HookEvents(CEventSrc* pSrc)
    {
        __hook(&CEventSrc::event1, pSrc, 0);   // C3710
        // try the following line instead
        // __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);
    }

    void UnhookEvents(CEventSrc* pSrc)
    {
        __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);
    }
};

int main()
{
    CEventSrc eventSrc;
    CEventRec eventRec;
    eventRec.HookEvents(&eventSrc);
    eventSrc.event1();
    eventRec.UnhookEvents(&eventSrc);
}
```
