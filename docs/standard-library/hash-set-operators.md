---
description: '&lt;Hash_set 연산자에 대 한 자세한 정보 &gt;'
title: '&lt;hash_set&gt; 연산자'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: a52c749df2bdd690fcd936c9a361251728696ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324085"
---
# <a name="lthash_setgt-operators"></a>&lt;hash_set&gt; 연산자

[연산자! =](#op_neq)\
[operator! = (hash_multiset)](#op_neq_hash_multiset)\
[연산자 = =](#op_eq_eq)\
[operator = = (hash_multiset)](#op_eq_eq_hash_multiset)

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_set 개체가 우변에 있는 hash_set 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_set` 형식의 개체입니다.

*오른쪽*\
`hash_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** hash_sets 같지 않으면이 고, 그렇지 않으면입니다. **`false`** hash_sets 같으면입니다.

### <a name="remarks"></a>설명

hash_set 개체 간의 비교는 해당 요소 간의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_set은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

[<hash_map>](../standard-library/hash-map.md) 및 [<hash_set](../standard-library/hash-set.md) 헤더 파일의 멤버는 [stdext 네임 스페이스](../standard-library/stdext-namespace.md)에 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_set 개체가 우변에 있는 hash_set 개체와 같은지 테스트합니다.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_set` 형식의 개체입니다.

*오른쪽*\
`hash_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 hash_set 연산자의 우변에 있는 hash_set와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

hash_set 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_set은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_neq_hash_multiset"></a> operator! = (hash_multiset)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_multiset 개체가 우변에 있는 hash_multiset 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_multiset` 형식의 개체입니다.

*오른쪽*\
`hash_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** hash_multisets 같지 않으면이 고, 그렇지 않으면입니다. **`false`** hash_multisets 같으면입니다.

### <a name="remarks"></a>설명

hash_multiset 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_multiset은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_eq_eq_hash_multiset"></a> operator = = (hash_multiset)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_multiset 개체가 우변에 있는 hash_multiset 개체와 같은지 테스트합니다.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_multiset` 형식의 개체입니다.

*오른쪽*\
`hash_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 hash_multiset 연산자의 우변에 있는 hash_multiset와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

hash_multiset 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_multiset은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>참고 항목

[<hash_set>](../standard-library/hash-set.md)
