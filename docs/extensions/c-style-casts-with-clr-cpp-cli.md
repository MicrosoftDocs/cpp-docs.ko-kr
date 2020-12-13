---
description: 자세히 알아보기:/clr을 사용한 C 스타일 캐스트 (c + +/CLI)
title: -clr을 사용한 C 스타일 캐스트(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: aedd794ca0f305f0cc292fb9048bd8dcceace7d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176992"
---
# <a name="c-style-casts-with-clr-ccli"></a>/clr을 사용한 C 스타일 캐스트(C++/CLI)

다음 항목은 공용 언어 런타임에만 적용됩니다.

CLR 형식에서 사용할 경우, 컴파일러는 C 스타일 캐스트를 아래에 나열된 캐스트 중 하나에 순서대로 매핑하려고 합니다.

1. const_cast

2. safe_cast

3. safe_cast 및 const_cast

4. static_cast

5. static_cast 및 const_cast

위에 나열된 캐스트가 모두 유효하지 않고 식의 형식과 대상 유형이 CLR 참조 형식이면, C 스타일 캐스트는 런타임 검사(castclass MSIL 명령)에 매핑됩니다. 매핑되지 않으면 C 스타일 캐스트가 잘못된 것으로 간주되어, 컴파일러에서 오류가 발생합니다.

## <a name="remarks"></a>설명

C 스타일 캐스트는 권장되지 않습니다. [/clr(공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)로 컴파일하는 경우 [safe_cast](safe-cast-cpp-component-extensions.md)를 사용합니다.

다음 샘플에서는에 매핑되는 C 스타일 캐스트를 보여 줍니다 **`const_cast`** .

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

다음 샘플에서는 **safe_cast** 에 매핑되는 C 스타일 캐스트를 보여 줍니다.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

다음 샘플에서는 **safe_cast** 더하기에 매핑되는 C 스타일 캐스트를 보여 줍니다 **`const_cast`** .

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

다음 샘플에서는에 매핑되는 C 스타일 캐스트를 보여 줍니다 **`static_cast`** .

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

다음 샘플에서는 더하기에 매핑되는 C 스타일 캐스트를 보여 줍니다 **`static_cast`** **`const_cast`** .

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

다음 샘플에서는 런타임 검사에 매핑되는 C 스타일 캐스트를 보여 줍니다.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

다음 샘플에서는 컴파일러에서 오류가 발생하는 잘못된 C 스타일 캐스트를 보여 줍니다.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
