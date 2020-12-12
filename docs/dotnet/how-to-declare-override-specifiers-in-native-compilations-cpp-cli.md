---
description: '자세한 정보: 방법: 네이티브 컴파일에서 Override 지정자 선언 (c + +/CLI)'
title: '방법: Override 지정자 선언 (c + +/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 75e925e26dc62d87e40d56b05e3be6d2dbda3e4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246398"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>방법: 네이티브 컴파일에 override 지정자 선언(C++/CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)및 [override](../extensions/override-cpp-component-extensions.md) 는 **/zw** 또는 [/clr](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하지 않는 컴파일에서 사용할 수 있습니다.

> [!NOTE]
> ISO c + + 11 표준 언어에는 [재정의](../cpp/override-specifier.md) 식별자와 [최종](../cpp/final-specifier.md) 식별자가 있으며, 둘 다 `final` 네이티브 전용 **`sealed`** 으로 컴파일되는 코드에서 대신 Visual Studio 사용에서 지원 됩니다.

## <a name="example-sealed-is-valid"></a>예: sealed가 올바릅니다.

### <a name="description"></a>설명

다음 예제에서는 **`sealed`** 이 네이티브 컴파일에서 유효함을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example-override-is-valid"></a>예: override가 올바릅니다.

### <a name="description"></a>설명

다음 예제에서는 `override` 가 네이티브 컴파일에서 유효함을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example-abstract-is-valid"></a>예: abstract가 올바릅니다.

### <a name="description"></a>설명

이 예제에서는 **`abstract`** 가 네이티브 컴파일에서 유효함을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>참조

[Override 지정자](../extensions/override-specifiers-cpp-component-extensions.md)
