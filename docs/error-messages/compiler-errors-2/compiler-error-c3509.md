---
title: 컴파일러 오류 C3509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3509
dev_langs:
- C++
helpviewer_keywords:
- C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da42291d41a3068f8c75d839b94aee85e5be3ee9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034338"
---
# <a name="compiler-error-c3509"></a>컴파일러 오류 C3509

'type': 자동화 반환 형식이 잘못 되었습니다. 'void', 'HRESULT' 또는 'SCODE' 해야 경우 매개 변수는 표시 된 'retval', 반환 형식

COM 인터페이스의 메서드는 void 또는 HRESULT를 반환 해야 합니다.

다음 샘플에서는 C3509 오류가 생성 됩니다.

```
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