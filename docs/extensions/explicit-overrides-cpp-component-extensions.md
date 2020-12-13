---
description: '자세한 정보: 명시적 재정의 (c + +/CLI 및 c + +/CX)'
title: 명시적 재정의(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: a24460f8135ff5379f14533dbaff83bde8918e4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330336"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>명시적 재정의(C++/CLI 및 C++/CX)

이 항목에서는 기본 클래스 또는 인터페이스의 멤버를 명시적으로 재정의하는 방법을 설명합니다. 명명된(명시적) 재정의는 다른 이름을 가진 파생 메서드로 메서드를 재정의하려는 경우에만 사용해야 합니다.

## <a name="all-runtimes"></a>모든 런타임

### <a name="syntax"></a>구문

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>매개 변수

*overriding-function-declarator*<br/>
재정의 함수의 반환 형식, 이름 및 인수 목록입니다.  재정의 함수가 재정의되는 함수와 같은 이름을 사용할 필요는 없습니다.

*type*<br/>
재정의할 함수가 포함된 기본 형식입니다.

*function*<br/>
재정의할 함수 이름이 쉼표로 구분되어 하나 이상 포함된 목록입니다.

*overriding-function-definition*<br/>
재정의 함수를 정의하는 함수 본문 문입니다.

### <a name="remarks"></a>설명

명시적 재정의를 사용 하 여 메서드 시그니처의 별칭을 만들거나 동일한 서명을 가진 메서드에 대해 다른 구현을 제공 합니다.

상속된 형식 및 상속된 형식 멤버의 동작을 수정하는 방법에 대한 자세한 내용은 [재정의 지정자](override-specifiers-cpp-component-extensions.md)를 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="remarks"></a>설명

네이티브 코드 또는 `/clr:oldSyntax`로 컴파일된 코드의 명시적 재정의에 대한 자세한 내용은 [명시적 재정의](../cpp/explicit-overrides-cpp.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 명시적 재정의를 사용하지 않는, 기본 인터페이스 멤버의 간단한 암시적 재정의 및 구현을 보여 줍니다.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

다음 코드 예제에서는 명시적 재정의 구문을 사용하여 모든 인터페이스 멤버를 공용 시그니처로 구현하는 방법을 보여 줍니다.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

다음 코드 예제에서는 함수 재정의가 구현하는 함수와 다른 이름을 사용할 수 있는 방법을 보여 줍니다.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

다음 코드 예제에서는 형식이 안전한 컬렉션을 구현하는 명시적 인터페이스 구현을 보여 줍니다.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
