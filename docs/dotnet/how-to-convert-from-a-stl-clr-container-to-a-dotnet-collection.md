---
title: '방법: STL/CLR 컨테이너에서 .NET 컬렉션으로 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f5e289c330c83ac0c630a5b1f8f97b8c65fc7efb
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686446"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>방법: STL/CLR 컨테이너에서 .NET 컬렉션으로 변환

이 항목에서는 STL/CLR 컨테이너를 해당 하는 .NET 컬렉션으로 변환 하는 방법을 보여 줍니다. 예를 들어 STL/CLR [벡터](../dotnet/vector-stl-clr.md) 를 .net으로 변환 하는 방법과 <xref:System.Collections.Generic.ICollection%601> stl/clr [맵을](../dotnet/map-stl-clr.md) .net으로 변환 하는 방법을 보여 <xref:System.Collections.Generic.IDictionary%602> 주지만 프로시저는 모든 컬렉션 및 컨테이너와 유사 합니다.

### <a name="to-create-a-collection-from-a-container"></a>컨테이너에서 컬렉션을 만들려면

1. 다음 방법 중 하나를 사용합니다.

   - 컨테이너의 일부를 변환 하려면 [make_collection](../dotnet/make-collection-stl-clr.md) 함수를 호출 하 고, STL/CLR 컨테이너의 시작 반복기와 끝 반복기를 전달 하 여 .net 컬렉션에 복사 합니다. 이 템플릿 함수는 STL/CLR 반복기를 템플릿 인수로 사용 합니다. 첫 번째 예제에서는이 메서드를 보여 줍니다.

   - 전체 컨테이너를 변환 하려면 컨테이너를 적절 한 .NET 컬렉션 인터페이스 또는 인터페이스 컬렉션으로 캐스팅 합니다. 두 번째 예제에서는이 메서드를 보여 줍니다.

## <a name="examples"></a>예제

이 예제에서는 STL/CLR을 만들고 `vector` 여기에 5 개의 요소를 추가 합니다. 그런 다음 함수를 호출 하 여 .NET 컬렉션을 만듭니다 `make_collection` . 마지막으로 새로 만든 컬렉션의 내용을 표시 합니다.

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

이 예제에서는 STL/CLR을 만들고 `map` 여기에 5 개의 요소를 추가 합니다. 그런 다음 .NET을 만들어에 <xref:System.Collections.Generic.IDictionary%602> `map` 직접 할당 합니다. 마지막으로 새로 만든 컬렉션의 내용을 표시 합니다.

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>추가 정보

[STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)<br/>
[방법: .NET 컬렉션에서 STL/CLR 컨테이너로 변환](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter(STL/CLR)](../dotnet/range-adapter-stl-clr.md)
