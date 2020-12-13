---
description: '방법: 어셈블리에서 STL/CLR 컨테이너 노출에 대해 자세히 알아보세요.'
title: '방법: 어셈블리에서 STL/CLR 컨테이너 노출'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: a4ed92af956def030c80f8f303f0a7501c4944c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134981"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>방법: 어셈블리에서 STL/CLR 컨테이너 노출

및와 같은 STL/CLR `list` 컨테이너 `map` 는 템플릿 ref 클래스로 구현 됩니다. 컴파일 시간에 c + + 템플릿이 인스턴스화되기 때문에 동일한 서명이 있지만 다른 어셈블리에 있는 두 템플릿 클래스는 실제로는 서로 다른 형식입니다. 즉, 어셈블리 경계에서 템플릿 클래스를 사용할 수 없습니다.

크로스 어셈블리 공유를 가능 하 게 하기 위해 STL/CLR 컨테이너는 제네릭 인터페이스를 구현 <xref:System.Collections.Generic.ICollection%601> 합니다. 이 제네릭 인터페이스를 사용 하 여 c + +, c # 및 Visual Basic을 비롯 한 제네릭을 지 원하는 모든 언어는 STL/CLR 컨테이너에 액세스할 수 있습니다.

이 항목에서는 c + + 어셈블리에 작성 된 여러 STL/CLR 컨테이너의 요소를 표시 하는 방법을 보여 줍니다 `StlClrClassLibrary` . 액세스할 두 어셈블리를 표시 `StlClrClassLibrary` 합니다. 첫 번째 어셈블리는 c + +로 작성 되 고 두 번째 어셈블리는 c #으로 작성 됩니다.

두 어셈블리가 c + +로 작성 된 경우 해당 typedef를 사용 하 여 컨테이너의 제네릭 인터페이스에 액세스할 수 있습니다 `generic_container` . 예를 들어 형식의 컨테이너가 있는 경우 `cliext::vector<int>` 해당 제네릭 인터페이스는 `cliext::vector<int>::generic_container` 입니다. 마찬가지로 `generic_iterator` 에서와 같이 typedef를 사용 하 여 제네릭 인터페이스에 대해 반복기를 가져올 수 있습니다 `cliext::vector<int>::generic_iterator` .

이러한 형식 정의는 c + + 헤더 파일에서 선언 되므로 다른 언어로 작성 된 어셈블리는이를 사용할 수 없습니다. 따라서 c # 또는 다른 .NET 언어로의 제네릭 인터페이스에 액세스 하려면를 `cliext::vector<int>` 사용 `System.Collections.Generic.ICollection<int>` 합니다. 이 컬렉션을 반복 하려면 루프를 사용 `foreach` 합니다.

다음 표에서는 각 STL/CLR 컨테이너가 구현 하는 제네릭 인터페이스를 보여 줍니다.

|STL/CLR 컨테이너|제네릭 인터페이스|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> `queue`, `priority_queue` 및 `stack` 컨테이너는 반복기를 지원 하지 않으므로 제네릭 인터페이스를 구현 하지 않으며 크로스 어셈블리에 액세스할 수 없습니다.

## <a name="example-1"></a>예제 1

### <a name="description"></a>설명

이 예제에서는 개인 STL/CLR 멤버 데이터를 포함 하는 c + + 클래스를 선언 합니다. 그런 다음 클래스의 전용 컬렉션에 대 한 액세스 권한을 부여 하는 공용 메서드를 선언 합니다. 이 작업은 두 가지 방법, 즉, c + + 클라이언트와 기타 .NET 클라이언트를 위한 것입니다.

### <a name="code"></a>코드

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>예제 2

### <a name="description"></a>설명

이 예제에서는 예제 1에 선언 된 클래스를 구현 합니다. 클라이언트에서이 클래스 라이브러리를 사용 하려면 매니페스트 도구 **mt.exe** 를 사용 하 여 매니페스트 파일을 DLL에 포함 합니다. 자세한 내용은 코드 주석을 참조 하세요.

매니페스트 도구 및 side-by-side 어셈블리에 대 한 자세한 내용은 [c/c + + 격리 된 응용 프로그램 및 Side-by-side 어셈블리 빌드](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)를 참조 하세요.

### <a name="code"></a>코드

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>예제 3

### <a name="description"></a>Description

이 예제에서는 예제 1과 2에서 만든 클래스 라이브러리를 사용 하는 c + + 클라이언트를 만듭니다. 이 클라이언트는 `generic_container` STL/CLR 컨테이너의 typedef를 사용 하 여 컨테이너를 반복 하 고 해당 내용을 표시 합니다.

### <a name="code"></a>코드

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>출력

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>예제 4

### <a name="description"></a>Description

이 예제에서는 예제 1과 2에서 만든 클래스 라이브러리를 사용 하는 c # 클라이언트를 만듭니다. 이 클라이언트는 <xref:System.Collections.Generic.ICollection%601> STL/CLR 컨테이너의 메서드를 사용 하 여 컨테이너를 반복 하 고 해당 내용을 표시 합니다.

### <a name="code"></a>코드

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>출력

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>참조

[STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)
