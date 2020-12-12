---
description: '자세한 정보: 컴파일러 오류 C3702'
title: 컴파일러 오류 C3702
ms.date: 11/04/2016
f1_keywords:
- C3702
helpviewer_keywords:
- C3702
ms.assetid: 14fcc20e-4404-45d7-be54-e4f09332fa5a
ms.openlocfilehash: a8ba08192b38f24036980151421fc61b85ec3354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278248"
---
# <a name="compiler-error-c3702"></a>컴파일러 오류 C3702

' function ': COM 이벤트에는 ATL이 필요 합니다.

필요한 ATL 헤더 파일을 포함 하지 않고 COM 이벤트를 사용 하려고 했습니다.

다음 샘플에서는 C3702를 생성 합니다.

```cpp
// C3702.cpp
// uncomment the following line to resolve
// #define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name=idid, uuid="12341234-1234-1234-1234-123412341234")];

[object]
__interface IEvents : IUnknown
{
   HRESULT event1([in] int i);
};

[dual]
__interface IBase
{
   HRESULT fireEvents();
};

[coclass, event_source(com)]
class CEventSrc : public IBase
{
   public:
   __event __interface IEvents;

   HRESULT fireEvents()
   {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};   // C3702

int main() {
}
```
