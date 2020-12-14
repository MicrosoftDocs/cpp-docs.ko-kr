---
description: '자세한 정보: STL/CLR 라이브러리 참조'
title: STL/CLR 라이브러리 참조
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: c051b58b76a70dd5ef3bd17b1f9bec1cbeeccebf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335323"
---
# <a name="stlclr-library-reference"></a>STL/CLR 라이브러리 참조

STL/CLR 라이브러리는 c + + 및 .NET Framework CLR (공용 언어 런타임)과 함께 사용 하기 위한 c + + 표준 라이브러리 컨테이너와 비슷한 인터페이스를 제공 합니다. STL/CLR은 c + + 표준 라이브러리의 Microsoft 구현과 완전히 별개입니다. STL/CLR은 레거시 지원을 위해 유지 되지만 c + + 표준으로 최신 상태로 유지 되지 않습니다. 가능 하면 STL/CLR 대신 네이티브 [c + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md) 컨테이너를 사용 하는 것이 좋습니다.

STL/CLR을 사용 하려면:

- 해당 하는 일반적인 c + + 표준 라이브러리 대신 **cliext** include 하위 디렉터리의 헤더를 포함 합니다.

- 대신를 사용 하 여 라이브러리 이름을 한정 `cliext::` `std::` 합니다.

STL/CLR 라이브러리는 c + + 및 .NET Framework CLR (공용 언어 런타임)과 함께 사용 하기 위한 STL과 유사한 인터페이스를 제공 합니다. 이 라이브러리는 레거시 지원을 위해 유지 되지만 c + + 표준으로 최신 상태로 유지 되지 않습니다. STL/CLR 대신 네이티브 [c + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md) 컨테이너를 사용 하는 것이 좋습니다.

## <a name="in-this-section"></a>섹션 내용

[cliext 네임 스페이스](../dotnet/cliext-namespace.md)<br/>
STL/CLR 라이브러리의 모든 형식이 포함 된 네임 스페이스에 대해 설명 합니다.

[STL/CLR 컨테이너](../dotnet/stl-clr-containers.md)<br/>
컨테이너 요소에 대 한 요구 사항, 삽입할 수 있는 요소의 형식 및 소유권 문제를 포함 하 여 c + + 표준 라이브러리에 있는 컨테이너에 대 한 개요를 제공 합니다.

[STL/CLR 컨테이너 요소에 대 한 요구 사항](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
C + + 표준 라이브러리 컨테이너에 삽입 되는 모든 참조 형식에 대 한 최소 요구 사항을 설명 합니다.

[방법: .NET 컬렉션에서 STL/CLR 컨테이너로 변환](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
.NET 컬렉션을 STL/CLR 컨테이너로 변환 하는 방법을 설명 합니다.

[방법: STL/CLR 컨테이너에서 .NET 컬렉션으로 변환](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
STL/CLR 컨테이너를 .NET 컬렉션으로 변환 하는 방법을 설명 합니다.

[방법: 어셈블리에서 STL/CLR 컨테이너 노출](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
C + + 어셈블리로 작성 된 여러 STL/CLR 컨테이너의 요소를 표시 하는 방법을 보여 줍니다.

또한이 섹션에서는 STL/CLR의 다음 구성 요소에 대해서도 설명 합니다.

:::row:::
   :::column span="":::
      [`adapter` (STL/CLR)](../dotnet/adapter-stl-clr.md)\
      [`algorithm` (STL/CLR)](../dotnet/algorithm-stl-clr.md)\
      [`deque` (STL/CLR)](../dotnet/deque-stl-clr.md)\
      [`for each`, `in`](../dotnet/for-each-in.md)\
      [`functional` (STL/CLR)](../dotnet/functional-stl-clr.md)\
      [`hash_map` (STL/CLR)](../dotnet/hash-map-stl-clr.md)\
      [`hash_multimap` (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)\
      [`hash_multiset` (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)\
      [`hash_set` (STL/CLR)](../dotnet/hash-set-stl-clr.md)\
      [`list` (STL/CLR)](../dotnet/list-stl-clr.md)\
   :::column-end:::
   :::column span="":::
      [`map` (STL/CLR)](../dotnet/map-stl-clr.md)\
      [`multimap` (STL/CLR)](../dotnet/multimap-stl-clr.md)\
      [`multiset` (STL/CLR)](../dotnet/multiset-stl-clr.md)\
      [`numeric` (STL/CLR)](../dotnet/numeric-stl-clr.md)\
      [`priority_queue` (STL/CLR)](../dotnet/priority-queue-stl-clr.md)\
      [`queue` (STL/CLR)](../dotnet/queue-stl-clr.md)\
      [`set` (STL/CLR)](../dotnet/set-stl-clr.md)\
      [`stack` (STL/CLR)](../dotnet/stack-stl-clr.md)\
      [`utility` (STL/CLR)](../dotnet/utility-stl-clr.md)\
      [`vector` (STL/CLR)](../dotnet/vector-stl-clr.md)\
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>참고 항목

[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
