---
description: '자세히 알아보기: abstract (c + +/CLI 및 c + +/CX)'
title: abstract(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: e40d0d0c03bbf97b684d9e011f4bf614f6a44332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177122"
---
# <a name="abstract--ccli-and-ccx"></a>abstract(C++/CLI 및 C++/CX)

**abstract** 키워드는 다음 중 하나를 선언합니다.

- 형식은 기본 형식으로 사용될 수 있지만 형식 자체는 인스턴스화될 수 없습니다.

- 형식 멤버 함수는 파생된 형식에서만 정의될 수 있습니다.

## <a name="all-platforms"></a>모든 플랫폼

### <a name="syntax"></a>Syntax

*class-declaration* *class-identifier* **abstract {}**

**`virtual`***반환 형식* *멤버 함수-식별자* **() abstract;**

### <a name="remarks"></a>설명

첫 번째 예제 구문에서는 클래스를 추상으로 선언합니다. *클래스 선언* 구성 요소는 네이티브 c + + 선언 (* * * * 또는) 이거나 또는 컴파일러 옵션이 지정 된 경우 **`class` **`struct`** c + + 확장 선언 (** ref 클래스 * * 또는 **ref 구조체**) 일 수 있습니다 `/ZW` `/clr` .

두 번째 예제 구문에서는 가상 멤버 함수를 추상으로 선언합니다. 함수를 추상으로 선언하는 것은 함수를 순수 가상 함수로 선언하는 것과 같습니다. 멤버 함수를 추상으로 선언하면 바깥쪽 클래스가 추상으로 선언됩니다.

**abstract** 키워드는 네이티브 코드와 플랫폼별 코드에서 지원됩니다. 즉, `/ZW` 또는 `/clr` 컴파일러 옵션을 사용하거나 사용하지 않고 컴파일할 수 있습니다.

컴파일 시간에 `__is_abstract(type)` 형식 특성을 사용하여 형식이 추상인지 여부를 검색할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

**abstract** 키워드는 상황에 맞는 재정의 지정자입니다. 상황에 맞는 키워드에 대한 자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요. 재정의 지정자에 대 한 자세한 내용은 [방법: 네이티브 컴파일에 재정의 지정자 선언](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)을 참조 하세요.

## <a name="windows-runtime"></a>Windows 런타임

자세한 내용은 [Ref 클래스 및 구조체](../cppcx/ref-classes-and-structs-c-cx.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 `X` 클래스가 **abstract** 로 표시되었기 때문에 오류가 발생합니다.

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

다음 코드 예제에서는 **abstract** 로 표시된 네이티브 클래스를 인스턴스화하기 때문에 오류가 발생합니다. 이 오류는 `/clr` 컴파일러 옵션 사용 여부와 관계없이 발생합니다.

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

다음 코드 예제에서는 `f` 함수가 정의를 포함하지만 **abstract** 로 표시되었기 때문에 오류가 발생합니다. 예제의 마지막 문에서는 추상 가상 함수를 선언하는 것이 순수 가상 함수를 선언하는 것과 일치함을 보여 줍니다.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
