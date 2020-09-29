---
title: '방법: 클래스 및 구조체 정의 및 사용 (c + +/CLI)'
description: C + +/CLI 코드에서 사용자 정의 클래스 및 구조체 형식을 만들고 사용 하는 방법입니다.
ms.date: 09/25/2020
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 17d0885d42febc1d2789c8711b54a76066ee8176
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414583"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>방법: 클래스 및 구조체 정의 및 사용 (c + +/CLI)

이 문서에서는 c + +/CLI에서 사용자 정의 참조 형식 및 값 형식을 정의 하 고 사용 하는 방법을 보여 줍니다.

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a> 개체 인스턴스화

참조 (ref) 형식은 스택 또는 네이티브 힙이 아닌 관리 되는 힙에서만 인스턴스화할 수 있습니다. 값 형식은 스택이나 관리 되는 힙에서 인스턴스화할 수 있습니다.

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> 암시적 추상 클래스

*암시적 추상 클래스* 는 인스턴스화할 수 없습니다. 클래스는 다음과 같은 경우 암시적으로 추상화 됩니다.

- 클래스의 기본 형식은 인터페이스입니다.
- 클래스는 인터페이스의 모든 멤버 함수를 구현 하지 않습니다.

인터페이스에서 파생 된 클래스에서 개체를 생성할 수 없습니다. 이는 클래스가 암시적으로 추상 일 수 있기 때문입니다. 추상 클래스에 대 한 자세한 내용은 [abstract](../extensions/abstract-cpp-component-extensions.md)를 참조 하세요.

다음 코드 예제에서는 `MyClass` 함수가 구현 되지 않았기 때문에 클래스를 인스턴스화할 수 없음을 보여 줍니다 `MyClass::func2` . 해당 예제를 컴파일하려면 `MyClass::func2`의 주석 처리를 제거하십시오.

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a> 형식 표시 유형

CLR (공용 언어 런타임) 형식의 표시 여부를 제어할 수 있습니다. 어셈블리를 참조 하는 경우 어셈블리의 형식을 어셈블리 외부에서 볼 수 있는지 여부를 제어 합니다.

`public` 형식을 `#using` 포함 하는 어셈블리에 대 한 지시문을 포함 하는 모든 소스 파일에 형식이 표시 됨을 나타냅니다.  `private` 형식을 `#using` 포함 하는 어셈블리에 대 한 지시문이 포함 된 소스 파일에 형식이 표시 되지 않음을 나타냅니다. 그러나 private 형식은 동일한 어셈블리 내에는 표시됩니다. 기본적으로 클래스에 대한 표시 유형은 `private`입니다.

기본적으로 Visual Studio 2005 이전에는 네이티브 형식이 어셈블리 외부에서 공용 액세스 가능성을 갖고 있습니다. Private 네이티브 형식이 잘못 사용 되는 위치를 확인 하려면 [컴파일러 경고 (수준 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) 를 사용 하도록 설정 합니다. [Make_public](../preprocessor/make-public.md) pragma를 사용 하 여 소스 코드 파일에서 수정할 수 없는 네이티브 형식에 public 액세스 가능성을 제공할 수 있습니다.

자세한 내용은 [#using 지시문](../preprocessor/hash-using-directive-cpp.md)을 참조하세요.

다음 샘플은 형식을 선언하고 해당 액세스 가능성을 지정한 다음 어셈블리 내부에서 이러한 형식에 액세스하는 방법을 보여 줍니다. 를 사용 하 여 전용 형식을 가진 어셈블리를 참조 하는 경우 `#using` 어셈블리의 public 형식만 표시 됩니다.

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**출력**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

이제 DLL로 빌드되는 이전 샘플을 다시 작성해 보겠습니다.

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

다음 샘플은 어셈블리 외부에서 형식에 액세스하는 방법을 보여 줍니다. 이 샘플에서 클라이언트는 이전 샘플에서 빌드한 구성 요소를 사용합니다.

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**출력**

```Output
in Public_Class
```

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a> 멤버 표시 유형

액세스 지정자 **`public`** , 및의 쌍을 사용 하 여 어셈블리 외부에서 액세스 하는 것과 다른 동일한 어셈블리 내에서 public 클래스의 멤버에 액세스할 수 있습니다. **`protected`****`private`**

이 표에서는 다양한 액세스 지정자의 효과를 요약하여 보여 줍니다.

|지정자|영향|
|---------------|------------|
|`public`|멤버는 어셈블리 내부 및 외부에서 액세스할 수 있습니다. 자세한 내용은 [`public`](../cpp/public-cpp.md)를 참조하세요.|
|`private`|멤버는 어셈블리 내부 및 외부 모두에서 액세스할 수 없습니다.  자세한 내용은 [`private`](../cpp/private-cpp.md)를 참조하세요.|
|`protected`|멤버는 파생된 형식에 한해 어셈블리 내부 및 외부에서 액세스할 수 있습니다. 자세한 내용은 [`protected`](../cpp/protected-cpp.md)를 참조하세요.|
|`internal`|멤버는 어셈블리 내부에서 public 이지만 어셈블리 외부에서는 private입니다. `internal`는 상황에 맞는 키워드입니다.  자세한 내용은 [상황에 맞는 키워드](../extensions/context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요.|
|`public protected` 또는 `protected public`|멤버는 어셈블리 내부에서 public이지만 어셈블리 외부에서는 protected입니다.|
|`private protected` 또는 `protected private`|멤버는 어셈블리 내부에서 protected이지만 어셈블리 외부에서는 private입니다.|

다음 샘플에서는 다른 액세스 지정자를 사용 하 여 선언 된 멤버를 포함 하는 public 형식을 보여 줍니다. 그런 다음 어셈블리 내에서 이러한 멤버에 대 한 액세스를 표시 합니다.

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**출력**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

이제 DLL로 이전 샘플을 빌드합니다.

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

다음 샘플에서는 이전 샘플에서 만든 구성 요소를 사용 합니다. 어셈블리 외부에서 멤버에 액세스 하는 방법을 보여 줍니다.

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**출력**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> Public 및 private 네이티브 클래스

네이티브 형식은 관리되는 형식에서 참조될 수 있습니다.  예를 들어 관리되는 형식의 함수는 네이티브 구조체 형식의 매개 변수를 사용할 수 있습니다.  관리되는 형식과 함수가 어셈블리 내에서 public이면 네이티브 형식도 public이어야 합니다.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

다음으로 네이티브 형식을 사용하는 소스 코드 파일을 만듭니다.

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

이제 클라이언트를 컴파일합니다.

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> 정적 생성자

클래스나 구조체 같은 CLR 형식은 정적 데이터 멤버를 초기화하는 데 사용할 수 있는 정적 생성자를 보유할 수 있습니다.  정적 생성자는 한 번만 호출되며 형식의 정적 멤버가 처음으로 액세스하기 전에 호출됩니다.

인스턴스 생성자는 항상 정적 생성자가 실행된 후 실행됩니다.

컴파일러는 클래스에 정적 생성자가 있는 경우 생성자에 대 한 호출을 인라인 할 수 없습니다. 클래스가 값 형식이 고 정적 생성자가 있고 인스턴스 생성자가 없는 경우 컴파일러는 멤버 함수에 대 한 호출을 인라인 할 수 없습니다. CLR은 호출을 인라인 할 수 있지만 컴파일러는 그렇지 않습니다.

정적 생성자는 CLR 에서만 호출 되기 때문에 전용 멤버 함수로 정의 합니다.

정적 생성자에 대 한 자세한 내용은 [방법: 인터페이스 정적 생성자 정의 (c + +/cli)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 를 참조 하세요.

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**출력**

```Output
in static constructor
10
11
```

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>포인터의 의미 체계 `this`

C + + \CLI를 사용 하 여 형식을 정의 하는 경우 **`this`** 참조 형식의 포인터는 *handle*형식입니다. **`this`** 값 형식의 포인터는 *내부 포인터*형식입니다.

포인터의 이러한 다양 한 의미 체계를 **`this`** 통해 기본 인덱서가 호출 될 때 예기치 않은 동작이 발생할 수 있습니다. 다음 예제에서는 참조 형식과 값 형식 모두에서 기본 인덱서에 액세스하는 올바른 방법을 보여 줍니다.

자세한 내용은 [개체 연산자에 대 한 핸들 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) 및 [Interior_ptr (c + +/cli)](../extensions/interior-ptr-cpp-cli.md) 를 참조 하세요.

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**출력**

```Output
10.89
10.89
```

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> 서명 숨기기 함수

표준 c + +에서 기본 클래스의 함수는 파생 클래스의 함수에 동일한 형식이 나 수의 매개 변수가 없더라도 파생 클래스에서 동일한 이름을 가진 함수에 의해 숨겨집니다. *이름으로 숨기기* 의미 체계 라고 합니다. 참조 형식에서 기본 클래스의 함수는 이름 및 매개 변수 목록이 모두 동일한 경우 파생 클래스의 함수에 의해서만 숨겨집니다. *서명 숨기기* 의미 체계 라고 합니다.

클래스의 모든 함수가 메타데이터에 `hidebysig`로 표시되면 클래스는 hide-by-signature 클래스라고 간주됩니다. 기본적으로에 생성 된 모든 클래스에는 **`/clr`** `hidebysig` 함수가 있습니다. 클래스에 `hidebysig` 함수가 있는 경우 컴파일러는 함수를 직접 기본 클래스의 이름으로 숨기지 않습니다. 하지만 컴파일러에서 상속 체인의 hide-by-name 클래스를 발견하는 경우 hide-by-name 동작이 계속됩니다.

hide-by-signature 의미 체계에 따라 함수가 객체에 호출되면 컴파일러는 함수 호출을 충족할 수 있는 함수가 포함된 가장 많이 파생된 클래스를 식별합니다. 호출을 충족 하는 함수가 클래스에 하나만 있는 경우 컴파일러는 해당 함수를 호출 합니다. 호출을 충족할 수 있는 함수가 클래스에 둘 이상 있는 경우 컴파일러는 오버 로드 확인 규칙을 사용 하 여 호출할 함수를 결정 합니다. 오버 로드 규칙에 대 한 자세한 내용은 [함수 오버 로드](../cpp/function-overloading.md)를 참조 하세요.

지정된 함수 호출의 경우 기본 클래스의 함수는 파생 클래스의 함수보다 조금 더 일치하는 시그니처를 가지고 있을 수 있습니다. 그러나 함수가 파생 클래스의 객체에 명시적으로 호출된 경우 파생 클래스의 함수가 호출됩니다.

반환 값은 함수 시그니처의 일부로 간주 되지 않으므로 반환 값의 형식이 서로 다른 경우에도 기본 클래스 함수가 동일한 이름을 사용 하 고 파생 클래스 함수와 동일한 종류와 수의 인수를 사용 하는 경우에는 숨겨집니다.

다음 샘플에서는 기본 클래스의 함수가 파생 클래스의 함수에 의해 숨겨지지 않는다는 것을 보여 줍니다.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**출력**

```Output
Base::Test
```

다음 샘플에서는 하나 이상의 매개 변수와 일치 하는 변환이 필요한 경우에도 Microsoft c + + 컴파일러가 가장 많이 파생 된 클래스의 함수를 호출 하 고, 함수 호출에 더 잘 일치 하는 기본 클래스의 함수를 호출 하지 않는 것을 보여 줍니다.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**출력**

```Output
Derived::Test2
```

다음 샘플은 기본 클래스에 파생 클래스와 동일한 시그니처가 있는 경우에도 함수를 숨길 수 있음을 보여 줍니다.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**출력**

```Output
Derived::Test4
97
```

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a> 복사 생성자

C++ 표준에 따르면 복사 생성자는 개체가 동일한 주소에서 생성되고 제거되는 것처럼 개체가 이동하면 호출됩니다.

그러나 MSIL로 컴파일된 함수가 네이티브 클래스 (또는 둘 이상)를 값으로 전달 하 고 네이티브 클래스에 복사 생성자 또는 소멸자가 있는 네이티브 함수를 호출 하면 복사 생성자가 호출 되지 않고 개체가 만들어진 위치와 다른 주소에서 개체가 삭제 됩니다. 클래스에 자신에 대 한 포인터가 있거나 코드에서 주소를 기준으로 개체를 추적 하는 경우이 동작으로 인해 문제가 발생할 수 있습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

다음 샘플에서는 복사 생성자가 생성 되지 않는 경우를 보여 줍니다.

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**출력**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> 소멸자 및 종료자

참조 형식의 소멸자는 리소스의 명확한 정리를 수행 합니다. 종료자는 관리 되지 않는 리소스를 정리 하 고, 소멸자가 명확 하 게 호출 하거나 가비지 수집기에 의해 불명확 하 게 호출 될 수 있습니다. 표준 c + +의 소멸자에 대 한 자세한 내용은 [소멸자](../cpp/destructors-cpp.md)를 참조 하세요.

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

CLR 가비지 수집기는 사용 되지 않는 관리 되는 개체를 삭제 하 고 더 이상 필요 하지 않을 때 해당 메모리를 해제 합니다. 그러나 형식에서 가비지 수집기가 해제 하는 방법을 알지 못하는 리소스를 사용할 수 있습니다. 이러한 리소스를 *관리 되지 않는* 리소스 (예: 네이티브 파일 핸들) 라고 합니다. 종료자에서 관리 되지 않는 리소스를 모두 해제 하는 것이 좋습니다. 가비지 수집기는 관리 되는 리소스를 명확 하 게 해제 하므로 종료자에서 관리 되는 리소스를 참조 하는 것은 안전 하지 않습니다. 가비지 수집기가 이미 정리 되었기 때문일 수 있습니다.

Visual C++ 종료자는 메서드와 동일 하지 않습니다 <xref:System.Object.Finalize%2A> . CLR 문서는 종료자와 <xref:System.Object.Finalize%2A> 메서드를 같은 뜻으로 사용합니다. <xref:System.Object.Finalize%2A> 메서드는 클래스 상속 체인의 각 종료자를 호출하는 가비지 수집기에 의해 호출됩니다. Visual C++ 소멸자와는 달리 파생 클래스 종료자 호출로 인해 컴파일러가 모든 기본 클래스의 종료자를 호출 하지는 않습니다.

Microsoft c + + 컴파일러는 리소스의 결정적 릴리스를 지원 하므로 또는 메서드를 구현 하지 마십시오 <xref:System.IDisposable.Dispose%2A> <xref:System.Object.Finalize%2A> . 그러나 이러한 메서드에 익숙한 경우 Visual C++ 종료자 및 소멸자가 <xref:System.IDisposable.Dispose%2A> 패턴에 매핑하도록 종료자를 호출하는 방법은 다음과 같습니다.

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

관리 되는 형식은 명확 하 게 해제 하려는 관리 되는 리소스를 사용할 수도 있습니다. 개체가 더 이상 필요 하지 않은 경우에는 가비지 수집기가 특정 시점에서 명확 하지 않은 개체를 해제 하는 것을 원하지 않을 수 있습니다. 리소스의 명확한 해제는 성능을 현저하게 개선할 수 있습니다.

Microsoft c + + 컴파일러에서는 소멸자를 정의 하 여 개체를 명확 하 게 정리할 수 있습니다. 소멸자를 사용하여 명확하게 해제하려는 리소스를 모두 해제하십시오.  종료자가 존재하는 경우 코드의 중복을 피하기 위해 소멸자에서 호출하십시오.

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

형식을 사용 하는 코드가 소멸자를 호출 하지 않는 경우 가비지 수집기는 결국 모든 관리 되는 리소스를 해제 합니다.

소멸자가 있는 경우에는 종료 자가 있음을 의미 하지 않습니다. 그러나 종료자의 존재는 소멸자를 정의해야 하고 해당 소멸자에서 종료자를 호출해야 함을 의미합니다. 이 호출은 관리 되지 않는 리소스의 결정적 릴리스를 제공 합니다.

<xref:System.GC.SuppressFinalize%2A>를 통해 소멸자를 호출하여 개체의 종료를 막습니다. 소멸자가 호출 되지 않은 경우에는 가비지 수집기에서 형식의 종료자를 호출 합니다.

CLR에서 개체를 명확 하 게 마무리 하는 대신 소멸자를 호출 하 여 개체의 리소스를 명확 하 게 정리 하는 방식으로 성능을 향상 시킬 수 있습니다.

Visual C++ 작성 되 고를 사용 하 여 컴파일된 코드는 **`/clr`** 다음과 같은 경우 형식의 소멸자를 실행 합니다.

- 스택 의미 체계를 사용하여 만들어진 개체가 범위를 벗어난 경우. 자세한 내용은 [참조 형식에 대 한 c + + 스택 의미 체계](../dotnet/cpp-stack-semantics-for-reference-types.md)를 참조 하세요.

- 개체의 생성 중에 예외가 발생한 경우

- 개체가 소멸자를 실행 중인 개체의 멤버인 경우

- 핸들에 대해 [delete](../cpp/delete-operator-cpp.md) 연산자를 호출 합니다 ([개체 연산자 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- 명시적으로 소멸자를 호출한 경우

다른 언어로 작성 된 클라이언트에서 형식을 사용 하는 경우 다음과 같이 소멸자가 호출 됩니다.

- <xref:System.IDisposable.Dispose%2A>에 대한 호출인 경우

- 형식의 `Dispose(void)`에 대한 호출인 경우

- 형식이 c # 문의 범위를 벗어나면이 고, **`using`**

참조 형식에 대 한 스택 의미 체계를 사용 하지 않고 관리 되는 힙에서 참조 형식의 개체를 만드는 경우 [try-finally](../cpp/try-finally-statement.md) 구문을 사용 하 여 예외가 소멸자 실행을 방해 하지 않도록 합니다.

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

형식에 소멸자가 있는 경우 컴파일러는 `Dispose`을 구현하는 <xref:System.IDisposable> 메서드를 생성합니다. Visual C++로 작성되고 다른 언어에서 사용된 소멸자가 있는 형식의 경우 해당 형식에서 `IDisposable::Dispose`를 호출하면 해당 형식의 소멸자가 호출됩니다. 형식이 Visual C++ 클라이언트에서 사용 되는 경우를 직접 호출할 수 없습니다. `Dispose` 대신 연산자를 사용 하 여 소멸자를 호출 **`delete`** 합니다.

형식에 종료자가 있는 경우 컴파일러는 `Finalize(void)`를 재정의하는 <xref:System.Object.Finalize%2A> 메서드를 생성합니다.

형식에 종료자 또는 소멸자가 있는 경우 컴파일러는 디자인 패턴에 따라 `Dispose(bool)` 메서드를 생성합니다. 자세한 내용은 [Dispose 패턴](/dotnet/standard/design-guidelines/dispose-pattern)을 참조 하세요. Visual C++에서 명시적으로 작성 하거나 호출할 수 없습니다 `Dispose(bool)` .

형식에 디자인 패턴을 따르는 기본 클래스가 있는 경우 파생 클래스의 소멸자가 호출될 때 모든 기본 클래스의 소멸자가 호출됩니다. (형식이 Visual C++로 작성 된 경우 컴파일러는 형식이이 패턴을 구현 하도록 합니다.) 즉, 참조 클래스의 소멸자는 c + + 표준에 지정 된 대로 해당 기본 및 멤버에 연결 됩니다. 먼저 클래스의 소멸자가 실행 됩니다. 그런 다음 해당 멤버에 대 한 소멸자는 생성 된 순서와 반대로 실행 됩니다. 마지막으로, 기본 클래스에 대 한 소멸자는 생성 된 순서와 반대로 실행 됩니다.

소멸자 및 종료자는 값 형식 또는 인터페이스 내에서 허용 되지 않습니다.

종료자는 참조 형식에서만 정의되거나 선언될 수 있습니다. 생성자와 소멸자와 같이 종료자는 반환 형식이 없습니다.

개체의 종료자가 실행된 후 기본 클래스의 종료자도 최소 파생된 형식으로 시작하여 호출됩니다. 데이터 멤버에 대 한 종료자는 클래스의 종료자에 의해 자동으로 연결 되지 않습니다.

종료 자가 관리 되는 형식에서 네이티브 포인터를 삭제 하는 경우 네이티브 포인터를 통해 또는에 대 한 참조가 중간에 수집 되지 않도록 해야 합니다. 를 사용 하는 대신 관리 되는 형식에서 소멸자를 호출 <xref:System.GC.KeepAlive%2A> 합니다.

컴파일 타임에서 형식에 종료자 또는 소멸자가 있는지 확인할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 관리 되지 않는 리소스가 있는 형식과 명확 하 게 릴리스되는 관리 되는 리소스가 있는 두 가지 형식을 보여 줍니다.

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)
