---
description: '&lt;Unordered_set 연산자에 대 한 자세한 정보 &gt;'
title: '&lt;unordered_set&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 6404ea9348dedea1e8ecdd4eefbca6b7c1b8158f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153735"
---
# <a name="ltunordered_setgt-operators"></a>&lt;unordered_set&gt; 연산자

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 [unordered_set](../standard-library/unordered-set-class.md) 개체가 우변에 있는 unordered_set 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`unordered_set` 형식의 개체입니다.

*오른쪽*\
`unordered_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** unordered_sets 같지 않으면이 고, 그렇지 않으면입니다. **`false`** 같으면이 고, 그렇지 않으면입니다.

### <a name="remarks"></a>설명

unordered_set 개체 간의 비교는 해당 요소를 저장하는 임의의 순서에 의해 영향을 받지 않습니다. 두 unordered_set는 요소 수가 같고 특정 컨테이너의 요소가 다른 컨테이너의 요소 순열이면 동일합니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**출력:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 [unordered_set](../standard-library/unordered-set-class.md) 개체가 우변에 있는 unordered_set 개체와 같은지 테스트합니다.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`unordered_set` 형식의 개체입니다.

*오른쪽*\
`unordered_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** unordered_sets 같으면이 고, 그렇지 않으면입니다. **`false`** 동일 하지 않은 경우입니다.

### <a name="remarks"></a>설명

unordered_set 개체 간의 비교는 해당 요소를 저장하는 임의의 순서에 의해 영향을 받지 않습니다. 두 unordered_set는 요소 수가 같고 특정 컨테이너의 요소가 다른 컨테이너의 요소 순열이면 동일합니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="operator-multiset"></a><a name="op_neq_unordered_multiset"></a> operator! = (multiset)

연산자의 좌변에 있는 [unordered_multiset](../standard-library/unordered-multiset-class.md) 개체가 우변에 있는 unordered_multiset 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`unordered_multiset` 형식의 개체입니다.

*오른쪽*\
`unordered_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** unordered_multisets 같지 않으면이 고, 그렇지 않으면입니다. **`false`** 같으면이 고, 그렇지 않으면입니다.

### <a name="remarks"></a>설명

unordered_multiset 개체 간의 비교는 해당 요소를 저장하는 임의의 순서에 의해 영향을 받지 않습니다. 두 unordered_multiset는 요소 수가 같고 특정 컨테이너의 요소가 다른 컨테이너의 요소 순열이면 동일합니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="operator-multiset"></a><a name="op_eq_eq_unordered_multiset"></a> operator = = (multiset)

연산자의 좌변에 있는 [unordered_multiset](../standard-library/unordered-multiset-class.md) 개체가 우변에 있는 unordered_multiset 개체와 같은지 테스트합니다.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`unordered_multiset` 형식의 개체입니다.

*오른쪽*\
`unordered_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** unordered_multisets 같으면이 고, 그렇지 않으면입니다. **`false`** 동일 하지 않은 경우입니다.

### <a name="remarks"></a>설명

unordered_multiset 개체 간의 비교는 해당 요소를 저장하는 임의의 순서에 의해 영향을 받지 않습니다. 두 unordered_multiset는 요소 수가 같고 특정 컨테이너의 요소가 다른 컨테이너의 요소 순열이면 동일합니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
