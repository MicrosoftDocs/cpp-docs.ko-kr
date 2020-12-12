---
description: '&lt;Hash_map 연산자에 대 한 자세한 정보 &gt;'
title: '&lt;hash_map&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: f3374ee86a989a90add86e85d6a9bf15959e26b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324124"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map&gt; 연산자

[연산자! =](#op_neq)\
[operator! = (multimap)](#op_neq_mm)\
[연산자 = =](#op_eq_eq)\
[operator = = (multimap)](#op_eq_eq_mm)

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_map 개체가 우변에 있는 hash_map 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_map` 형식의 개체입니다.

*오른쪽*\
`hash_map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** hash_maps 같지 않으면이 고, 그렇지 않으면입니다. **`false`** hash_maps 같으면입니다.

### <a name="remarks"></a>설명

hash_map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_map은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

<의 멤버는 [stdext 네임 스페이스](stdext-namespace.md)의 hash_set 헤더 파일을>하 고 [<](hash-set.md) [hash_map](hash-map.md) 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

연산자의 좌변에 있는 hash_map 개체가 우변에 있는 hash_map 개체와 같은지 테스트합니다.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_map` 형식의 개체입니다.

*오른쪽*\
`hash_map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 hash_map 연산자의 우변에 있는 hash_map와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

hash_map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_map은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a> operator! = (hash_multimap)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](unordered-multimap-class.md)입니다.

연산자의 좌변에 있는 hash_multimap 개체가 우변에 있는 hash_multimap 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_multimap` 형식의 개체입니다.

*오른쪽*\
`hash_multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** hash_multimaps 같지 않으면이 고, 그렇지 않으면입니다. **`false`** hash_multimaps 같으면입니다.

### <a name="remarks"></a>설명

hash_multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_multimap은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a> operator = = (hash_multimap)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](unordered-multimap-class.md)입니다.

연산자의 좌변에 있는 hash_multimap 개체가 우변에 있는 hash_multimap 개체와 같은지 테스트합니다.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`hash_multimap` 형식의 개체입니다.

*오른쪽*\
`hash_multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 hash_multimap 연산자의 우변에 있는 hash_multimap와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

hash_multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 hash_multimap은 같은 것이고 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>참고 항목

[<hash_map>](hash-map.md)
