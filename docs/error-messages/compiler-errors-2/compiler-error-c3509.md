---
description: '자세한 정보: 컴파일러 오류 C3509'
title: 컴파일러 오류 C3509
ms.date: 11/04/2016
f1_keywords:
- C3509
helpviewer_keywords:
- C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
ms.openlocfilehash: 58accbf4d408a2d0ce4181b0ab35db003d2d6f39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113144"
---
# <a name="compiler-error-c3509"></a>컴파일러 오류 C3509

' type ': 자동화 반환 형식이 잘못 되었습니다. 매개 변수가 ' t r u e '로 표시 된 경우 반환 형식은 ' void ', ' HRESULT ' 또는 ' i n t ' 이어야 합니다.

COM 인터페이스의 메서드는 void 또는 HRESULT를 반환 해야 합니다.

다음 샘플에서는 C3509를 생성 합니다.

```cpp
// C3509.cpp
#define _ATL_DEBUG_QI

#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers
#define STRICT
#ifndef _WIN32_WINNT
#define _WIN32_WINNT 0x0400
#endif

#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
extern CComModule _Module;
#include <atlcom.h>
#include <atlctl.h>
#include <atlstr.h>

[module(name=oso)];

[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]
__interface I {
   [id(1)] int f([out, retval] int*);   // C3509
   // try the following line instead
   // [id(1)] void f([out, retval] int*);
};

[coclass, uuid(00000000-0000-0000-0000-000000000002)]
struct C : I {
   int f(int*) {
   // try the following line instead, and delete return statement
   // void f(int*) {
      return 0;
   }
};

int main() {
}
```
