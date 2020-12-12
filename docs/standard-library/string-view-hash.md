---
description: '자세히 알아보기: hash &lt; string_view &gt; 특수화'
title: hash &lt; string_view &gt; 특수화
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::hash
helpviewer_keywords:
- std::basic_string_view::hash
ms.openlocfilehash: cf4012752bbd8b3531920e78d612e78479de4b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183687"
---
# <a name="hashltstring_viewgt-specialization"></a>hash &lt; string_view &gt; 특수화

String_view 지정 된 해시 값을 생성 하는 템플릿 특수화입니다.

```cpp
template <class CharType, class Traits>
struct hash<basic_string_view<CharType, Traits>>
{
    typedef basic_string_view<CharType, Traits> argument_type;
    typedef size_t result_type;

    size_t operator()(const basic_string_view<CharType, Traits>) const
        noexcept;
};
```

### <a name="remarks"></a>설명

String_view 해시는 기본 문자열 개체의 해시와 같습니다.

### <a name="example"></a>예제

```cpp
//compile with: /std:c++17
#include <string>
#include <string_view>
#include <iostream>

using namespace std;

int main()
{
    string_view sv{ "Hello world" };
    string s{ "Hello world" };
    cout << boolalpha << (hash<string_view>{}(sv)
        == hash<string>{}(s)); // true
}
```
