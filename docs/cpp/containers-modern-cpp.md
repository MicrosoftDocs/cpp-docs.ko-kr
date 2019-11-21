---
title: 컨테이너(최신 C++)
ms.date: 11/12/2019
ms.topic: conceptual
ms.openlocfilehash: 7ac2f30c2e7ab91a5f25125ccd07ad84c0116d9c
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245886"
---
# <a name="containers-modern-c"></a>컨테이너(최신 C++)

By default, use [std::vector](../standard-library/vector-class.md) as the preferred sequential container in C++. The performance of **std::vector** is comparable to C-style arrays in most scenarios and is far safer. **std::vector** is equivalent to `List<T>` in .NET languages.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Use [map](../standard-library/map-class.md) (not `unordered_map`) as the default associative container. Use [set](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), and [multiset](../standard-library/multiset-class.md) for degenerate & multi cases.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

When performance optimization is needed, consider using:

- The [array](../standard-library/array-class-stl.md) type when embedding is important, for example, as a class member.

- Unordered associative containers such as [unordered_map](../standard-library/unordered-map-class.md). These have lower per-element overhead and constant-time lookup, but they can be harder to use correctly and efficiently.

- Sorted `vector`. 자세한 내용은 [알고리즘](../cpp/algorithms-modern-cpp.md)을 참조하세요.

Don’t use C-style arrays. For older APIs that need direct access to the data, use accessor methods such as `f(vec.data(), vec.size());` instead.

For more information about containers, see [C++ Standard Library Containers](../standard-library/stl-containers.md).

## <a name="see-also"></a>참조

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
