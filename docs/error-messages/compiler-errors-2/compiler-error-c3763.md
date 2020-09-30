---
title: 컴파일러 오류 C3763
ms.date: 11/04/2016
f1_keywords:
- C3763
helpviewer_keywords:
- C3763
ms.assetid: 58b1f079-cd1d-46e0-9431-ea18210106b7
ms.openlocfilehash: 7ccb3d846982bbf9a52a7267549f6481b5a1bd9b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503955"
---
# <a name="compiler-error-c3763"></a>컴파일러 오류 C3763

' type ': ' retval ' 및 ' o u t '는 데이터 포인터 형식에만 사용할 수 있습니다.

[Out](../../windows/attributes/out-cpp.md) 또는 [retval](../../windows/attributes/retval.md) 특성은 포인터 형식의 매개 변수에만 나타날 수 있습니다. 특성을 제거 하거나 포인터 형식의 매개 변수를 만듭니다.

다음 샘플에서는 C3763를 생성 합니다.

```cpp
// C3763.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlplus.h>
#include <atlcom.h>

[ module(name=test) ];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IF84 : IDispatch
{
   [id(0x00000002)]HRESULT m2([out]unsigned char);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class CF84 : public IF84
{   // C3763
public:
   HRESULT __stdcall m2(unsigned char i)
   {
      return S_OK;
   }
};

int main()
{
}
```
