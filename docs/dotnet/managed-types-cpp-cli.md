---
description: '자세한 정보: 관리 되는 형식 (c + +/CLI)'
title: 관리되는 형식(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: ccf126152216cfddb9a78cb5abc608f23cc3ba80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344460"
---
# <a name="managed-types-ccli"></a>관리되는 형식(C++/CLI)

Visual C++를 사용 하면 공용 언어 런타임의 기능에 대 한 지원을 제공 하는 관리 되는 형식을 통해 .NET 기능에 액세스할 수 있으며 런타임의 장점과 제한 사항이 적용 됩니다.

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a> 관리 되는 형식 및 main 함수

를 사용 하 여 응용 프로그램을 작성할 때는 **`/clr`** **main ()** 함수의 인수를 관리 되는 형식으로 지정할 수 없습니다.

적절 한 서명의 예는 다음과 같습니다.

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a> C + + 네이티브 형식에 해당 하는 .NET Framework

다음 표에서는 **System** 네임 스페이스에 있는 미리 정의 된 형식의 별칭인 기본 제공 Visual C++ 형식에 대 한 키워드를 보여 줍니다.

|Visual C++ 형식|.NET Framework 형식|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** 및 **`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**, **`signed int`** , **`long`** 및 **`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** 및 **`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** 및 **`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** 및 **`long double`**|<xref:System.Double?displayProperty=nameWithType>|

컴파일러 옵션을 또는로 기본으로 하는 방법에 대 한 자세한 내용은을 **`signed char`** **`unsigned char`** 참조 하세요. [ `/J` 기본 **`char`** 형식은입니다 **`unsigned`**](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a> 네이티브 형식에 중첩 된 값 형식의 버전 문제

클라이언트 어셈블리를 빌드하는 데 사용 되는 서명 된 (강력한 이름) 어셈블리 구성 요소를 고려 합니다. 구성 요소에는 클라이언트에서 네이티브 공용 구조체, 클래스 또는 배열의 멤버에 대 한 형식으로 사용 되는 값 형식이 포함 되어 있습니다. 이후 버전의 구성 요소에서 값 형식의 크기 또는 레이아웃을 변경 하는 경우 클라이언트를 다시 컴파일해야 합니다.

[sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) ()를 사용 하 여 keyfile을 만듭니다 `sn -k mykey.snk` .

### <a name="example"></a>예제

다음 샘플은 구성 요소입니다.

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>예제

이 샘플은 클라이언트입니다.

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>출력

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>의견

그러나 nested_value_types의에 다른 멤버를 추가 하 `struct S` 고 (예: `double d;` ) 클라이언트를 다시 컴파일하지 않고 구성 요소를 다시 컴파일하면 결과가 처리 되지 않은 예외 (형식)로 표시 됩니다 <xref:System.IO.FileLoadException?displayProperty=fullName> .

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a> 방법: 같음 여부 테스트

다음 샘플에서는 Managed Extensions for C++를 사용 하는 같음 테스트는 핸들이 참조 하는 내용을 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

이 프로그램의 IL은 op_Equality에 대 한 호출을 사용 하 여 반환 값을 구현 하는 것을 보여 줍니다.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a> 방법: 어셈블리 호환성 문제 진단 및 해결

이 항목에서는 컴파일 시간에 참조 되는 어셈블리 버전이 런타임에 참조 되는 어셈블리의 버전과 일치 하지 않을 때 발생할 수 있는 작업 및 문제를 방지 하는 방법을 설명 합니다.

어셈블리를 컴파일할 때 다른 어셈블리는 구문을 사용 하 여 참조할 수 있습니다 `#using` . 컴파일하는 동안 컴파일러에서 이러한 어셈블리에 액세스 합니다. 이러한 어셈블리의 정보는 최적화 결정을 내리는 데 사용 됩니다.

그러나 참조 된 어셈블리를 변경 하 고 다시 컴파일하는 경우 해당 어셈블리에 종속 된 참조 어셈블리를 다시 컴파일하지 않으면 어셈블리가 여전히 호환 되지 않을 수 있습니다. 처음에 유효한 최적화 결정은 새 어셈블리 버전과 관련 하 여 정확 하지 않을 수 있습니다. 이러한 비 호환성으로 인해 다양 한 런타임 오류가 발생할 수 있습니다. 이러한 경우에 생성 되는 특정 예외는 없습니다. 런타임에 오류가 보고 되는 방식은 문제를 일으킨 코드 변경의 특성에 따라 다릅니다.

릴리스 버전의 제품에 대해 전체 응용 프로그램을 다시 작성 하는 경우에는 최종 프로덕션 코드에서 이러한 오류가 발생 해서는 안 됩니다. Public으로 릴리스된 어셈블리는 공식 버전 번호로 표시 되어야 합니다. 그러면 이러한 문제를 방지할 수 있습니다. 자세한 내용은 [어셈블리 버전 관리](/dotnet/framework/app-domains/assembly-versioning)를 참조하세요.

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>비호환 오류 진단 및 해결

1. 다른 어셈블리를 참조 하는 코드에서 발생 하는 런타임 예외 또는 기타 오류 조건이 발생 하 고 다른 확인 된 원인이 없는 경우 오래 된 어셈블리를 처리할 수 있습니다.

1. 먼저 예외 또는 다른 오류 조건을 격리 하 고 재현 합니다. 오래 된 예외로 인해 발생 하는 문제를 재현할 수 있어야 합니다.

1. 응용 프로그램에서 참조 되는 모든 어셈블리의 타임 스탬프를 확인 합니다.

1. 참조 된 어셈블리의 타임 스탬프가 응용 프로그램의 마지막 컴파일의 타임 스탬프 보다 이후 이면 응용 프로그램이 만료 된 것입니다. 이 경우 최신 어셈블리를 사용 하 여 응용 프로그램을 다시 컴파일하고 코드를 변경 해야 합니다.

1. 응용 프로그램을 다시 실행 하 고, 문제를 재현 하는 단계를 수행 하 고, 예외가 발생 하지 않았는지 확인 합니다.

### <a name="example"></a>예제

다음 프로그램은 메서드의 액세스 가능성을 줄이고 다시 컴파일하지 않고 다른 어셈블리에서 해당 메서드에 액세스 하려고 시도 하 여 발생 하는 문제를 보여 줍니다. 먼저 컴파일을 시도 `changeaccess.cpp` 합니다. 이는 변경 되는 참조 어셈블리입니다. 그런 다음 컴파일합니다 `referencing.cpp` . 컴파일이 성공 합니다. 이제 호출 된 메서드의 액세스 가능성을 줄입니다. `changeaccess.cpp`플래그를 사용 하 여 다시 컴파일하십시오 `/DCHANGE_ACCESS` . 이렇게 하면 메서드가 private이 아닌 보호 되므로 합법적으로 호출할 수 없습니다. 다시 컴파일하지 않고 `referencing.exe` 응용 프로그램을 다시 실행 합니다. 예외가 발생 <xref:System.MethodAccessException> 합니다.

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[다른 .NET 언어와의 상호 운용성(C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[관리되는 형식(C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using 지시문](../preprocessor/hash-using-directive-cpp.md)
