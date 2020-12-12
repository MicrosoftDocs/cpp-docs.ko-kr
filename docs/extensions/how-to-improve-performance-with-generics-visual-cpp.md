---
description: '자세히 알아보기: 방법: 제네릭을 사용 하 여 성능 향상 (c + +/CLI)'
title: '방법: 제네릭을 사용하여 성능 개선(C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 90066a64deda574dae895023cf92ac7fa2807603
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119163"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>방법: 제네릭을 사용하여 성능 개선(C++/CLI)

제네릭을 사용하여 형식 매개 변수를 기반으로 재사용 가능한 코드를 만들 수 있습니다. 형식 매개 변수의 실제 형식은 클라이언트 코드에서 호출할 때까지 지연됩니다. 제네릭에 대한 자세한 내용은 [Generics](generics-cpp-component-extensions.md)을 참조하세요.

이 문서에서는 제네릭으로 컬렉션을 사용하는 애플리케이션의 성능을 향상시키는 방법을 설명합니다.

## <a name="example-two-main-drawbacks-of-net-framework-collections"></a>예: .NET Framework 컬렉션의 두 가지 주요 단점

.NET Framework에는 <xref:System.Collections?displayProperty=fullName> 네임스페이스의 여러 컬렉션 클래스가 제공됩니다. 이러한 컬렉션의 대부분은 <xref:System.Object?displayProperty=fullName> 형식의 개체에서 동작합니다. 그러면 값 형식까지 포함한 .NET Framework의 모든 형식이 <xref:System.Object?displayProperty=fullName>에서 파생되기 때문에 컬렉션에서 모든 형식을 저장할 수 있습니다. 그러나 이 방법에는 두 가지 단점이 있습니다.

우선, 컬렉션에서 정수와 같은 값 형식을 저장하는 경우 해당 값은 컬렉션에 추가되기 전에 boxing되어야 하며 해당 값을 컬렉션에서 검색할 때 unboxing되어야 합니다. 이는 부담이 큰 작업입니다.

둘째, 컬렉션에 추가할 수 있는 형식을 제어할 방법이 없습니다. 의도가 아닐지라도 동일한 컬렉션에 정수 및 문자열을 추가하는 데는 문제가 전혀 없습니다. 따라서 코드의 형식이 안전하려면 컬렉션에서 검색된 형식이 실제로 필요한 것인지 확인해야 합니다.

다음 코드 예제에서는 제네릭 전 .NET Framework 컬렉션의 두 가지 주요 단점을 보여 줍니다.

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example-benefit-of-using-generic-collection"></a>예: 제네릭 컬렉션 사용의 장점

새 <xref:System.Collections.Generic?displayProperty=fullName> 네임스페이스는 <xref:System.Collections?displayProperty=fullName> 네임스페이스에서 찾을 수 있는 여러 개의 동일한 컬렉션을 포함하고 있지만, 제네릭 형식 매개 변수를 받기 위해 수정되었습니다. 이렇게 하면 제네릭이 아닌 컬렉션의 두 가지 단점이 사라집니다. 값 형식의 boxing 및 unboxing과 컬렉션에 저장할 형식을 지정할 수 없는 것이 그 단점입니다. 두 컬렉션에 대한 작업은 동일합니다. 인스턴스화되는 방법만 다릅니다.

제네릭 <xref:System.Collections.Generic.Stack%601> 컬렉션을 사용하는 이 예제와 위에서 작성된 예제를 비교합니다. 자주 액세스되는 큰 컬렉션에서 이 예제의 성능은 위의 예제보다 훨씬 뛰어날 것입니다.

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>참고 항목

[제네릭](generics-cpp-component-extensions.md)
