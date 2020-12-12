---
description: '자세한 정보: 컴파일러 오류 C2749'
title: 컴파일러 오류 C2749
ms.date: 11/04/2016
f1_keywords:
- C2749
helpviewer_keywords:
- C2749
ms.assetid: a81aef36-cdca-4d78-89d5-b72eff2500b2
ms.openlocfilehash: 582bc035411c8ee77684f89ca841260a4391340a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122891"
---
# <a name="compiler-error-c2749"></a>컴파일러 오류 C2749

' type ':/clr: safe를 사용 하 여 관리 되는 클래스에 대 한 핸들만 throw 하거나 catch 할 수 있습니다.

**/Clr: safe** 를 사용 하는 경우 참조 형식만 throw 하거나 catch 할 수 있습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2749를 생성 합니다.

```cpp
// C2749.cpp
// compile with: /clr:safe
ref struct MyStruct {
public:
   int i;
};

int main() {
   MyStruct ^x = gcnew MyStruct;

   // Delete the following 4 lines to resolve.
   try {
      throw (1);   // C2749
   }
   catch(int){}

   // OK
   try {
      throw (x);
   }
   catch(MyStruct ^){}
}
```
