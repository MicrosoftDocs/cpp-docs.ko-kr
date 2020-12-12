---
description: '자세히 알아보기: interface 클래스 (c + +/CLI 및 c + +/CX)'
title: 인터페이스 클래스(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 8d6fd1eda0ddaaf6ab995e09ad1d84f78fcc91be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119022"
---
# <a name="interface-class--ccli-and-ccx"></a>인터페이스 클래스(C++/CLI 및 C++/CX)

인터페이스를 선언합니다.  네이티브 인터페이스에 대한 자세한 내용은 [__interface](../cpp/interface.md)를 참조하세요.

## <a name="all-runtimes"></a>모든 런타임

### <a name="syntax"></a>구문

```cpp
interface_access interface class name : inherit_access base_interface {};
interface_access interface struct name : inherit_access base_interface {};
```

### <a name="parameters"></a>매개 변수

*interface_access*<br/>
어셈블리 외부에서 인터페이스의 접근성입니다.  가능한 값은 **`public`** 및 **`private`** 입니다.  **`private`** 가 기본값입니다. 중첩된 인터페이스에는 *interface_access* 지정자를 사용할 수 없습니다.

*name*<br/>
인터페이스의 이름입니다.

*inherit_access*<br/>
*base_interface* 의 접근성입니다.  기본 인터페이스에 대해 유일 하 게 허용 되는 액세스 가능성은 **`public`** (기본값)입니다.

*base_interface*<br/>
(선택 사항) 인터페이스 ‘이름’의 기본 인터페이스입니다.

### <a name="remarks"></a>설명

**인터페이스 구조체** 는 **인터페이스 클래스** 와 동일합니다.

인터페이스에는 함수, 이벤트 및 속성에 대한 선언을 포함할 수 있습니다.  모든 인터페이스 멤버는 public 접근성을 갖습니다. 인터페이스에 정적 데이터 멤버, 함수, 이벤트 및 속성을 포함할 수도 있으며, 이러한 정적 멤버는 인터페이스에서 정의해야 합니다.

인터페이스는 클래스를 구현할 수 있는 방법을 정의합니다. 인터페이스는 클래스가 아니며, 클래스는 인터페이스를 구현할 수만 있습니다. 클래스가 인터페이스에서 선언된 함수를 정의하는 경우 함수가 재정의되지 않고 구현됩니다. 따라서 이름 조회는 인터페이스 멤버를 포함하지 않습니다.

인터페이스에서 파생된 클래스 또는 구조체는 인터페이스의 모든 멤버를 구현해야 합니다. 인터페이스 ‘이름’을 구현하는 경우 `base_interface` 목록의 인터페이스도 구현해야 합니다.

자세한 내용은 다음을 참조하세요.

- [인터페이스 정적 생성자](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [제네릭 인터페이스(C++/CLI)](generic-interfaces-visual-cpp.md)

다른 CLR 형식에 대한 자세한 내용은 [클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)를 참조하세요.

컴파일 시간에 `__is_interface_class(type)`을 사용하여 형식이 인터페이스인지 여부를 검색할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

개발 환경에서는 키워드 (예:)를 강조 표시 하 고 F1 키를 눌러 이러한 키워드에 대 한 F1 도움말을 가져올 수 있습니다 **`interface class`** .

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

(이 언어 기능에는 Windows 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="remarks"></a>설명

(이 언어 기능에는 공용 언어 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 인터페이스를 통해 클록 함수의 동작을 정의할 수 있는 방법을 보여 줍니다.

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

다음 코드 샘플에서는 여러 인터페이스에서 동일한 시그니처를 선언하고 해당 인터페이스를 클래스에서 사용하는 함수를 구현하는 두 가지 방법을 보여 줍니다.

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
