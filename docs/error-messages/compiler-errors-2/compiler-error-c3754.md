---
description: '자세한 정보: 컴파일러 오류 C3754'
title: 컴파일러 오류 C3754
ms.date: 11/04/2016
f1_keywords:
- C3754
helpviewer_keywords:
- C3754
ms.assetid: 14b877bc-9277-40ec-af1c-196a58b45f10
ms.openlocfilehash: 1f6c32a94caf6b2045f177480f76aa0c7fc2a7fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340140"
---
# <a name="compiler-error-c3754"></a>컴파일러 오류 C3754

대리자 생성자: ' type ' 형식의 인스턴스에서는 ' function ' 멤버 함수를 호출할 수 없습니다.

함수를 포함 하지 않는 형식에 대 한 포인터를 통해 함수를 호출 했습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3754를 생성 합니다.

```cpp
// C3754a.cpp
// compile with: /clr
using namespace System;

delegate void MyDel();

interface class MyInterface {};

ref struct MyClass : MyInterface {
   void f() {}
};

int main() {
   MyInterface^ p = gcnew MyClass;
   MyDel^ q = gcnew MyDel(p, &MyClass::f);   // C3754
   // try the following line instead
//   MyDel^ q = gcnew MyDel(safe_cast<MyClass^>(p), &MyClass::f);
}
```
