---
description: '자세한 정보: 컴파일러 오류 C2107'
title: 컴파일러 오류 C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: aee5e7384f3d0a58265d1cc36448c7fb49c71f4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335279"
---
# <a name="compiler-error-c2107"></a>컴파일러 오류 C2107

잘못 된 인덱스입니다. 간접 참조는 허용 되지 않습니다.

첨자가 포인터로 계산 되지 않는 식에 적용 됩니다.

## <a name="example"></a>예제

값 형식의 포인터를 잘못 사용 하 여 **`this`** 형식의 기본 인덱서에 액세스 하는 경우 C2107이 발생할 수 있습니다. 자세한 내용은 [이 포인터의 의미 체계](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)를 참조 하세요.

다음 샘플에서는 C2107를 생성 합니다.

```cpp
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
