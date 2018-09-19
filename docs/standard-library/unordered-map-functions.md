---
title: '&lt;unordered_map&gt; 함수 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_map/std::swap
- unordered_map/std::swap (unordered_map)
- unordered_map/std::swap (unordered_multimap)
dev_langs:
- C++
ms.assetid: cf2e4115-f205-4a0e-90be-a143ffcc1f44
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::swap (unordered_map/multimap)
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6d8a925f493a8299cf1afd8e851456277a68e9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715522"
---
# <a name="ltunorderedmapgt-functions"></a>&lt;unordered_map&gt; 함수

|||
|-|-|
|[swap(unordered_map)](#swap)|[swap(unordered_multimap)](#swap_function_multimap)|

## <a name="swap"></a>  swap(unordered_map)

두 컨테이너의 내용을 바꿉니다.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_map <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_map <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>매개 변수

*키*<br/>
키 형식입니다.

*Ty*<br/>
매핑된 형식입니다.

*해시*<br/>
해시 함수 개체 형식입니다.

*pred*<br/>
같음 비교 함수 개체 형식입니다.

*할당*<br/>
할당자 클래스입니다.

*left*<br/>
교환할 첫 번째 컨테이너입니다.

*right*<br/>
교환할 두 번째 컨테이너입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left.`[unordered_map::swap](../standard-library/unordered-map-class.md#swap)`(right)`을 실행합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__u_m_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="swap_function_multimap"></a>  swap(unordered_multimap)

두 컨테이너의 내용을 바꿉니다.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>매개 변수

*키*<br/>
키 형식입니다.

*Ty*<br/>
매핑된 형식입니다.

*해시*<br/>
해시 함수 개체 형식입니다.

*pred*<br/>
같음 비교 함수 개체 형식입니다.

*할당*<br/>
할당자 클래스입니다.

*left*<br/>
교환할 첫 번째 컨테이너입니다.

*right*<br/>
교환할 두 번째 컨테이너입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left.`[unordered_multimap::swap](../standard-library/unordered-multimap-class.md#swap)`(right)`을 실행합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__u_mm_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_multimap<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

    // display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>참고자료

[<unordered_map>](../standard-library/unordered-map.md)<br/>
