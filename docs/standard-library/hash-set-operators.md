---
title: '&lt;hash_set&gt; 연산자 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
dev_langs:
- C++
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: b9c6fe6b39b771b81b6508c10abd43c71774f9a7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108260"
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set&gt; 연산자

||||
|-|-|-|
|[operator!=](#op_neq)|[operator!=(hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[operator==(hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>  operator!=

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_set 개체가 우변에 있는 hash_set 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*left*<br/>
`hash_set` 형식의 개체입니다.

*right*<br/>
`hash_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

hash_set이 같지 않으면 **true**이고, hash_set이 같으면 **false**입니다.

### <a name="remarks"></a>설명

hash_set 개체 간의 비교는 해당 요소 간의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_set은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

멤버는 [< hash_map >](../standard-library/hash-map.md) 하 고 [< hash_set >](../standard-library/hash-set.md) 헤더 파일에는 [stdext Namespace](../standard-library/stdext-namespace.md).

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

## <a name="op_eq_eq"></a>  operator==

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_set 개체가 우변에 있는 hash_set 개체와 같은지 테스트합니다.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*left*<br/>
`hash_set` 형식의 개체입니다.

*right*<br/>
`hash_set` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 hash_set이 연산자 우변의 hash_set과 같으면 **true**이고 그렇지 않으면 **false**입니다.

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

## <a name="neq_hash_multiset"></a>  operator!=(hash_multiset)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_multiset 개체가 우변에 있는 hash_multiset 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*left*<br/>
`hash_multiset` 형식의 개체입니다.

*right*<br/>
`hash_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

hash_multiset이 같지 않으면 **true**이고, hash_multiset이 같으면 **false**입니다.

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

## <a name="eq_eq_hash_multiset"></a>  operator==(hash_multiset)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_multiset 개체가 우변에 있는 hash_multiset 개체와 같은지 테스트합니다.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*left*<br/>
`hash_multiset` 형식의 개체입니다.

*right*<br/>
`hash_multiset` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 hash_multiset이 연산자 우변의 hash_multiset과 같으면 **true**이고 그렇지 않으면 **false**입니다.

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

## <a name="see-also"></a>참고자료

[<hash_set>](../standard-library/hash-set.md)<br/>
