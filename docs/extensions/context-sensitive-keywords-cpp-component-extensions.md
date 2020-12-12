---
description: 자세한 내용은 Context-Sensitive 키워드 (c + +/CLI 및 c + +/CX)를 확인 하세요.
title: 상황에 맞는 키워드(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: 7c005b1a6149f010b9729db5459fa3951bc50521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176862"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>상황에 맞는 키워드(C++/CLI 및 C++/CX)

*상황에 맞는 키워드* 는 특정 컨텍스트에서만 인식되는 언어 요소입니다. 특정 컨텍스트가 아닐 경우 상황에 맞는 키워드는 사용자 정의 기호일 수 있습니다.

## <a name="all-runtimes"></a>모든 런타임

### <a name="remarks"></a>설명

다음은 상황에 맞는 키워드의 목록입니다.

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [property](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where`([제네릭](generics-cpp-component-extensions.md)에 포함)

가독성을 위해 상황에 맞는 키워드를 사용자 정의 기호로만 사용하는 것이 좋습니다.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

(이 기능에는 플랫폼별 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="remarks"></a>설명

(이 기능에는 플랫폼별 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 적절 한 컨텍스트에서 상황에 맞는 키워드를 **`property`** 사용 하 여 속성 및 변수를 정의할 수 있음을 보여 줍니다.

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
