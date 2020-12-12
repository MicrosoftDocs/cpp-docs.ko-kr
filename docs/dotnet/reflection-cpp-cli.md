---
description: '자세한 정보: 리플렉션 (c + +/CLI)'
title: 리플렉션(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: a3a9a33a239ec678279455ea41b7c60749cc0189
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245800"
---
# <a name="reflection-ccli"></a>리플렉션(C++/CLI)

리플렉션에서는 알려진 데이터 형식을 런타임에 검사할 수 있습니다. 리플렉션에서는 지정 된 어셈블리에서 데이터 형식의 열거를 허용 하 고 지정 된 클래스 또는 값 형식의 멤버를 검색할 수 있습니다. 이는 컴파일 타임에 형식을 알 수 있는지, 아니면 참조 했는지에 관계 없이 적용 됩니다. 이를 통해 개발 및 코드 관리 도구에 대 한 유용한 기능을 사용할 수 있습니다.

제공 된 어셈블리 이름은 강력한 이름 (어셈블리 버전, 문화권 및 서명 정보를 포함 하는 [Strong-Named 어셈블리 만들기 및 사용](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)참조)입니다. 또한 데이터 형식을 정의 하는 네임 스페이스의 이름은 기본 클래스의 이름과 함께 검색할 수 있습니다.

리플렉션 기능에 액세스 하는 가장 일반적인 방법은 메서드를 사용 하는 것입니다 <xref:System.Object.GetType%2A> . 이 메서드는에서 제공 하는 <xref:System.Object?displayProperty=nameWithType> 모든 가비지 수집 클래스에서 파생 됩니다.

> [!NOTE]
> **/Clr: pure** 또는 **/clr: safe** 컴파일러 옵션을 사용 하 여 .exe를 빌드하는 경우에만 Microsoft c + + 컴파일러를 사용 하 여 빌드한 .exe에서 리플렉션을 수행할 수 있습니다. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서 사용할 수 없습니다. 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md) 를 참조 하세요.

자세한 내용은 <xref:System.Reflection>을 참조하세요.

## <a name="example-gettype"></a>예: GetType

`GetType`메서드는 <xref:System.Type> 개체의 기반이 되는 경우의 형식을 설명 하는 클래스 개체에 대 한 포인터를 반환 합니다. ( **형식** 개체는 인스턴스별 정보를 포함 하지 않습니다.) 이러한 항목 중 하나는 형식의 전체 이름이 며 다음과 같이 표시 될 수 있습니다.

형식 이름에는 네임 스페이스를 포함 하 여 형식이 정의 된 전체 범위가 포함 되며, .NET 구문에 표시 되 고 범위 확인 연산자로 점이 포함 됩니다.

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>예: boxed 값 형식

값 형식은 함수에도 사용할 수 `GetType` 있지만 먼저 boxing 해야 합니다.

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100;
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>예: typeid

`GetType`메서드와 마찬가지로 [typeid](../extensions/typeid-cpp-component-extensions.md) 연산자는 **형식** 개체에 대 한 포인터를 반환 하므로이 코드는 형식 이름 **system.object** 를 나타냅니다. 형식 이름을 표시 하는 것이 리플렉션의 가장 기본적인 기능 이지만, 열거 형식에 대 한 유효한 값을 검사 하거나 검색 하는 것이 더 유용한 기술입니다. 이 작업은 각각 텍스트 형식의 열거형 값을 포함 하는 문자열의 배열을 반환 하는 static **Enum:: GetNames** 함수를 사용 하 여 수행할 수 있습니다.  다음 샘플에서는 **옵션** (CLR) 열거형의 값 열거형 값을 설명 하 고 루프에 표시 하는 문자열의 배열을 검색 합니다.

네 번째 옵션이 **옵션** 열거에 추가 된 경우이 코드는 열거를 별도의 어셈블리에 정의 하더라도 다시 컴파일하지 않고 새 옵션을 보고 합니다.

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'",
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>예: GetType 멤버 및 속성

`GetType`개체는 형식을 검사 하는 데 사용할 수 있는 여러 멤버와 속성을 지원 합니다. 이 코드는 다음 정보 중 일부를 검색 하 고 표시 합니다.

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral,
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>예제: 형식 열거

리플렉션을 사용 하 여 어셈블리 내의 형식 및 클래스 내의 멤버를 열거할 수도 있습니다. 이 기능을 설명 하려면 간단한 클래스를 정의 합니다.

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; }
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>예제: 어셈블리 검사

위의 코드가 vcpp_reflection_6.dll 라는 DLL로 컴파일되면 리플렉션을 사용 하 여이 어셈블리의 콘텐츠를 검사할 수 있습니다. 이 작업에는 정적 리플렉션 API 함수 f% 2A? displayProperty = nameWithType을 사용 하 여 어셈블리를 로드 해야 합니다. 이 함수는에서 모듈 및 형식에 대해 쿼리할 수 있는 **어셈블리** 개체의 주소를 반환 합니다.

리플렉션 시스템에서 어셈블리를 성공적으로 로드 한 후에는 함수를 사용 하 여 **형식** 개체의 배열을 검색 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> 합니다. 각 배열 요소는 다른 형식에 대 한 정보를 포함 하지만이 경우에는 하나의 클래스만 정의 됩니다. 루프를 사용 하 여이 배열의 각 **형식은** **Type:: getmembers** 함수를 사용 하 여 형식 멤버에 대해 쿼리 됩니다. 이 함수는 형식에서 멤버 함수, 데이터 멤버 또는 속성에 대 한 정보를 포함 하는 **MethodInfo** 개체의 배열을 반환 합니다.

메서드 목록에는 **TestClass** 에서 명시적으로 정의 된 함수와 **System:: Object** 클래스에서 암시적으로 상속 된 함수가 포함 됩니다. Visual C++ 구문 대신 .NET에서 설명 하는의 일부로 속성은 get/set 함수에서 액세스 하는 기본 데이터 멤버로 나타납니다. Get/set 함수는이 목록에 일반 메서드로 표시 됩니다. 리플렉션에서는 Microsoft c + + 컴파일러가 아니라 공용 언어 런타임을 통해 지원 됩니다.

이 코드를 사용 하 여 정의한 어셈블리를 검사 했지만이 코드를 사용 하 여 .NET 어셈블리를 검사할 수도 있습니다. 예를 들어 TestAssembly를 mscorlib로 변경 하면 mscorlib.dll에 정의 된 모든 유형과 메서드의 목록이 표시 됩니다.

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):",
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})",
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="how-to-implement-a-plug-in-component-architecture-using-reflection"></a><a name="implement"></a> 방법: 리플렉션을 사용 하 여 Plug-In 구성 요소 아키텍처 구현

다음 코드 예제에서는 간단한 "플러그 인" 아키텍처를 구현 하기 위해 리플렉션을 사용 하는 방법을 보여 줍니다. 첫 번째 목록은 응용 프로그램이 고 두 번째는 플러그 인입니다. 응용 프로그램은 명령줄 인수로 제공 된 플러그 인 DLL에 있는 폼 기반 클래스를 사용 하 여 자신을 채우는 다중 문서 양식입니다.

응용 프로그램은 메서드를 사용 하 여 제공 된 어셈블리를 로드 하려고 합니다 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> . 성공 하면 메서드를 사용 하 여 어셈블리 내의 형식을 열거 합니다 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> . 그런 다음 메서드를 사용 하 여 각 형식에 대해 호환성을 확인 <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> 합니다. 이 예제에서 제공 된 어셈블리에 있는 클래스는 <xref:System.Windows.Forms.Form> 플러그 인으로 한정 하기 위해 클래스에서 파생 되어야 합니다.

호환 되는 클래스는 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 를 인수로 사용 하 <xref:System.Type> 고 새 인스턴스에 대 한 포인터를 반환 하는 메서드를 사용 하 여 인스턴스화됩니다. 그러면 각 새 인스턴스가 폼에 연결 되 고 표시 됩니다.

<xref:System.Reflection.Assembly.Load%2A>메서드는 파일 확장명을 포함 하는 어셈블리 이름을 허용 하지 않습니다. 응용 프로그램의 main 함수는 제공 된 확장을 모두 지우므로, 다음 코드 예제는 어떤 경우에도 작동 합니다.

### <a name="example"></a>예제

다음 코드는 플러그 인을 허용 하는 응용 프로그램을 정의 합니다. 첫 번째 인수로 어셈블리 이름을 제공 해야 합니다. 이 어셈블리에는 public 파생 형식이 하나 이상 포함 되어야 합니다 <xref:System.Windows.Forms.Form> .

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>예제

다음 코드에서는에서 파생 된 세 개의 클래스를 정의 합니다 <xref:System.Windows.Forms.Form> . 결과 어셈블리 이름의 이름이 이전 목록의 실행 파일에 전달 되 면 컴파일 타임에 이러한 세 클래스가 모두 검색 되 고 인스턴스화됩니다 .이는 컴파일 타임에 호스팅 응용 프로그램에서 모두 알 수 없기 때문입니다.

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="how-to-enumerate-data-types-in-assemblies-using-reflection"></a><a name="enumerate"></a> 방법: 리플렉션을 사용 하 여 어셈블리에 데이터 형식 열거

다음 코드에서는를 사용 하 여 public 형식 및 멤버의 열거형을 보여 줍니다 <xref:System.Reflection> .

로컬 디렉터리 또는 GAC에서 어셈블리의 이름을 지정 하는 경우 아래 코드는 어셈블리를 열고 설명을 검색 하려고 합니다. 성공 하면 각 형식이 public 멤버와 함께 표시 됩니다.

<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>에서는 파일 확장명이 사용 되지 않습니다. 따라서 "mscorlib.dll"를 명령줄 인수로 사용 하면 실패 하 고 "mscorlib"를 사용 하면 .NET Framework 형식이 표시 됩니다. 어셈블리 이름을 제공 하지 않으면 코드에서 현재 어셈블리 (이 코드의 결과로 생성 되는 EXE) 내의 형식을 검색 하 여 보고 합니다.

### <a name="example"></a>예제

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>참고 항목

- [C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
