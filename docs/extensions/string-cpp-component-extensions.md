---
description: '자세한 정보: 문자열 (c + +/CLI 및 c + +/CX)'
title: String(C++/CLI 및 C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: a47842713d1e7349717eaaeddcd4f3cba86fbbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206333"
---
# <a name="string--ccli-and-ccx"></a>String(C++/CLI 및 C++/CX)

Windows 런타임 및 공용 언어 런타임은 할당된 메모리가 자동으로 관리되는 개체로 문자열을 나타냅니다. 즉, 문자열 변수가 범위를 벗어나거나 애플리케이션이 종료될 때 문자열에 대한 메모리를 명시적으로 버릴 필요가 없습니다. 문자열 개체의 수명이 자동으로 관리됨을 나타내려면 [개체 핸들(^)](handle-to-object-operator-hat-cpp-component-extensions.md) 한정자를 사용하여 문자열 형식을 선언합니다.

## <a name="windows-runtime"></a>Windows 런타임

Windows 런타임 아키텍처에서는 `String` 데이터 형식이 `Platform` 네임스페이스에 있어야 합니다. 편의를 위해, Visual C++에서는 `Platform::String`의 동의어인 `string` 데이터 형식도 `default` 네임스페이스에 제공합니다.

### <a name="syntax"></a>Syntax

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

`/clr`로 컴파일하는 경우, 컴파일러에서 문자열 리터럴을 <xref:System.String> 형식의 문자열로 변환합니다. 기존 코드에서 이전 버전과의 호환성을 유지하기 위해 다음 두 가지 예외가 있습니다.

- 예외 처리. 문자열 리터럴이 throw되면 컴파일러에서 문자열 리터럴로 catch합니다.

- 템플릿 추론. 템플릿 인수로 문자열 리터럴이 전달되면 컴파일러에서 <xref:System.String>으로 변환하지 않습니다. 제네릭 인수로 전달된 문자열 리터럴의 수준이 <xref:System.String>으로 올라갑니다.

컴파일러는 동작의 사용자 지정을 위해 재정의할 수 있는 다음 세 개의 연산자도 기본적으로 지원합니다.

- System::String^ operator +( System::String, System::String);

- System::String^ operator +( System::Object, System::String);

- System::String^ operator +( System::String, System::Object);

<xref:System.String>이 전달되면, 컴파일러에서 필요한 경우 개체(ToString 포함)를 boxing하고 문자열과 연결합니다.

> [!NOTE]
> 캐럿(“^”)은 선언된 변수가 C++/CLI 관리형 개체에 대한 핸들임을 나타냅니다.

자세한 내용은 [문자열 및 문자 리터럴](../cpp/string-and-character-literals-cpp.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: **/clr**

### <a name="examples"></a>예제

다음 코드 예제에서는 문자열을 연결하고 비교하는 방법을 보여 줍니다.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

다음 샘플에서는 컴파일러 제공 연산자를 오버로드할 수 있으며, 컴파일러에서 <xref:System.String> 형식을 기준으로 함수 오버로드를 찾게 됨을 보여 줍니다.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

다음 샘플에서는 컴파일러에서 네이티브 문자열과 <xref:System.String> 문자열을 구분함을 보여 줍니다.

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)<br/>
[문자열 및 문자 리터럴](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr(공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)
