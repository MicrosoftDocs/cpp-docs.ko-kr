---
title: 컴파일러 오류 C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 72bdef1b3344b3d69ba0d014f92a85e9381de4b3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776719"
---
# <a name="compiler-error-c3392"></a>컴파일러 오류 C3392

'type_arg': 제네릭 'generic_type'의 제네릭 매개 변수 'param'에 대한 형식 인수가 잘못되었습니다. 매개 변수가 없는 public 생성자가 있어야 합니다.

제네릭 형식이 잘못 인스턴스화되었습니다. 형식 정의를 확인하세요. 자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)합니다.

## <a name="example"></a>예제

C +의 제네릭 형식을 제작 하는 경우 지원 되지 않는 특정 제약 조건이 있는 제네릭 형식을 포함 하는 구성 요소를 만들려면 다음 샘플에서는 C# + CLI입니다. 자세한 내용은 [형식 매개 변수에 대한 제약 조건](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)을 참조하세요.

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

C3392.dll 구성 요소를 사용할 수 있는 경우 다음 샘플에서는 C3392를 생성 합니다.

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```