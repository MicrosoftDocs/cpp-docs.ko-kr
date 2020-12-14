---
description: '자세한 정보: 컴파일러 오류 C3833'
title: 컴파일러 오류 C3833
ms.date: 11/04/2016
f1_keywords:
- C3833
helpviewer_keywords:
- C3833
ms.assetid: 8152be53-e01e-48cd-9eef-9de38723664c
ms.openlocfilehash: e43ec93c222d3190bacb427cc06c0eae643fcfe1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249192"
---
# <a name="compiler-error-c3833"></a>컴파일러 오류 C3833

' type ': pointer_type의 대상 형식이 잘못 되었습니다.

[Interior_ptr](../../extensions/interior-ptr-cpp-cli.md) 또는 [pin_ptr](../../extensions/pin-ptr-cpp-cli.md) 잘못 선언 되었습니다.

다음 샘플에서는 C3833를 생성 합니다.

```cpp
// C3833.cpp
// compile with: /clr

ref class MyClass {
public:
   int data;
   MyClass() : data(35) {}
};

int main() {
   interior_ptr<MyClass> p;   // C3833

   // OK
   MyClass ^ h_MyClass = gcnew MyClass;
   interior_ptr<int> i = &(h_MyClass->data);
   System::Console::WriteLine(*i);
}
```

다음 샘플에서는 C3833를 생성 합니다.

```cpp
// C3833b.cpp
// compile with: /clr /c
ref class G {
public:
   int i;
};

int main() {
   G ^ pG = gcnew G;
   pin_ptr<G> ppG = &pG;   // C3833 can't pin a whole object

   // OK
   pin_ptr<int> ppG2 = &pG->i;
   *ppG2 = 54;
   int * pi = ppG2;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);

   *pi = 55;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);

   *ppG2 = 56;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);
}
```
