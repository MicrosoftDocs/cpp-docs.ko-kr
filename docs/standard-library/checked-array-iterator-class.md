---
title: checked_array_iterator 클래스
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: 467a94212d7b1e9d28a3229660b8a8619993b201
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684943"
---
# <a name="checked_array_iterator-class"></a>checked_array_iterator 클래스

이 `checked_array_iterator` 클래스를 사용하여 확인한 반복기로 배열 또는 포인터를 변환할 수 있습니다 이러한 경고를 전역적으로 해제하는 대신 이 클래스를 원시 포인터 또는 배열에 대한 래퍼로 목적에 따라 사용하여([make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) 함수 사용) 확인을 제공하고 확인되지 않은 포인터 경고를 관리합니다. 필요에 따라 이 클래스의 확인되지 않은 버전, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)를 사용할 수 있습니다.

> [!NOTE]
> 이 클래스는 C++ 표준 라이브러리의 Microsoft 확장입니다. 이 함수를 사용하여 구현한 코드는 이 Microsoft 확장을 지원하지 않는 C++ 표준 빌드 환경으로 이식할 수 없습니다. 이 클래스의 사용을 요구하지 않는 코드를 작성하는 방법을 보여 주는 예는 아래의 두 번째 예제를 참조하세요.

## <a name="syntax"></a>구문

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>설명

이 클래스는 [stdext](../standard-library/stdext-namespace.md) 네임스페이스에 정의됩니다.

확인된 반복기 기능에 대한 자세한 내용 및 예제 코드는 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="examples"></a>예제

다음 샘플은 확인된 배열 반복기를 정의 및 사용하는 방법을 보여 줍니다.

대상이 복사하는 모든 요소를 보관할 수 없는 크기인 경우, 라인을 변경하는 경우가 해당합니다.

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

을

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

런타임 오류가 발생합니다.

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

C++ 표준 라이브러리 알고리즘을 사용할 경우 `checked_array_iterator` 클래스를 사용할 필요가 없도록 하려면 동적으로 할당된 배열 대신 `vector`를 사용해 보세요. 다음 예제에서는 이 작업을 수행하는 방법을 보여 줍니다.

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|기본 반복기에서 기본 `checked_array_iterator` 또는 `checked_array_iterator`를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[difference_type](#difference_type)|동일한 컨테이너 안에서 요소를 참조하는 두 `checked_array_iterator` 사이의 차이를 제공하는 형식입니다.|
|[놓고](#pointer)|`checked_array_iterator`로 주소를 지정하는 요소에 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`checked_array_iterator`로 주소를 지정하는 요소에 참조를 제공하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[base](#base)|`checked_array_iterator`에서 기본 반복기를 복구합니다.|

### <a name="operators"></a>연산자

|연산자|Description|
|-|-|
|[연산자 = =](#op_eq_eq)|두 `checked_array_iterator`가 같은지 테스트합니다.|
|[연산자! =](#op_neq)|두 `checked_array_iterator`가 다른지 테스트합니다.|
|[연산자<](#op_lt)|연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 작은지 테스트합니다.|
|[연산자>](#op_gt)|연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 큰지 테스트합니다.|
|[연산자<=](#op_lt_eq)|연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 작거나 같은지 테스트합니다.|
|[연산자>=](#op_gt_eq)|연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 크거나 같은지 테스트합니다.|
|[연산자](#op_star)|`checked_array_iterator`가 주소 지정하는 요소를 반환합니다.|
|[연산자->](#op_arrow)|`checked_array_iterator`가 주소 지정하는 요소로 포인터를 반환합니다.|
|[operator + +](#op_add_add)|`checked_array_iterator`를 다음 요소로 증가시킵니다.|
|[연산자--](#operator--)|`checked_array_iterator`를 이전 요소로 감소시킵니다.|
|[operator + =](#op_add_eq)|`checked_array_iterator`에 지정된 오프셋을 추가합니다.|
|[연산자 +](#op_add)|반복기에 오프셋을 추가하고 새 오프셋 위치에서 삽입된 요소를 주소 지정하는 새 `checked_array_iterator`를 반환합니다.|
|[연산자-=](#operator-_eq)|`checked_array_iterator`에서 지정된 오프셋을 감소시킵니다.|
|[연산자](#operator-)|반복기에서 오프셋을 감소시키고 새로운 오프셋 위치에서 삽입된 요소를 주소 지정하는 새로운 `checked_array_iterator`를 반환합니다.|
|[operator&#91;&#93;](#op_at)|`checked_array_iterator`에서 주소 지정하는 요소의 요소 오프셋으로 지정된 위치 수만큼 참조를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** stdext

## <a name="checked_array_iteratorbase"></a><a name="base"></a> checked_array_iterator:: base

`checked_array_iterator`에서 기본 반복기를 복구합니다.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iteratorchecked_array_iterator"></a><a name="checked_array_iterator"></a> checked_array_iterator:: checked_array_iterator

기본 반복기에서 기본 `checked_array_iterator` 또는 `checked_array _iterator`를 생성합니다.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>매개 변수

*ptr*\
배열에 대한 포인터입니다.

*크기가*\
배열의 크기입니다.

*인덱싱할*\
(선택 사항) 반복기를 초기화하는 배열의 요소입니다.  기본적으로 반복기는 배열의 첫 번째 요소로 초기화됩니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="checked_array_iteratordifference_type"></a><a name="difference_type"></a> checked_array_iterator::d ifference_type

동일한 컨테이너 안에서 요소를 참조하는 두 `checked_array_iterator` 사이의 차이를 제공하는 형식입니다.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>설명

`checked_array_iterator` 차이 형식은 반복기 차이 형식과 같습니다.

코드 샘플은 [checked_array_iterator:: operator []](#op_at) 를 참조 하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratoroperator"></a><a name="op_eq_eq"></a> checked_array_iterator:: operator = =

두 `checked_array_iterator`가 같은지 테스트합니다.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
같은지 확인할 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_neq"></a> checked_array_iterator:: operator! =

두 `checked_array_iterator`가 다른지 테스트합니다.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
같지 않은지 확인할 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt"></a> checked_array_iterator:: operator&lt;

연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 작은지 테스트합니다.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
같지 않은지 확인할 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt"></a> checked_array_iterator:: operator&gt;

연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 큰지 테스트합니다.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 대상인 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

코드 샘플은 [checked_array_iterator: &lt; : operator](#op_lt) 를 참조 하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt_eq"></a> checked_array_iterator:: operator&lt;=

연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 작거나 같은지 테스트합니다.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 대상인 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

코드 샘플은 [checked_array_iterator: &gt; = : operator](#op_gt_eq) 를 참조 하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt_eq"></a> checked_array_iterator:: operator&gt;=

연산자의 좌변에 있는 `checked_array_iterator`가 우변에 있는 `checked_array_iterator`보다 크거나 같은지 테스트합니다.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 대상인 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_star"></a> checked_array_iterator:: operator *

`checked_array_iterator`가 주소 지정하는 요소를 반환합니다.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>반환 값

`checked_array_iterator`에서 주소를 지정한 요소의 값입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="checked_array_iteratoroperator-gt"></a><a name="op_arrow"></a> checked_array_iterator:: operator-&gt;

`checked_array_iterator`가 주소 지정하는 요소로 포인터를 반환합니다.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>반환 값

`checked_array_iterator`에서 주소를 지정한 요소에 대한 포인터입니다.

### <a name="remarks"></a>설명

코드 샘플은 [checked_array_iterator::pointer](#pointer)를 참조하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratoroperator"></a><a name="op_add_add"></a> checked_array_iterator:: operator + +

`checked_array_iterator`를 다음 요소로 증가시킵니다.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>반환 값

첫 번째 연산자는 사전 증가된 `checked_array_iterator`를 반환하고, 두 번째(사후 증가) 연산자는 증가된 `checked_array_iterator`의 복사본을 반환합니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
77
*/
```

## <a name="checked_array_iteratoroperator--"></a><a name="operator--"></a> checked_array_iterator:: operator--

`checked_array_iterator`를 이전 요소로 감소시킵니다.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>반환 값

첫 번째 연산자는 사전 감소된 `checked_array_iterator`를 반환하고, 두 번째(사후 감소) 연산자는 감소된 `checked_array_iterator`의 복사본을 반환합니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
6
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add_eq"></a> checked_array_iterator:: operator + =

`checked_array_iterator`에 지정된 오프셋을 추가합니다.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>매개 변수

*_Off*\
반복기를 증가시킬 오프셋입니다.

### <a name="return-value"></a>반환 값

`checked_array_iterator`에서 주소를 지정한 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add"></a> checked_array_iterator:: operator +

반복기에 오프셋을 추가하고 새 오프셋 위치에서 삽입된 요소를 주소 지정하는 새 `checked_array_iterator`를 반환합니다.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>매개 변수

*_Off*\
`checked_array_iterator`에 추가할 오프셋입니다.

### <a name="return-value"></a>반환 값

오프셋 요소의 주소를 지정하는 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-_eq"></a> checked_array_iterator:: operator-=

`checked_array_iterator`에서 지정된 오프셋을 감소시킵니다.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>매개 변수

*_Off*\
반복기를 증가시킬 오프셋입니다.

### <a name="return-value"></a>반환 값

`checked_array_iterator`에서 주소를 지정한 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
/* Output:
199
3
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-"></a> checked_array_iterator:: operator-

반복기에서 오프셋을 감소시키고 새로운 오프셋 위치에서 삽입된 요소를 주소 지정하는 새로운 `checked_array_iterator`를 반환합니다.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>매개 변수

*_Off*\
`checked_array_iterator`에서 감소될 오프셋입니다.

### <a name="return-value"></a>반환 값

오프셋 요소의 주소를 지정하는 `checked_array_iterator`입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratoroperator"></a><a name="op_at"></a> checked_array_iterator:: operator []

`checked_array_iterator`에서 주소 지정하는 요소의 요소 오프셋으로 지정된 위치 수만큼 참조를 반환합니다.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>매개 변수

*_Off*\
`checked_array_iterator` 주소의 오프셋입니다.

### <a name="return-value"></a>반환 값

요소 오프셋에 대한 참조입니다.

### <a name="remarks"></a>설명

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
/* Output:
3
*/
```

## <a name="checked_array_iteratorpointer"></a><a name="pointer"></a> checked_array_iterator::p ointer

`checked_array_iterator`로 주소를 지정하는 요소에 포인터를 제공하는 형식입니다.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>설명

코드 샘플은 [checked_array_iterator:: operator *](#op_star) 를 참조 하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="checked_array_iteratorreference"></a><a name="reference"></a> checked_array_iterator:: reference

`checked_array_iterator`로 주소를 지정하는 요소에 참조를 제공하는 형식입니다.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>설명

코드 샘플은 [checked_array_iterator:: operator []](#op_at) 를 참조 하세요.

자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="see-also"></a>추가 정보

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
