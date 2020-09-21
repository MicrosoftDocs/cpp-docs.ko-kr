---
title: '&lt;map&gt; 연산자'
ms.date: 03/27/2019
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 5cfd40add5e2b2503a5eea9610cadffd97bb0a80
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743323"
---
# <a name="ltmapgt-operators"></a>&lt;map&gt; 연산자

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 맵이 동일 하지 않으면이 고, 그렇지 않으면입니다. **`false`** map이 같으면입니다.

### <a name="remarks"></a>설명

map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 map은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체보다 작은지 테스트합니다.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 map이 연산자 우변의 map 보다 엄격 하 게 작으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 작음 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
```

```Output
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체보다 작거나 같은지 테스트합니다.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 map이 연산자 우변의 map 보다 작거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
```

```Output
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체와 같은지 테스트합니다.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 map이 연산자 우변의 맵과 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 map은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체보다 큰지 테스트합니다.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 map이 연산자 우변의 map 보다 크면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

map 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 큼 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
/* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

연산자의 좌변에 있는 map 개체가 우변에 있는 map 개체보다 크거나 같은지 테스트합니다.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`map` 형식의 개체입니다.

*오른쪽*\
`map` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 map이 목록 오른쪽의 map 보다 크거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
```

```Output
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
```

## <a name="operator-multimap"></a><a name="op_neq_multimap"></a> operator! = (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** multimap이 같지 않으면입니다. **`false`** multimap이 같으면입니다.

### <a name="remarks"></a>설명

multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 multimap은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
```

```Output
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
```

## <a name="operatorlt-multimap"></a><a name="op_lt_multimap"></a> 연산자 &lt; (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체보다 작은지 테스트합니다.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 multimap이 연산자 우변의 multimap 보다 엄격 하 게 작으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 작음 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
```

## <a name="operatorlt-multimap"></a><a name="op_lt_eq_multimap"></a> 연산자 &lt; = (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체보다 작거나 같은지 테스트합니다.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 multimap이 연산자 우변의 multimap 보다 작거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
```

```Output
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
```

## <a name="operator-multimap"></a><a name="op_eq_eq_multimap"></a> operator = = (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체와 같은지 테스트합니다.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 multimap이 연산자 우변의 multimap과 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 multimap은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
```

```Output
m1 and m2 are not equal
m1 and m3 are equal
```

## <a name="operatorgt-multimap"></a><a name="op_gt_multimap"></a> 연산자 &gt; (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체보다 큰지 테스트합니다.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 multimap이 연산자 우변의 multimap 보다 크면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

multimap 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 큼 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
```

```Output
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
```

## <a name="operatorgt-multimap"></a><a name="op_gt_eq_multimap"></a> 연산자 &gt; = (multimap)

연산자의 좌변에 있는 multimap 개체가 우변에 있는 multimap 개체보다 크거나 같은지 테스트합니다.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`multimap` 형식의 개체입니다.

*오른쪽*\
`multimap` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 multimap가 목록의 오른쪽에 있는 multimap 보다 크거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
```
