---
title: 특성 매개 변수 형식(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
ms.openlocfilehash: cf33014c455bef145f7b7ec7ee353f27d1157f24
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008598"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>특성 매개 변수 형식(C++/CLI 및 C++/CX)

특성에 전달된 값은 컴파일 타임에 컴파일러에 알려야 합니다.  특성 매개 변수는 다음 형식일 수 있습니다.

- **`bool`**

- **`char`**, **`unsigned char`**

- **`short`**, **`unsigned short`**

- **`int`**, **`unsigned int`**

- **`long`**, **`unsigned long`**

- **`__int64`**, **unsigned __int64**

- **`float`**, **`double`**

- **`wchar_t`**

- **`char*`** 또는 `wchar_t*` 또는 `System::String*`

- `System::Type ^`

- `System::Object ^`

- **`enum`**

## <a name="example-attribute-parameter-types"></a>예: 특성 매개 변수 형식

### <a name="code"></a>코드

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example-unnamed-arguments-precede-named-arguments"></a>예: 명명 되지 않은 인수는 명명 된 인수 앞에 옵니다.

### <a name="description"></a>설명

특성을 지정할 때 명명되지 않은 모든 (위치) 인수는 모든 명명된 인수 앞에 와야 합니다.

### <a name="code"></a>코드

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example-one-dimensional-array-attribute-parameter"></a>예: 1 차원 배열 특성 매개 변수

### <a name="description"></a>설명

특성 매개 변수는 이전 형식의 1차원 배열일 수 있습니다.

### <a name="code"></a>코드

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>참조

[사용자 정의 특성](user-defined-attributes-cpp-component-extensions.md)
