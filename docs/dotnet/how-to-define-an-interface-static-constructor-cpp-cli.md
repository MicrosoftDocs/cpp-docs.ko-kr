---
title: '방법: 인터페이스 정적 생성자 정의(C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 0617454e0957dccc7e28a5172a40273b5d93bede
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566389"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>방법: 인터페이스 정적 생성자 정의(C++/CLI)

인터페이스 정적 데이터 멤버 초기화를 사용할 수 있는 정적 생성자를 가질 수 있습니다.  정적 생성자는 한 번만 호출 됩니다 및 처음 정적 인터페이스 멤버에 액세스 하기 전에 호출 됩니다.

## <a name="example"></a>예제

```
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>참고 항목

[인터페이스 클래스](../windows/interface-class-cpp-component-extensions.md)