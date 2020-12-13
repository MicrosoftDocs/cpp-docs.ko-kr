---
description: '자세히 알아보기: sealed (c + +/CLI 및 c + +/CX)'
title: sealed(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: a1ec201f9b03d1f2cf4d11eb71ba166f48bc6cea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341050"
---
# <a name="sealed--ccli-and-ccx"></a>sealed(C++/CLI 및 C++/CX)

**sealed** 는 가상 멤버를 재정의할 수 없거나 형식을 기본 형식으로 사용할 수 없음을 나타내는 ref 클래스에 대한 상황에 맞는 키워드입니다.

> [!NOTE]
> ISO C++ 11 표준 언어에서는 [final](../cpp/final-specifier.md) 키워드가 도입되었습니다. 표준 클래스에서는 **final** 을 사용하고 ref 클래스에서는 **sealed** 를 사용합니다.

## <a name="all-runtimes"></a>모든 런타임

## <a name="syntax"></a>구문

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>매개 변수

*identifier*<br/>
함수나 클래스의 이름입니다.

*반환 형식*<br/>
함수에서 반환하는 형식입니다.

## <a name="remarks"></a>설명

첫 번째 구문 예에서는 클래스가 봉인되어 있고, 두 번째 예에서는 가상 함수가 봉인되어 있습니다.

ref 클래스 및 해당 가상 멤버 함수에 대해 **sealed** 키워드를 사용합니다. 자세한 내용은 [재정의 지정자 및 네이티브 컴파일](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)을 참조하세요.

컴파일 시간에 `__is_sealed(type)` 형식 특성을 사용하여 형식이 봉인되어 있는지 여부를 검색할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

**sealed** 는 상황에 맞는 키워드입니다.  자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

[Ref 클래스 및 구조체](../cppcx/ref-classes-and-structs-c-cx.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

(이 언어 기능에는 공용 언어 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 가상 멤버에 대한 **sealed** 의 영향을 보여 줍니다.

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

다음 코드 예제에서는 클래스를 sealed로 표시하는 방법을 보여 줍니다.

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
