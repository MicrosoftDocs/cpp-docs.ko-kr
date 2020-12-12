---
description: '&lt;Unordered_map 함수에 대해 자세히 알아보세요. &gt;'
title: '&lt;unordered_map&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::swap
- unordered_map/std::swap (unordered_map)
- unordered_map/std::swap (unordered_multimap)
ms.assetid: cf2e4115-f205-4a0e-90be-a143ffcc1f44
helpviewer_keywords:
- std::swap (unordered_map/multimap)
ms.openlocfilehash: 2a1374935fa8116a3cb7e5447a659235acc0ebaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321503"
---
# <a name="ltunordered_mapgt-functions"></a>&lt;unordered_map&gt; 함수

[swap (unordered_map)](#swap) 
 [swap (unordered_multimap)](#swap_function_multimap)

## <a name="swap-unordered_map"></a><a name="swap"></a> swap (unordered_map)

두 컨테이너의 내용을 바꿉니다.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_map <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_map <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>매개 변수

*키인지*\
키 형식입니다.

*Ty*\
매핑된 형식입니다.

*해시로*\
해시 함수 개체 형식입니다.

*Pred*\
같음 비교 함수 개체 형식입니다.

*#C4*\
할당자 클래스입니다.

*비어*\
교환할 첫 번째 컨테이너입니다.

*오른쪽*\
교환할 두 번째 컨테이너입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left.` [unordered_map:: swap](../standard-library/unordered-map-class.md#swap)을 실행 합니다 `(right)` .

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

## <a name="swap-unordered_multimap"></a><a name="swap_function_multimap"></a> swap (unordered_multimap)

두 컨테이너의 내용을 바꿉니다.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>매개 변수

*키인지*\
키 형식입니다.

*Ty*\
매핑된 형식입니다.

*해시로*\
해시 함수 개체 형식입니다.

*Pred*\
같음 비교 함수 개체 형식입니다.

*#C4*\
할당자 클래스입니다.

*비어*\
교환할 첫 번째 컨테이너입니다.

*오른쪽*\
교환할 두 번째 컨테이너입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left.` [unordered_multimap:: swap](../standard-library/unordered-multimap-class.md#swap)을 실행 합니다 `(right)` .

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

## <a name="see-also"></a>참고 항목

[<unordered_map>](../standard-library/unordered-map.md)
