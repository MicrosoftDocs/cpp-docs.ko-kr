---
description: '자세한 정보: 컴파일러 오류 C3642'
title: 컴파일러 오류 C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 77d65d2bb2c426fe78671328b0eccab739b9dabe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340309"
---
# <a name="compiler-error-c3642"></a>컴파일러 오류 C3642

' return_type/args ': 네이티브 코드에서 __clrcall 호출 규칙을 사용 하 여 함수를 호출할 수 없습니다.

[__Clrcall](../../cpp/clrcall.md) 호출 규칙으로 표시 된 함수는 네이티브 (비관리) 코드에서 호출할 수 없습니다.

*return_type/targs* 는 함수 이름 또는 호출 하려는 함수의 형식입니다 `__clrcall` .  함수 포인터를 통해를 호출 하는 경우 형식이 사용 됩니다.

네이티브 컨텍스트에서 관리 되는 함수를 호출 하려면 함수를 호출 하는 "래퍼" 함수를 추가 하면 됩니다 `__clrcall` . 또는 CLR 마샬링 메커니즘을 사용할 수 있습니다. 자세한 내용은 [방법: PInvoke를 사용 하 여 함수 포인터 마샬링을](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) 참조 하세요.

다음 샘플에서는 C3642를 생성 합니다.

```cpp
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
