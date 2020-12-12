---
description: '자세한 정보: 컴파일러 오류 C2715'
title: 컴파일러 오류 C2715
ms.date: 11/04/2016
f1_keywords:
- C2715
helpviewer_keywords:
- C2715
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
ms.openlocfilehash: 6575e5b678189834a035f9e236b3d768dc7ab368
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320810"
---
# <a name="compiler-error-c2715"></a>컴파일러 오류 C2715

' type ':이 형식을 throw 하거나 catch 할 수 없습니다.

관리 코드에서 예외 처리를 사용 하는 경우 값 형식은 올바른 인수가 아닙니다. 자세한 내용은 [예외 처리](../../extensions/exception-handling-cpp-component-extensions.md) 를 참조 하십시오.

```cpp
// C2715a.cpp
// compile with: /clr
using namespace System;

value struct V {
   int i;
};

void f1() {
   V v;
   v.i = 10;
   throw v;   // C2715
   // try the following line instead
   // throw ((V^)v);
}

int main() {
   try {
      f1();
   }

   catch(V v) { if ( v.i == 10 ) {   // C2715
   // try the following line instead
   // catch(V^ pv) { if ( pv->i == 10 ) {
         Console::WriteLine("caught 10 - looks OK");
      }
      else {
         Console::WriteLine("catch looks bad");
      }
   }
   catch(...) {
      Console::WriteLine("catch looks REALLY bad");
   }
}
```
