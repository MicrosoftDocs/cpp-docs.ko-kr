---
title: literal (c + +/CLI)
description: Literal 키워드는 컴파일 시간 상수에 대 한 Microsoft c + +/CLI 상황에 맞는 키워드입니다.
ms.date: 10/20/2020
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.openlocfilehash: 2d71a535252ba51f89407670b474a34b407eaffc
ms.sourcegitcommit: 59b7c18703d1ffd66827db0e2eeece490d3d8789
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92337215"
---
# <a name="literal-ccli"></a>`literal` (C + +/CLI)

컴파일에서로 표시 된 변수 (데이터 멤버)는 **`literal`** **`/clr`** 컴파일 타임 상수입니다. C # 변수에 해당 하는 네이티브 항목입니다 [`const`](/dotnet/csharp/language-reference/keywords/const) .

## <a name="all-platforms"></a>모든 플랫폼

### <a name="remarks"></a>설명

(이 언어 기능에는 모든 런타임에 적용되는 설명이 없습니다.)

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

(이 언어 기능에는 Windows 런타임에만 적용되는 설명이 없습니다.)

## <a name="common-language-runtime"></a>공용 언어 런타임

## <a name="remarks"></a>설명

로 표시 된 데이터 멤버는 **`literal`** 선언 될 때 초기화 되어야 합니다. 및 값은 상수 정수 계열, 열거형 또는 문자열 형식 이어야 합니다. 초기화 식의 형식에서 데이터 멤버의 형식으로 변환 하려면 **`literal`** 사용자 정의 변환이 필요 하지 않습니다.

런타임에 필드에 대해 메모리가 할당 되지 않습니다. **`literal`** 컴파일러는 클래스에 대 한 메타 데이터에 해당 값을 삽입 합니다. **`literal`** 값은 컴파일 시간 상수로 취급 됩니다. 표준 c + +에서 가장 유사한 것은 **`constexpr`** 이지만 데이터 멤버는 **`constexpr`** c + +/cli 일 수 없습니다.

로 표시 된 변수가 표시 되는 변수와 **`literal`** 다릅니다 **`static const`** . **`static const`** 데이터 멤버는 다른 컴파일러에 대 한 메타 데이터에서 사용할 수 없습니다. 자세한 내용은 [`static`](../cpp/storage-classes-cpp.md) 및 [`const`](../cpp/const-cpp.md)을 참조하세요.

**`literal`** 는 상황에 맞는 키워드입니다. 자세한 내용은 상황에 맞는 [키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조 하세요.

## <a name="examples"></a>예

이 예에서는 변수가를 의미 함을 보여 줍니다 **`literal`** **`static`** .

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

다음 샘플에서는 메타 데이터의 효과를 보여 줍니다 **`literal`** .

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

`sc` 및 `lit`에 대한 메타데이터에서의 차이점을 확인할 수 있습니다. `modopt` 지시문은 `sc`에 적용되어, 다른 컴파일러에서 무시될 수 있습니다.

```MSIL
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x00000001)
```

```MSIL
.field public static literal int32 lit = int32(0x00000000)
```

C #으로 작성 된 다음 샘플은 이전 샘플에서 만든 메타 데이터를 참조 하 고 및 변수의 효과를 보여 줍니다 **`literal`** **`static const`** .

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
