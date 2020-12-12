---
description: '자세한 정보: 제네릭 및 템플릿 (c + +/CLI)'
title: 제네릭 및 템플릿(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: a62e765255896ef75d4cda73b66e7be0298b3690
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301687"
---
# <a name="generics-and-templates-ccli"></a>제네릭 및 템플릿(C++/CLI)

제네릭과 템플릿은 둘 다 매개 변수가 있는 형식을 지원하는 언어 기능입니다. 그러나 제네릭과 템플릿은 서로 다르며, 다른 용도로 사용됩니다. 이 항목에서는 여러 가지 차이점에 대해 간략하게 설명합니다.

자세한 내용은 [Windows 런타임 및 관리형 템플릿](windows-runtime-and-managed-templates-cpp-component-extensions.md)을 참조하세요.

## <a name="comparing-templates-and-generics"></a>템플릿과 제네릭 비교

제네릭과 C++ 템플릿의 주요 차이점은 다음과 같습니다.

- 제네릭은 런타임에 형식으로 대체될 때까지 제네릭입니다. 템플릿은 컴파일 시간에 특수화되므로 런타임에는 아직 매개 변수가 있는 형식이 아닙니다.

- 공용 언어 런타임은 특히 MSIL에서 제네릭을 지원합니다. 런타임에 제네릭을 인식하기 때문에 제네릭 형식이 포함된 어셈블리를 참조할 때 제네릭 형식을 특정 형식으로 대체할 수 있습니다. 반면, 템플릿은 컴파일 시간에 일반 형식으로 확인되므로 다른 어셈블리에서 결과 형식을 특수화할 수 없습니다.

- 동일한 형식 인수를 사용하는, 서로 다른 두 어셈블리에서 특수화된 제네릭은 같은 형식입니다. 동일한 형식 인수를 사용하는, 서로 다른 두 어셈블리에서 특수화된 템플릿은 런타임에 다른 형식으로 간주됩니다.

- 제네릭은 모든 참조 형식 인수에 사용되는 단일 실행 코드 조각으로 생성됩니다. 이와 달리, 값 형식의 경우 값 형식마다 고유한 구현이 있습니다. JIT 컴파일러는 제네릭을 인식하며, 형식 인수로 사용되는 참조 형식 또는 값 형식에 맞게 코드를 최적화할 수 있습니다. 템플릿은 특수화마다 별도의 런타임 코드를 생성합니다.

- 제네릭은 `template <int i> C {}` 같은 비형식 템플릿 매개 변수를 허용하지 않지만 템플릿은 허용합니다.

- 제네릭은 명시적 특수화, 즉 특정 형식에 대한 템플릿의 사용자 지정 구현을 허용하지 않지만 템플릿은 허용합니다.

- 제네릭은 부분 특수화, 즉 형식 인수의 하위 집합에 대한 사용자 지정 구현을 허용하지 않지만 템플릿은 허용합니다.

- 제네릭은 제네릭 형식의 기본 클래스로 형식 매개 변수를 허용하지 않지만 템플릿은 허용합니다.

- 템플릿은 템플릿-템플릿 매개 변수(예: `template<template<class T> class X> class MyClass`)를 지원하지만 제네릭은 지원하지 않습니다.

## <a name="combining-templates-and-generics"></a>템플릿과 제네릭 결합

제네릭의 기본적인 차이점은 템플릿과 제네릭을 결합하는 애플리케이션 빌드에 영향을 준다는 것입니다. 예를 들어 템플릿을 다른 언어에 제네릭으로 공개하기 위해 제네릭 래퍼를 만들려는 템플릿 클래스가 있다고 가정합니다. 템플릿은 컴파일 시간에 형식 매개 변수가 있어야 하지만 제네릭은 런타임 시까지 형식 매개 변수를 확인하지 않으므로, 제네릭이 형식 매개 변수를 받아서 템플릿에 전달하도록 할 수 없습니다. 런타임에 인스턴스화될 수 있는 임의의 제네릭 형식에 대해 템플릿을 컴파일 시간에 확장할 수 없기 때문에 제네릭 안에 템플릿을 중첩해도 효과가 없습니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 템플릿과 제네릭을 함께 사용하는 간단한 예제를 보여 줍니다. 이 예제에서 템플릿 클래스는 해당 매개 변수를 제네릭 형식에 전달합니다. 반대의 경우는 불가능합니다.

C++/CLI 어셈블리의 로컬 템플릿 코드를 사용하여 기존 제네릭 API에서 빌드하려는 경우 또는 제네릭에서 지원되지 않는 템플릿의 특정 기능을 이용하기 위해 제네릭 형식에 여분의 매개 변수화 레이어를 추가해야 하는 경우 이 관용구를 사용할 수 있습니다.

### <a name="code"></a>코드

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>참조

[제네릭](generics-cpp-component-extensions.md)
