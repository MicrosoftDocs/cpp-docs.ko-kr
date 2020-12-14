---
description: '자세한 정보: 컴파일러 오류 C3732'
title: 컴파일러 오류 C3732
ms.date: 11/04/2016
f1_keywords:
- C3732
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
ms.openlocfilehash: 406acf356ee0bec09eb5d9e218114256f9c58858
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245059"
---
# <a name="compiler-error-c3732"></a>컴파일러 오류 C3732

' interface ': COM 이벤트를 발생 시키는 사용자 지정 인터페이스는 IDispatch에서 상속할 수 없습니다.

COM 이벤트를 지 원하는 인터페이스는에서 상속할 수 없습니다 `IDispatch` . 자세한 내용은 [COM에서 이벤트 처리](../../cpp/event-handling-in-com.md)를 참조 하세요.

다음 오류는 C3732을 생성 합니다.

```cpp
// C3732.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="test")];

// to resolve this C3732, use dual instead of object
// or inherit from IUnknown
[ object ]
__interface I : IDispatch
{
};

[ event_source(com), coclass ]
struct A
{
   __event __interface I;   // C3732
};

int main()
{
}
```
