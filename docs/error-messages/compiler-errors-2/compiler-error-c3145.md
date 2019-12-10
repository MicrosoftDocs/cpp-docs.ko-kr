---
title: 컴파일러 오류 C3145
ms.date: 11/04/2016
f1_keywords:
- C3145
helpviewer_keywords:
- C3145
ms.assetid: f165c874-0f51-45c7-85e8-ebe321cbc168
ms.openlocfilehash: 10ce7f9e6fac09401892304f2803ea76c226fab5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746008"
---
# <a name="compiler-error-c3145"></a>컴파일러 오류 C3145

'object': 전역 또는 정적 변수는 WinRT 또는 관리되는 형식 'type'을 가질 수 없습니다.

함수 범위 내에서만 CLR 또는 WinRT 개체를 정의할 수 있습니다.

다음 샘플에서는 C3145 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3145.cpp
// compile with: /clr
using namespace System;
ref class G {};

G ^ ptr;   // C3145
G ^ ptr2 = gcnew G;   // C3145

ref class GlobalObjects {
public:
   static G ^ ptr;   // OK
   static G ^ ptr2 = gcnew G;   // OK
};

int main() {
   G ^ ptr;   // OK
   G ^ ptr2 = gcnew G;   // OK
}
```

다음 샘플에서는 C3145 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3145b.cpp
// compile with: /clr
ref class MyClass {
public:
   static int data;
};

interior_ptr<int> p = &(MyClass::data);   // C3145

void Test(interior_ptr<int> x) {}

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   interior_ptr<int> p = &(h_MyClass->data);
}
```
