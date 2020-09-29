---
title: 컴파일러 오류 C3390
description: Microsoft c + + 컴파일러 오류 C3390, 해당 원인 및 해결 방법입니다.
ms.date: 09/26/2020
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 467b379d7f5a349a217b566dc55b28d5fbd789da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414362"
---
# <a name="compiler-error-c3390"></a>컴파일러 오류 C3390

> '*type_arg*': 제네릭 '*generic_type*'의 제네릭 매개 변수 '*param*'에 대 한 형식 인수가 잘못 되었습니다. 참조 형식 이어야 합니다.

제네릭 형식이 잘못 인스턴스화되었습니다. 형식 정의를 확인하세요.

## <a name="remarks"></a>설명

자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

첫 번째 샘플에서는 c #을 사용 하 여 제네릭 형식을 포함 하는 구성 요소를 만듭니다. 이 형식에는 c + +/CLI에서 제네릭 형식을 작성할 때 지원 되지 않는 특정 제약 조건이 있습니다. 자세한 내용은 [형식 매개 변수에 대한 제약 조건](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)을 참조하세요.

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

C3390.dll 구성 요소를 사용할 수 있는 경우 다음 샘플에서는 C3390를 생성 합니다.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK - do this instead
}
```
