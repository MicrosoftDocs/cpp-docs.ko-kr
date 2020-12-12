---
description: '자세한 정보: 방법: 인터페이스 정적 생성자 정의 (c + +/CLI)'
title: '방법: 인터페이스 정적 생성자 정의(C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 2cc6eca19a26f9857c029fc01c500ed9f4691e8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245904"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>방법: 인터페이스 정적 생성자 정의(C++/CLI)

인터페이스에는 정적 데이터 멤버를 초기화 하는 데 사용할 수 있는 정적 생성자가 있을 수 있습니다.  정적 생성자는 한 번만 호출 되며 정적 인터페이스 멤버에 처음으로 액세스 하기 전에 호출 됩니다.

## <a name="example"></a>예제

```cpp
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

[인터페이스 클래스](../extensions/interface-class-cpp-component-extensions.md)
