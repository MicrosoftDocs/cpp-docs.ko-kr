---
title: literal(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: 2687352c02bed609ffaa60ee8b1df40b51126d21
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686732"
---
# <a name="literal-ccli-and-ccx"></a>literal(C++/CLI 및 C++/CX)

**/clr** 컴파일에서 **literal**로 표시된 변수(데이터 멤버)는 **static const** 변수의 네이티브와 동일합니다.

## <a name="all-platforms"></a>모든 플랫폼

### <a name="remarks"></a>설명

(이 언어 기능에는 모든 런타임에 적용되는 설명이 없습니다.)

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

(이 언어 기능에는 Windows 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

## <a name="remarks"></a>설명

**literal**로 표시된 데이터 멤버는 선언할 때 초기화해야 하며, 값이 상수 정수, 열거형 또는 문자열 형식이어야 합니다. 초기화 식의 형식에서 정적 const 데이터 멤버의 형식으로 변환하는 데 사용자 정의 변환이 필요 없어야 합니다.

메모리는 런타임에 리터럴 필드에 대해 할당되지 않습니다. 컴파일러는 클래스에 대한 메타데이터에 해당 값을 삽입하기만 합니다.

**static const**로 표시된 변수는 메타데이터를 통해 다른 컴파일러에서 사용할 수 없습니다.

자세한 내용은 [Static](../cpp/storage-classes-cpp.md) 및 [const](../cpp/const-cpp.md)를 참조하세요.

**literal**은 상황에 맞는 키워드입니다. 자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요.

## <a name="examples"></a>예제

이 예에서는 **리터럴** 변수가를 의미 **`static`** 합니다.

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

다음 샘플에서는 메타데이터에서 리터럴의 영향을 보여 줍니다.

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

`sc` 및 `lit`에 대한 메타데이터에서의 차이점을 확인할 수 있습니다. `modopt` 지시문은 `sc`에 적용되어, 다른 컴파일러에서 무시될 수 있습니다.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

C#으로 작성된 다음 샘플은 이전 샘플에서 만든 메타데이터를 참조하고 **literal** 및 **static const** 변수의 영향을 보여 줍니다.

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

## <a name="see-also"></a>추가 정보

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
