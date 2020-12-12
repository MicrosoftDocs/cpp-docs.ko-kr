---
description: 자세한 내용은 User-Defined 특성 (c + +/CLI 및 c + +/CX)을 (를) 확인 하세요.
title: 사용자 정의 특성(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: 2fab2cc1317522b43cd4bddbb56ae174907607d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327901"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>사용자 정의 특성(C++/CLI 및 C++/CX)

C++/CLI 및 C++/CX를 사용하면 인터페이스, 클래스 또는 구조체, 메서드, 매개 변수 또는 열거형의 메타데이터를 확장하는 플랫폼별 특성을 만들 수 있습니다. 이러한 특성은 [표준 C++ 특성](../cpp/attributes.md)과 다릅니다.

## <a name="windows-runtime"></a>Windows 런타임

C++/CX 특성을 속성에 적용할 수 있지만 생성자 또는 메서드에는 적용할 수 없습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

이 항목에 제공된 정보와 구문은 [특성](../windows/attributes/attribute.md)에 제공된 정보를 대체합니다.

형식을 정의하고 <xref:System.Attribute>를 형식의 기본 클래스로 설정한 다음, 필요에 따라 <xref:System.AttributeUsageAttribute> 특성을 적용하여 사용자 지정 특성을 정의할 수 있습니다.

자세한 내용은 다음을 참조하세요.

- [특성 대상](attribute-targets-cpp-component-extensions.md)

- [특성 매개 변수 형식](attribute-parameter-types-cpp-component-extensions.md)

Visual C++에서 어셈블리에 서명하는 방법에 대한 자세한 내용은 [강력한 이름 어셈블리(어셈블리 서명)(C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 샘플에서는 사용자 지정 특성을 정의하는 방법을 보여 줍니다.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

다음 예제에서는 사용자 지정 특성의 몇 가지 중요한 기능을 보여 줍니다. 예를 들어 이 예제에서는 사용자 지정 특성의 일반적인 사용 예로, 클라이언트에 완벽한 자체 설명이 가능한 서버를 인스턴스화하는 방법을 보여 줍니다.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

`Object^` 형식이 variant 데이터 형식을 대체합니다. 다음 예제에서는 `Object^` 배열을 매개 변수로 사용하는 사용자 지정 특성을 정의합니다.

특성 인수는 컴파일 시간 상수여야 하며, 대부분의 경우 상수 리터럴이어야 합니다.

사용자 지정 특성 블록에서 System::Type 값을 반환하는 방법에 대한 자세한 내용은 [typeid](typeid-cpp-component-extensions.md)를 참조하세요.

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

런타임에 사용자 지정 특성 클래스의 공개 부분이 직렬화 가능해야 합니다.  사용자 지정 특성을 작성할 때 사용자 지정 특성의 명명된 인수는 컴파일 시간 상수로 제한됩니다.  메타데이터의 클래스 레이아웃에 추가되는 비트 시퀀스로 간주하면 됩니다.

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
