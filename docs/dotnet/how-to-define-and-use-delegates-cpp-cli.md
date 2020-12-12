---
description: '자세히 알아보기: 방법: 대리자 정의 및 사용 (c + +/CLI)'
title: '방법: 대리자 정의 및 사용(C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: 4229af2015db3a9a77722e9e4cc24b80aa05a49b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175757"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>방법: 대리자 정의 및 사용(C++/CLI)

이 문서에서는 c + +/CLI에서 대리자를 정의 하 고 사용 하는 방법을 보여 줍니다.

.NET Framework는 여러 대리자를 제공 하지만 경우에 따라 새 대리자를 정의 해야 할 수도 있습니다.

다음 코드 예제에서는 라는 대리자를 정의 합니다 `MyCallback` . 이 새 대리자가 실행 될 때 호출 되는 이벤트 처리 코드는의 반환 형식을 가져야 **`void`** 하 고 참조를 사용 해야 합니다 <xref:System.String> .

Main 함수는로 정의 된 정적 메서드를 사용 하 여 `SomeClass` 대리자를 인스턴스화합니다 `MyCallback` . 그러면 대리자는 대리자 개체에 "single" 문자열을 전송 하 여 보여 주는 것 처럼이 함수를 호출 하는 대체 메서드가 됩니다. 다음으로의 추가 인스턴스 `MyCallback` 는 함께 연결 된 다음 대리자 개체에 대 한 호출을 통해 실행 됩니다.

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

다음 코드 샘플에서는 대리자를 값 클래스의 멤버와 연결 하는 방법을 보여 줍니다.

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>대리자를 구성 하는 방법

"" 연산자를 사용 `-` 하 여 구성 된 대리자에서 구성 요소 대리자를 제거할 수 있습니다.

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**출력**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>함수 포인터가 필요한 네이티브 함수에 대리자 ^ 전달

관리 되는 구성 요소에서 네이티브 함수가 관리 되는 구성 요소의 대리자의 멤버 함수를 호출할 수 있는 함수 포인터 매개 변수를 사용 하 여 네이티브 함수를 호출할 수 있습니다.

이 샘플에서는 네이티브 함수를 내보내는 .dll을 만듭니다.

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

다음 샘플에서는 .dll을 사용 하 고 함수 포인터가 필요한 네이티브 함수에 대리자 핸들을 전달 합니다.

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**출력**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>대리자를 관리 되지 않는 함수와 연결 하려면

대리자를 네이티브 함수와 연결 하려면 네이티브 함수를 관리 되는 형식으로 래핑하고를 통해 호출할 함수를 선언 해야 합니다 `PInvoke` .

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**출력**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>바인딩되지 않은 대리자를 사용 하려면

바인딩되지 않은 대리자를 사용 하 여 대리자가 호출 될 때 호출 하려는 함수를 포함 하는 형식의 인스턴스를 전달할 수 있습니다.

바인딩되지 않은 대리자는 [for each](../dotnet/for-each-in.md) (키워드)를 사용 하 여 컬렉션의 개체를 반복 하 고 각 인스턴스에서 멤버 함수를 호출 하는 경우에 특히 유용 합니다.

다음은 bound 및 바인딩되지 않은 대리자를 선언, 인스턴스화 및 호출 하는 방법입니다.

|작업|바인딩된 대리자|바인딩되지 않은 대리자|
|------------|---------------------|-----------------------|
|Declare|대리자 시그니처는 대리자를 통해 호출 하려는 함수의 시그니처와 일치 해야 합니다.|대리자 시그니처의 첫 번째 매개 변수는 호출 하려는 개체의 형식입니다 **`this`** .<br /><br /> 첫 번째 매개 변수 다음에 대리자 시그니처는 대리자를 통해 호출 하려는 함수의 시그니처와 일치 해야 합니다.|
|인스턴스화하지|바인딩된 대리자를 인스턴스화할 때 인스턴스 함수 또는 전역 또는 정적 멤버 함수를 지정할 수 있습니다.<br /><br /> 인스턴스 함수를 지정 하기 위해 첫 번째 매개 변수는 호출 하려는 멤버 함수를 포함 하는 형식의 인스턴스이고 두 번째 매개 변수는 호출 하려는 함수의 주소입니다.<br /><br /> 전역 또는 정적 멤버 함수를 호출 하려면 전역 함수의 이름이 나 정적 멤버 함수의 이름을 전달 하면 됩니다.|바인딩되지 않은 대리자를 인스턴스화하면 호출할 함수의 주소를 전달 하기만 하면 됩니다.|
|호출|바인딩된 대리자를 호출 하는 경우 대리자 시그니처에 필요한 매개 변수만 전달 하면 됩니다.|바인딩된 대리자와 동일 하지만 첫 번째 매개 변수는 호출 하려는 함수를 포함 하는 개체의 인스턴스여야 합니다.|

이 샘플에서는 바인딩되지 않은 대리자를 선언, 인스턴스화 및 호출 하는 방법을 보여 줍니다.

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**출력**

```Output
2
3
2
3
2
7
8
7
8
7
```

다음 샘플에서는 바인딩되지 않은 대리자와 [for each를](../dotnet/for-each-in.md) 사용 하 여 컬렉션의 개체를 반복 하 고 각 인스턴스에서 멤버 함수를 호출 하는 방법을 보여 줍니다.

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

이 샘플에서는 속성의 접근자 함수에 대해 바인딩되지 않은 대리자를 만듭니다.

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**출력**

```Output
11
```

다음 샘플에서는 하나의 인스턴스가 바인딩되고 한 인스턴스가 바인딩되지 않는 멀티 캐스트 대리자를 호출 하는 방법을 보여 줍니다.

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**출력**

```Output
in f(R ^ r)
in f()
```

다음 샘플에서는 바인딩되지 않은 제네릭 대리자를 만들고 호출 하는 방법을 보여 줍니다.

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**출력**

```Output
12
14
```

## <a name="see-also"></a>참고 항목

[delegate(C++ 구성 요소 확장)](../extensions/delegate-cpp-component-extensions.md)
