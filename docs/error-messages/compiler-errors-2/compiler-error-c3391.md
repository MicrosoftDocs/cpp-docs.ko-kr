---
description: '자세한 정보: 컴파일러 오류 C3391'
title: 컴파일러 오류 C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 1bac535136b2c6115bf0f5ff31c9e098407e03bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313400"
---
# <a name="compiler-error-c3391"></a>컴파일러 오류 C3391

' type_arg ': 제네릭 ' generic_type '의 제네릭 매개 변수 ' param '에 대 한 형식 인수가 null을 허용 하지 않는 값 형식 이어야 합니다.

제네릭 형식이 잘못 인스턴스화되었습니다. 형식 정의를 확인하세요. 자세한 내용은 <xref:System.Nullable> 및 [제네릭을](../../extensions/generics-cpp-component-extensions.md)참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 c #을 사용 하 여 c + +/CLI에서 제네릭 형식을 작성할 때 지원 되지 않는 특정 제약 조건이 있는 제네릭 형식이 포함 된 구성 요소를 만듭니다. 자세한 내용은 [형식 매개 변수에 대한 제약 조건](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)을 참조하세요.

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

C3391.dll 구성 요소를 사용할 수 있는 경우 다음 샘플에서는 C3391를 생성 합니다.

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```
