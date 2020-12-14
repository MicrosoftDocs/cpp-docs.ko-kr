---
description: '자세한 정보: 컴파일러 오류 C2440'
title: 컴파일러 오류 C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 918f071f7d7ecc294ddab92764c03da98ad86555
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189745"
---
# <a name="compiler-error-c2440"></a>컴파일러 오류 C2440

' conversion ': ' type1 '에서 ' type2 ' (으)로 변환할 수 없습니다.

컴파일러가에서로 캐스팅할 수 `type1` 없습니다 `type2` .

C2440은 **`char*`** `wchar_t*` 컴파일러 규칙 옵션 [/zc: strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 가 설정 된 경우 c + + 코드에서 문자열 리터럴을 사용 하 여 비 const (또는)를 초기화 하려고 하면 발생할 수 있습니다. C에서 문자열 리터럴의 형식은의 배열 **`char`** 이지만 c + +에서는의 배열입니다 `const char` .

## <a name="examples"></a>예제

이 샘플에서는 C2440을 생성 합니다.

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

멤버에 대 한 포인터를 void *로 변환 하려고 하는 경우에도 C2440이 발생할 수 있습니다. 다음 샘플에서는 C2440을 생성 합니다.

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

지정 된 앞에만 선언 되었지만 정의 되지 않은 형식에서 캐스팅 하려고 시도 하는 경우에도 C2440이 발생할 수 있습니다. 이 샘플에서는 C2440을 생성 합니다.

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

다음 샘플의 줄 15 및 16에 있는 C2440 오류는 메시지를 사용 하 여 정규화 됩니다 `Incompatible calling conventions for UDT return value` . *UDT* 는 클래스, 구조체 또는 공용 구조체와 같은 사용자 정의 형식입니다. 이러한 종류의 비호환 오류는 전방 선언의 반환 형식에 지정 된 UDT의 호출 규칙이 UDT의 실제 호출 규칙과 충돌 하 고 함수 포인터가 포함 될 때 발생 합니다.

이 예제에서는 먼저 구조체 및 구조체를 반환 하는 함수에 대 한 전방 선언이 있습니다. 컴파일러는 구조체에서 c + + 호출 규칙을 사용 한다고 가정 합니다. 다음은 기본적으로 C 호출 규칙을 사용 하는 구조체 정의입니다. 컴파일러가 전체 구조체 읽기를 완료할 때까지 구조체의 호출 규칙을 알지 못하기 때문에의 반환 형식에 있는 구조체에 대 한 호출 규칙도 `get_c2` c + +로 간주 됩니다.

구조체 뒤에 구조체를 반환 하는 또 다른 함수 선언이 오고 있지만이 시점에서 컴파일러는 구조체의 호출 규칙이 c + + 임을 인식 합니다. 마찬가지로 구조체를 반환 하는 함수 포인터는 구조체에서 c + + 호출 규칙을 사용 한다는 것을 컴파일러에서 인식할 수 있도록 구조체 정의 다음에 정의 됩니다.

호환 되지 않는 호출 규칙으로 인해 발생 하는 C2440을 해결 하려면 UDT 정의 뒤에 UDT를 반환 하는 함수를 선언 합니다.

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

C2440은 내부 포인터에 0을 할당 하는 경우에도 발생할 수 있습니다.

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

C2440은 사용자 정의 변환을 잘못 사용 하는 경우에도 발생할 수 있습니다. 예를 들어 변환 연산자가로 정의 된 경우 **`explicit`** 컴파일러는 암시적 변환에 사용할 수 없습니다. 사용자 정의 변환에 대 한 자세한 내용은 [사용자 정의 변환 (c + +/cli)](../../dotnet/user-defined-conversions-cpp-cli.md)을 참조 하세요. 이 샘플에서는 C2440을 생성 합니다.

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

C2440은 형식이 인 Visual C++ 배열의 인스턴스를 만들려고 하는 경우에도 발생할 수 있습니다 <xref:System.Array> .  자세한 내용은 [배열](../../extensions/arrays-cpp-component-extensions.md)을 참조하세요.  다음 샘플에서는 C2440을 생성 합니다.

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

C2440은 특성 기능의 변경 내용으로 인해 발생할 수도 있습니다.  다음 샘플에서는 C2440을 생성 합니다.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

**/Clr** 프로그래밍을 사용 하는 소스 코드가 컴파일되면 Microsoft c + + 컴파일러에서 더 이상 [const_cast 연산자](../../cpp/const-cast-operator.md) 를 사용할 수 없습니다.

이 C2440을 해결 하려면 올바른 cast 연산자를 사용 합니다. 자세한 내용은 [캐스팅 연산자](../../cpp/casting-operators.md)를 참조 하세요.

이 샘플에서는 C2440을 생성 합니다.

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

C2440은 Visual Studio 2015 업데이트 3의 컴파일러에 대 한 규칙 변경으로 인해 발생할 수 있습니다. 이전에는 컴파일러에서 작업에 대 한 템플릿 일치를 식별할 때 특정 고유 식을 동일한 형식으로 잘못 처리 **`static_cast`** 했습니다. 이제 컴파일러는 형식을 올바르게 구분 하 고 이전 동작에 의존 하는 코드는 **`static_cast`** 중단 됩니다. 이 문제를 해결 하려면 템플릿 매개 변수 형식과 일치 하도록 템플릿 인수를 변경 하거나 **`reinterpret_cast`** 또는 C 스타일 캐스트를 사용 합니다.

이 샘플에서는 C2440을 생성 합니다.

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 이상에서는 Visual Studio 2015에서 catch 되지 않은 이니셜라이저 목록을 사용 하 여 개체 생성과 관련 된 컴파일러 오류를 올바르게 발생 시키며 충돌 하거나 정의 되지 않은 런타임 동작이 발생할 수 있습니다. C + + 17 복사 목록 초기화에서 컴파일러는 오버 로드 확인을 위한 명시적인 생성자를 고려해 야 하지만 오버 로드가 실제로 선택 된 경우 오류를 발생 시켜야 합니다.

다음 예제는 visual studio 2015에서는 컴파일되지만 Visual Studio 2017에서는 컴파일되지 않습니다.

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

오류를 수정하려면 직접 초기화를 사용합니다.

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

### <a name="cv-qualifiers-in-class-construction"></a>클래스 생성의 cv 한정자

Visual Studio 2015에서는 컴파일러가 생성자 호출을 통해 클래스 개체를 생성할 때 cv 한정자를 잘못 무시하는 경우가 있습니다. 이로 인해 잠재적으로 크래시 또는 예기치 않은 런타임 동작이 발생할 수 있습니다. 다음 예제는 Visual Studio 2015에서 컴파일되지만 Visual Studio 2017 이상에서 컴파일러 오류를 발생 시킵니다.

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

오류를 수정하려면 operator int()를 생성자로 선언합니다.
