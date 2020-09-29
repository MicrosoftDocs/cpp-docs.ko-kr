---
title: typeid(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: bfb226bc11f0fd7d3feddfb2c50ffe1aa6311d3d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500378"
---
# <a name="typeid--ccli-and-ccx"></a>typeid(C++/CLI 및 C++/CX)

개체의 형식을 나타내는 값을 가져옵니다.

> [!NOTE]
> 이 항목은 TypeId의 C++ 구성 요소 확장명 버전을 참조합니다. 이 키워드의 ISO C++ 버전은 [typeid 연산자](../cpp/typeid-operator.md)를 참조하세요.

## <a name="all-runtimes"></a>모든 런타임

### <a name="syntax"></a>구문

```cpp
T::typeid
```

### <a name="parameters"></a>매개 변수

*T*<br/>
형식 이름.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="syntax"></a>구문

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
형식 이름.

### <a name="remarks"></a>설명

C++/CX에서 typeId는 런타임 형식 정보에서 생성된 [Platform::Type](../cppcx/platform-type-class.md)을 반환합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="syntax"></a>구문

```
type::typeid
```

### <a name="parameters"></a>매개 변수

*type*<br/>
`System::Type` 개체를 가져오려는 형식(추상 선언자)의 이름입니다.

### <a name="remarks"></a>설명

**`typeid`** 는 <xref:System.Type> 컴파일 시간에 형식에 대 한를 가져오는 데 사용 됩니다.

**`typeid`** 는 `System::Type` 런타임에 또는를 사용 하 여 형식에 대 한를 가져오는 것과 비슷합니다 <xref:System.Type.GetType%2A> <xref:System.Object.GetType%2A> . 그러나에서는 **`typeid`** 형식 이름만 매개 변수로 허용 합니다.  형식의 인스턴스를 사용 하 여 해당 `System::Type` 이름을 가져오려면를 사용 `GetType` 합니다.

**`typeid`** 는 컴파일 시간에 형식 이름 (형식)을 계산할 수 있어야 하는 반면 GetType은 런타임에 반환 될 형식을 평가 합니다.

**`typeid`** 네이티브 형식 이름에 대해 네이티브 형식 이름 또는 공용 언어 런타임 별칭을 사용할 수 있습니다. 자세한 내용은 [c + + 네이티브 형식에 해당 하는 .NET Framework (c + +/cli)를](../dotnet/managed-types-cpp-cli.md#dotnet) 참조 하세요.

**`typeid`** 는 여전히을 반환 하지만 네이티브 형식 에서도 작동 `System::Type` 합니다.  Type_info 구조체를 가져오려면 [ `typeid` Operator](../cpp/typeid-operator.md)를 사용 합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예

다음 예제에서는 typeid 키워드와 `GetType()` 멤버를 비교합니다.

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

다음 샘플에서는 System::Type 형식의 변수를 사용하여 형식의 특성을 가져올 수 있음을 보여 줍니다.  또한 일부 형식의 경우 사용할 typedef를 만들어야 함을 보여 줍니다 **`typeid`** .

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
