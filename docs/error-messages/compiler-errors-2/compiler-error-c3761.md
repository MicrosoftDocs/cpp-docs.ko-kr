---
title: 컴파일러 오류 C3761
ms.date: 11/04/2016
f1_keywords:
- C3761
helpviewer_keywords:
- C3761
ms.assetid: 0c16f093-7a78-4838-b90b-0c67ef6e9270
ms.openlocfilehash: 615992a2cf7563ab474f2547098a645dde0a31f8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501260"
---
# <a name="compiler-error-c3761"></a>컴파일러 오류 C3761

' function ': ' retval '은 함수의 마지막 인수에만 사용할 수 있습니다.

[Retval](../../windows/attributes/retval.md) 특성이 목록에서 마지막 인수가 아닌 함수 인수에 사용 되었습니다.

다음 샘플에서는 C3761를 생성 합니다.

```cpp
// C3761.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name=test) ];

[dispinterface]
__interface I
{
   [id(1)] HRESULT func([out, retval] int* i, [in] int j);
   // try the following line instead
   // [id(1)] HRESULT func([in] int i, [out, retval] int* j);
};

[coclass]
struct C : I {   // C3761
   HRESULT func(int* i, int j)
   // try the following line instead
   // HRESULT func(int j, int* i)
   {
      return S_OK;
   }
};

int main()
{
}
```
