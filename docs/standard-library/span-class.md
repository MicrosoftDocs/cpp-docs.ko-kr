---
title: span 클래스 (c + + 표준 라이브러리) | Microsoft Docs
description: 연속 하는 개체 시퀀스에 대 한 간단한 뷰를 제공 하는 STL (표준 템플릿 라이브러리) span 클래스에 대 한 API 참조입니다.
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: 297104820f5498e59397db9025aed1675984a060
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039966"
---
# <a name="span-class-c-standard-library"></a>span 클래스 (c + + 표준 라이브러리)

연속 된 개체 시퀀스에 대해 간단한 뷰를 제공 합니다. 범위는 기본 제공 배열, 또는에 저장 된 개체와 같이 메모리에서 다시 뒤쪽으로 정렬 된 개체를 반복 하 고 인덱싱할 수 있는 안전한 방법을 제공 `std::array` `std::vector` 합니다.

포인터와 인덱스를 사용 하 여 백 엔드 개체의 시퀀스에 일반적으로 액세스 하는 경우는 `span` 보다 안전 하 고 간단한 대안입니다.

의 크기는 `span` 컴파일 시간에 템플릿 인수로 지정 하거나를 지정 하 여 런타임에 설정할 수 있습니다 `dynamic_extent` .

## <a name="syntax"></a>구문

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>템플릿 매개 변수

`T`\
 범위에 있는 요소의 형식입니다.

`Extent`\
 컴파일 시간에 지정 된 경우 범위의 요소 수입니다. `std::dynamic_extent`런타임에 요소 수를 지정 하면이 고, 그렇지 않으면입니다.

[추론 가이드](#deduction_guides)

## <a name="members"></a>멤버

| **형식 정의** | **설명** |
|-|-|
| [const_pointer](#pointer) | 요소에 대 한 포인터의 형식 **`const`** 입니다. |
| [const_reference](#reference) | 요소에 대 한 참조의 형식 **`const`** 입니다. |
| [difference_type](#difference_type) | 두 요소 사이의 부호가 있는 거리의 형식입니다. |
| [element_type](#element_type) | Span 요소의 형식입니다. |
| [반복](#iterator) | 범위에 대 한 반복기의 형식입니다. |
| [놓고](#pointer) | 요소에 대한 포인터의 형식입니다. |
| [reference](#reference) | 요소에 대한 참조의 형식입니다. |
| [reverse_iterator](#reverse_iterator) | 범위에 대 한 역방향 반복기의 형식입니다. |
| [size_type](#size_type) | 범위에 있는 두 요소 간의 부호 없는 거리에 대 한 결과의 형식입니다. |
| [value_type](#value_type) | 또는 한정자가 없는 요소의 형식입니다 **`const`** **`volatile`** . |
| **생성자** | **설명** |
|[거칠](#span)| `span`을 생성합니다.|
| **반복기 지원** | **설명** |
|[시작](#begin) | 범위의 첫 번째 요소를 가리키는 반복기를 가져옵니다.|
|[종단](#end) | 범위의 끝을 가리키는 반복기를 가져옵니다. |
|[rbegin](#rbegin) | 범위의 마지막 요소를 가리키는 역방향 반복기를 가져옵니다. 즉, 역방향 범위의 시작 부분입니다.|
|[rend](#rend) | 범위의 앞을 가리키는 역방향 반복기를 가져옵니다. 즉, 역방향 범위의 끝입니다.|
| **액세스 요소**| **설명** |
|[뒤로](#back) | 범위의 마지막 요소를 가져옵니다.|
|[data](#data) | 범위에 있는 첫 번째 요소의 주소를 가져옵니다.|
|[앞뒤](#front) | 범위의 첫 번째 요소를 가져옵니다.|
|[연산자\[\]](#op_at) | 지정 된 위치에 있는 요소에 액세스 합니다.|
| **관찰자** | **설명** |
|[empty](#empty)| 범위가 비어 있는지 여부를 테스트 합니다.|
|[size](#size) | 범위에 있는 요소 수를 가져옵니다.|
|[size_bytes](#size_bytes) | 범위의 크기 (바이트)를 가져옵니다.|
| **하위 뷰** | **설명**|
| [first](#first_view) | 범위 앞에서 하위 범위를 가져옵니다.|
| [last](#last_view) | 범위 뒷면에서 하위 범위를 가져옵니다.|
| [하위 범위](#sub_view) | 범위 내 어디에서 나 하위 범위를 가져옵니다.|
| **연산자** | **설명** |
|[span:: operator =](#op_eq)| 범위를 바꿉니다.|
|[span:: operator\[\]](#op_at)| 지정 된 위치에 있는 요소를 가져옵니다. |

## <a name="remarks"></a>설명

모든 `span` 멤버 함수는 일정 한 시간 복잡성을 갖습니다.

또는와 달리 `array` `vector` 범위는 내부에서 요소를 "소유" 하지 않습니다. 범위는 해당 개체에 대 한 저장소를 소유 하지 않기 때문에 내 항목에 대 한 저장소를 해제 하지 않습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<span>

**네임스페이스:** std

**컴파일러 옵션:** [/std: c + + 최신](../build/reference/std-specify-language-standard-version.md)

## <a name="spanback"></a><a name="back"></a> `span::back`

범위의 마지막 요소를 가져옵니다.

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>반환 값

범위의 마지막 요소에 대 한 참조입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

범위의 첫 번째 요소를 가리키는 반복기를 가져옵니다.

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>반환 값

범위의 첫 번째 요소를 가리키는 반복기입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

범위 데이터의 시작 부분에 대 한 포인터를 가져옵니다.

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>반환 값

범위에 저장 된 첫 번째 항목에 대 한 포인터입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

범위에 있는 두 요소 사이의 요소 수입니다.

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

범위에 있는 요소의 형식입니다.

```cpp
using element_type = T;
```

### <a name="remarks"></a>설명

범위를 만들 때 템플릿 매개 변수에서 형식을 가져옵니다 `T` .

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

범위에 요소가 포함 되어 있는지 여부를 나타냅니다.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** 인 경우 `this->size() == 0` 을 반환 합니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

범위의 끝 부분에 대 한 반복기를 가져옵니다.

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 반복기입니다.

### <a name="remarks"></a>설명

`end`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

이 반복기에서 반환 된 값을 역참조 하지 않습니다. 이를 사용 하 여 반복기가 범위에서 마지막 요소를 넘어 도달 했는지 여부를 식별 합니다.

### <a name="example"></a>예제

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

이 범위의 앞에서 가져온 subspan을 가져옵니다.

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>매개 변수

*수*\
이 범위의 front에서 하위 범위에 넣을 요소의 수입니다.  
요소 수는 아래 그림과 같이 템플릿 또는 함수에 대 한 매개 변수로 지정 됩니다.

### <a name="return-value"></a>반환 값

이 범위 앞의 요소를 포함 하는 범위입니다 `count` .

### <a name="remarks"></a>설명

가능 하면 컴파일 시간에 대 한 유효성을 검사 하 고 범위에 대 한 정보를 유지 하기 위해이 함수의 템플릿 버전을 사용 `count` 합니다 .이는 고정 익스텐트의 범위를 반환 하기 때문입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

범위의 첫 번째 요소를 가져옵니다.

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>반환 값

범위의 첫 번째 요소에 대 한 참조입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

Span 요소에 대 한 반복기의 형식입니다.

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>설명

이 형식은 범위의 요소에 대 한 반복기 역할을 합니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

이 범위의 끝에서 가져온 subspan을 가져옵니다.

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>매개 변수

*수*\
이 범위가 하위 범위에 배치 되는 끝의 요소 수입니다.
이 번호는 아래 그림과 같이 템플릿 또는 함수에 대 한 매개 변수로 지정할 수 있습니다.

### <a name="return-value"></a>반환 값

이 범위에서 마지막 요소를 포함 하는 범위 `count` 입니다.

### <a name="remarks"></a>설명

가능 하면 컴파일 시간에 대 한 유효성을 검사 하 고 범위에 대 한 정보를 유지 하기 위해이 함수의 템플릿 버전을 사용 `count` 합니다 .이는 고정 익스텐트의 범위를 반환 하기 때문입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

범위에서 지정 된 위치에 있는 요소를 가져옵니다.

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>매개 변수

*이동*\
에 액세스할 범위에서 0부터 시작 하는 요소입니다.

### <a name="return-value"></a>반환 값

위치 *오프셋*에 있는 요소에 대 한 참조입니다. 위치가 잘못 된 경우 동작은 정의 되지 않습니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

이 항목에 다른 범위를 할당 합니다.

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>매개 변수

*다른*\
이 항목에 할당할 범위입니다.

### <a name="return-value"></a>반환 값

`*this`

### <a name="remarks"></a>설명

할당은 데이터 포인터와 크기의 단순 복사본을 만듭니다. 단순 복사는에서 `span` 포함 하는 요소에 대해 메모리를 할당 하지 않으므로 안전 합니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

범위 요소에 대 한 포인터 및 포인터의 형식입니다 **`const`** .

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

이 범위의 마지막 요소를 가리키는 역방향 반복기를 가져옵니다.

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 범위의 시작 부분을 가리키는 반복기입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

범위 요소에 대 한 참조 및 참조의 형식 **`const`** 입니다.

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

역방향 범위의 끝 바로 다음을 가리키는 임의 액세스 반복기를 가져옵니다.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 범위에서 마지막 요소 다음에 나오는 자리 표시자에 대 한 역방향 반복기입니다. 즉, 반전 된 범위에서 첫 번째 요소 앞의 자리 표시자입니다.

### <a name="remarks"></a>설명

`rend` 는 span [:: end](#end) 가 범위와 함께 사용 되는 것 처럼 역방향 범위에 사용 됩니다. 이를 사용 하 여 역방향 반복기가 범위 끝에 도달 했는지 여부를 테스트 합니다.

에서 반환 된 값은 `rend` 역참조 되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

범위에 대 한 역방향 반복기의 형식입니다.

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

범위에 있는 요소 수를 가져옵니다.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>반환 값

범위의 요소 수입니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

범위에 있는 요소의 크기 (바이트)를 가져옵니다.

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>반환 값

범위에 있는 모든 요소가 차지 하는 바이트 수입니다. 즉, `sizeof(element_type)` 범위의 요소 수를 곱합니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

범위에 있는 요소 수를 저장 하는 데 적합 한, 부호 없는 형식입니다.

```cpp
using size_type = size_t;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span` 생성자.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>매개 변수

*arr*\
배열에서 범위를 생성 합니다.

*수*\
범위에 있는 요소 수입니다.

*기본*\
범위의 첫 번째 요소에 대 한 반복기입니다.

*최신*\
범위에서 마지막 요소 바로 다음을 가리키는 반복기입니다.

*개의*\
범위에 있는 요소 수입니다.

*다른*\
이 범위의 복사본을 만듭니다.

*&*\
이 범위에서 범위를 생성 합니다.

### <a name="remarks"></a>설명

범위 내에 있는 개체의 저장소를 소유 하지 않기 때문에 범위에서 항목에 대 한 저장소를 해제 하지 않습니다.

|생성자  | Description  |
|---------|---------|
|`span()` | 빈 범위를 생성 합니다. 템플릿 매개 변수가 또는 인 경우에만 오버 로드 확인 중에만 고려 `Extent` 됩니다 `0` `dynamic_extent` .|
|`span(It first, size_type count)` | 반복기의 첫 번째 요소에서 범위를 생성 `count` `first` 합니다.  템플릿 매개 변수가이 아닌 경우 오버 로드 확인 중에만 고려 `Extent` `dynamic_extent` 됩니다. |
|`span(It first, End last)` | 끝에 도달할 때까지 반복기의 요소에서 범위를 생성 `first` `last` 합니다. 템플릿 매개 변수가이 아닌 경우 오버 로드 확인 중에만 고려 `Extent` `dynamic_extent` 됩니다. `It` 이어야 합니다 `contiguous_iterator` .  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  `N`지정 된 배열의 요소에서 범위를 생성 합니다. 템플릿 매개 변수가 이거나 같으면 오버 로드 확인 중에만 고려 됩니다 `Extent` `dynamic_extent` `N` . |
|`span(R&& r)` |  범위에서 범위를 생성 합니다. 템플릿 매개 변수가이 아닌 경우에만 오버 로드 확인에 참여 `Extent` `dynamic_extent` 합니다.|
|`span(const span& other)` |  컴파일러에서 생성 된 복사 생성자입니다. 범위가 요소를 보유 하기 위해 메모리를 할당 하지 않으므로 데이터 포인터의 단순 복사본은 안전 합니다. |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | 생성자 변환: 다른 범위에서 범위를 구성 합니다. 템플릿 매개 변수가 이거나 이거나 인 경우에만 오버 로드 확인에 참여 `Extent` `dynamic_extent` `N` `dynamic_extent` `Extent` 합니다.|

### <a name="example"></a>예제

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

이 범위의 subspan을 가져옵니다.

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>매개 변수

*수*\
Subspan에 넣을 요소의 수입니다. `count`가 `dynamic_extent` (기본값) 이면에서 `offset` 이 범위의 끝까지 하위 범위를 가져옵니다.

*이동*\
이 범위에서 하위 범위를 시작할 위치입니다.

### <a name="return-value"></a>반환 값

이 범위의에서 시작 하는 범위 `offset` 입니다. `count`요소를 포함 합니다.

### <a name="remarks"></a>설명

이 함수의 템플릿 버전은 컴파일 시간에 개수를 확인 하는 데 사용할 수 있으며,이는 고정 익스텐트의 범위를 반환 하 여 범위에 대 한 정보를 유지 합니다.

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

범위 내에서 또는 한정자가 없는 요소의 형식입니다 **`const`** **`volatile`** .

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>예제

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a> 추론 가이드

다음 추론 가이드는 범위에 대해 제공 됩니다.

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>참고 항목

[\<span>](../standard-library/span.md)  
[클래스 템플릿 인수 추론을 사용 하는 방법](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
