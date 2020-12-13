---
description: '자세히 알아보기: &lt; 배열 &gt; 함수'
title: '&lt;array&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: b2f6cd72c5f82f36914f96dee6924654a96a9fc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149554"
---
# <a name="ltarraygt-functions"></a>&lt;array&gt; 함수

헤더에는 \<array> `get` `swap` **배열** 개체에 대해 작동 하는 멤버 함수 두 개 (및)가 포함 되어 있습니다.

[가져오기](#get)\
[스왑을](#swap)

## <a name="get"></a><a name="get"></a> 가져오기

배열의 지정된 요소에 대한 참조를 반환합니다.

```cpp
template <int Index, class T, size_t N>
constexpr T& get(array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr const T& get(const array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr T&& get(array<T, N>&& arr) noexcept;
```

### <a name="parameters"></a>매개 변수

*인덱싱할*\
요소 오프셋입니다.

*트*\
요소의 형식입니다.

*개의*\
배열의 요소 수입니다.

*arr*\
선택할 배열입니다.

### <a name="example"></a>예제

```cpp
#include <array>
#include <iostream>

using namespace std;

typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display odd elements " 1 3"
    cout << " " << get<1>(c0);
    cout << " " << get<3>(c0) << endl;
}
```

```Output
0 1 2 3
1 3
```

## <a name="swap"></a><a name="swap"></a> 스왑을

`std::swap`두 **배열** 개체를 교환 하는의 멤버가 아닌 템플릿 특수화입니다.

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>매개 변수

*Ty*\
요소의 형식입니다.

*개의*\
배열의 크기입니다.

*비어*\
교환할 첫 번째 배열입니다.

*오른쪽*\
교환할 두 번째 배열입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `left.swap(right)`를 실행합니다.

### <a name="example"></a>예제

```cpp
// std__array__swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="see-also"></a>참고 항목

[\<array>](../standard-library/array.md)
