---
description: '자세히 알아보기: deque 클래스'
title: deque 클래스
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: f46c3c31dd23f7603a1d4ef6289e435c9b38e823
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324577"
---
# <a name="deque-class"></a>deque 클래스

선형 정렬에서 지정된 형식의 요소를 정렬하고 벡터처럼 모든 요소에 대한 빠른 임의 액세스와 컨테이너 뒤쪽에서 효율적인 삽입 및 삭제를 가능하게 합니다. 그러나 벡터와 달리 `deque` 클래스는 컨테이너 앞에서 효율적인 삽입 및 삭제를 지원합니다.

## <a name="syntax"></a>구문

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>매개 변수

*입력할*\
deque에 저장되는 요소 데이터 형식입니다.

*할당자*\
deque의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 **할당자 \<Type>** 입니다.

## <a name="remarks"></a>설명

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 요소에 대 한 임의 액세스는 프리미엄이 고 요소 삽입 또는 삭제는 시퀀스의 끝 에서만 수행 하면 되는 시퀀스를 관리 하려면 [벡터](../standard-library/vector-class.md) 를 기본 컨테이너로 사용 해야 합니다. 시퀀스 내의 모든 위치에서 효율적인 삽입 및 삭제(일정한 시간)가 최상일 때 목록 컨테이너의 성능이 가장 우수합니다. 시퀀스 중 이러한 작업에는 시퀀스의 요소 수에 비례하는 요소 복사본 및 할당이 필요합니다(선형 시간).

멤버 함수가 시퀀스의 요소를 삽입하거나 지워야 하면 deque 다시 할당이 수행됩니다.

- 빈 시퀀스에 요소를 삽입하거나 요소를 지워 빈 시퀀스가 남는 경우 [begin](#begin) 및 [end](#end)에서 이전에 반환된 반복기가 무효화됩니다.

- deque의 첫 번째 위치에 요소를 삽입하는 경우 기존 요소를 지정하는 모든 반복기가 무효화되지만 참조는 그렇지 않습니다.

- deque의 끝에 요소를 삽입하는 경우 [end](#end) 및 기존 요소를 지정하는 모든 반복기가 무효화되지만 참조는 그렇지 않습니다.

- deque 앞에서 요소를 지우는 경우 해당 반복기와 지워진 요소에 대한 참조만 무효화됩니다.

- deque의 끝에서 마지막 요소를 지우는 경우 최종 요소에 대한 해당 반복기와 지워진 요소에 대한 참조만 무효화됩니다.

그렇지 않으면 요소를 삽입 또는 제거하는 경우 모든 반복기와 참조가 무효화됩니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[deque](#deque)|`deque`를 생성합니다. `deque`비어 있는, 지정 된 개수의 빈 요소를 사용 하 여 로드, 다른 위치에서 콘텐츠 이동 또는 복사, `deque` 반복기를 사용 하 여 콘텐츠 복사 또는 이동, 한 요소를 `deque` `count` 시간으로 복사 하는 등의 여러 가지 방법으로 새의 콘텐츠를 설정 하기 위해 여러 생성자가 제공 됩니다. 일부 생성자의 경우 사용자 지정 `allocator`를 사용하여 요소를 만들 수 있습니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `deque` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|의 요소를로 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다. `deque`**`const`**|
|[const_pointer](#const_pointer)|`deque`의 요소에 대한 포인터를 `const.`로 제공하는 형식입니다.|
|[const_reference](#const_reference)|읽기 및 기타 작업을 위해 `deque`의 요소에 대한 참조를 `const.`로 제공하는 형식입니다.|
|[const_reverse_iterator](#const_reverse_iterator)|의 요소를로 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 `deque` **`const`** . deque가 역방향으로 표시됩니다. 자세한 내용은 [reverse_iterator 클래스](../standard-library/reverse-iterator-class.md)를 참조하세요.|
|[difference_type](#difference_type)|동일한 `deque` 내의 요소를 참조하는 두 임의 액세스 반복기 간의 차이를 제공하는 형식입니다.|
|[iterator](#iterator)|`deque`에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.|
|[놓고](#pointer)|`deque`의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`deque` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|`deque`에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다. deque가 역방향으로 표시됩니다.|
|[size_type](#size_type)|`deque`의 요소 수를 계산하는 형식입니다.|
|[value_type](#value_type)|`deque` 내에 저장된 데이터 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[assign](#assign)|`deque`에서 요소를 지우고 대상 `deque`에 요소의 새 시퀀스를 복사합니다.|
|[at](#at)|`deque`의 지정된 위치에 있는 요소에 대한 참조를 반환합니다.|
|[뒤로](#back)|`deque`의 마지막 요소에 대한 참조를 반환합니다.|
|[시작](#begin)|`deque`의 첫 번째 요소를 처리하는 임의 액세스 반복기를 반환합니다.|
|[cbegin](#cbegin)|`deque`의 첫 번째 요소에 대해 const 반복기를 반환합니다.|
|[cend](#cend)|끝의 바로 다음을 가리키는 임의 액세스 반복기를 반환 합니다 **`const`** `deque` .|
|[clear](#clear)|`deque`의 모든 요소를 지웁니다.|
|[crbegin](#crbegin)|역방향으로 표시된 `deque`의 첫 번째 요소에 대한 임의 액세스 const 반복기를 반환합니다.|
|[crend](#crend)|역방향으로 표시된 `deque`의 첫 번째 요소에 대한 임의 액세스 const 반복기를 반환합니다.|
|[emplace](#emplace)|내부에서 생성된 요소를 `deque`의 지정된 위치에 삽입합니다.|
|[emplace_back](#emplace_back)|생성된 요소를 `deque`의 끝에 추가합니다.|
|[emplace_front](#emplace_front)|생성된 요소를 `deque`의 시작 부분에 추가합니다.|
|[empty](#empty)|**`true`** 에 `deque` 요소가 포함 되어 있지 않으면이 고, **`false`** 하나 이상의 요소가 포함 된 경우를 반환 합니다.|
|[end](#end)|`deque` 끝의 바로 다음을 가리키는 임의 액세스 반복기를 반환합니다.|
|[erase](#erase)|`deque`의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.|
|[앞뒤](#front)|`deque`의 첫 번째 요소에 대한 참조를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`를 생성하는 데 사용된 `deque` 개체의 복사본을 반환합니다.|
|[insert](#insert)|한 요소, 여러 요소 또는 요소의 범위를 `deque`의 지정된 위치에 삽입합니다.|
|[max_size](#max_size)|`deque`의 최대 허용 길이를 반환합니다.|
|[pop_back](#pop_back)|`deque`의 끝에 있는 요소를 지웁니다.|
|[pop_front](#pop_front)|`deque`의 시작 부분에 있는 요소를 지웁니다.|
|[push_back](#push_back)|`deque`의 끝에 요소를 추가합니다.|
|[push_front](#push_front)|`deque`의 시작 부분에 요소를 추가합니다.|
|[rbegin](#rbegin)|역방향 `deque`의 첫 번째 요소에 대한 임의 액세스 반복기를 반환합니다.|
|[rend](#rend)|역방향 `deque`에서 마지막 요소 바로 다음을 가리키는 임의 액세스 반복기를 반환합니다.|
|[조정해](#resize)|`deque`의 새 크기를 지정합니다.|
|[shrink_to_fit](#shrink_to_fit)|여분의 용량을 삭제합니다.|
|[size](#size)|`deque`에 있는 요소 수를 반환합니다.|
|[스왑을](#swap)|두 `deque`의 요소를 교환합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[operator&#91;&#93;](#op_at)|지정된 위치에 있는 `deque` 요소에 대한 참조를 반환합니다.|
|[연산자 =](#op_eq)|`deque`의 요소를 다른 `deque`의 복사본으로 바꿉니다.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

deque 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type`는 템플릿 매개 변수 `Allocator`의 동의어입니다.

### <a name="example"></a>예제

[get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="assign"></a><a name="assign"></a> 할당

deque에서 요소를 삭제하고 대상 deque에 요소의 새 집합을 복사합니다.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>매개 변수

*기본*\
인수 deque에서 복사할 요소 범위에 있는 첫 번째 요소의 위치입니다.

*최신*\
인수 deque에서 복사할 요소 범위를 벗어난 첫 번째 요소의 위치입니다.

*수*\
deque에 삽입되는 요소의 복사본의 수입니다.

*짧은*\
deque에 삽입되는 요소의 값입니다.

*IList*\
deque에 삽입되는 initializer_list입니다.

### <a name="remarks"></a>설명

대상 deque에서 기존 요소가 지워진 후 `assign`은 원래 deque나 일부 다른 deque에서 지정된 범위의 요소를 대상 deque에 삽입하거나, 지정한 값의 새 요소 복사본을 대상 deque에 삽입합니다.

### <a name="example"></a>예제

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a><a name="at"></a> 속도

deque의 지정된 위치에 있는 요소에 대한 참조를 반환합니다.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>매개 변수

*pos*\
deque에서 참조할 요소의 아래 첨자 또는 위치 번호입니다.

### <a name="return-value"></a>반환 값

*Pos* 가 deque의 크기 보다 큰 경우는 예외를 `at` throw 합니다.

### <a name="return-value"></a>반환 값

`at`의 반환 값이 `const_reference`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `at`의 반환 값이 `reference`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> 뒤로

deque의 마지막 요소에 대한 참조를 반환합니다.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>반환 값

deque의 마지막 요소입니다. deque가 비어 있으면 반환 값이 정의 해제됩니다.

### <a name="remarks"></a>설명

`back`의 반환 값이 `const_reference`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `back`의 반환 값이 `reference`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 deque의 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> begin

deque의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>반환 값

deque의 첫 번째 요소 또는 빈 deque 다음의 위치 주소를 지정하는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`begin`의 반환 값이 `const_iterator`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. 의 반환 값 `begin` 이에 할당 된 경우 `iterator` deque 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 임의 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

**`const`** 범위에서 마지막 요소 바로 다음 위치의 주소를 가리키는 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `end()` `cend()` 합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="clear"></a><a name="clear"></a> 해제

deque의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Deque의 요소를 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

[back](#back)의 예제를 참조하세요.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Deque의 요소에 대 한 포인터를 제공 **`const`** 합니다.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다. [iterator](#iterator)는 deque 요소에 액세스하는 데 사용되는 경우가 더 많습니다.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

**`const`** 작업을 읽고 수행 하기 위해 deque에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>설명

`const_reference` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Deque의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 deque를 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

반복기를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

역방향 deque의 첫 번째 요소에 대해 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [deque](../standard-library/deque-class.md)에서 첫 번째 요소의 주소를 지정하거나 역방향이 해제된 `deque`에서 마지막 요소의 주소를 지정하는 const 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

반환 값이 `crbegin`이면 `deque` 개체를 수정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

역방향 deque에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [deque](../standard-library/deque-class.md)에서 마지막 요소 다음의 위치(역방향이 해제된 deque의 첫 번째 요소 앞의 위치) 주소를 지정하는 const 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 [array::cend](../standard-library/array-class-stl.md#cend)가 `deque`에 사용되는 것처럼 역방향 `deque`에 사용됩니다.

반환 값이 `crend`(적절하게 감소)인 `deque` 개체는 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 deque 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a><a name="deque"></a> deque

특정 크기의 deque 또는 특정 값의 요소나 특정 할당자가 포함된 목록을 다른 deque 일부 또는 전체의 복사본으로 생성합니다.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 개체에 사용할 할당자 클래스입니다.

*수*\
생성된 deque에 있는 요소의 수입니다.

*짧은*\
생성된 deque에 있는 요소의 값입니다.

*오른쪽*\
생성된 deque가 복사본으로 지정될 deque입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어난 첫 번째 요소의 위치입니다.

*IList*\
복사할 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체 (*Al*)를 저장 하 고 deque를 초기화 합니다.

처음 두 생성자는 빈 초기 deque를 지정 합니다. 또한 두 번째는 사용할 할당자 형식 ()을 지정 합니다 `_Al` .

세 번째 생성자는 `count` 클래스에 대한 기본값 요소의 지정된 반복 횟수(`Type`)를 지정합니다.

네 번째 및 다섯 번째 생성자는 값의 요소 반복 (*개수*)을 지정 합니다 `val` .

여섯 번째 생성자는 deque *Right* 의 복사본을 지정 합니다.

일곱 번째 및 여덟 번째 생성자는 deque의 범위 `[First, Last)`를 복사합니다.

일곱 번째 생성자는 deque을 *오른쪽* 으로 이동 합니다.

여덟 번째 생성자는 initializer_list의 콘텐츠를 복사합니다.

중간 다시 할당을 수행하는 생성자는 없습니다.

### <a name="example"></a>예제

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

동일한 deque 내의 요소를 참조하는 두 반복기 사이의 차이를 제공하는 형식입니다.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 두 포인터 사이의 요소로도 설명할 수 있습니다.

### <a name="example"></a>예제

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

내부에서 생성된 요소를 deque의 지정된 위치에 삽입합니다.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>매개 변수

*_Where*\
[deque](../standard-library/deque-class.md)에서 첫 번째 요소를 삽입하는 위치입니다.

*짧은*\
`deque`에 삽입되는 요소의 값입니다.

### <a name="return-value"></a>반환 값

이 함수는 새 요소를 deque에 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

모든 삽입 작업에서는 많은 계산을 수행해야 할 수 있습니다. `deque` 성능에 대한 설명은 `deque`를 참조하세요.

### <a name="example"></a>예제

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

내부에서 생성된 요소를 deque의 끝에 추가합니다.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
[deque](../standard-library/deque-class.md) 끝에 추가되는 요소입니다.

### <a name="example"></a>예제

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

내부에서 생성된 요소를 deque의 끝에 추가합니다.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
[Deque](../standard-library/deque-class.md)의 시작 부분에 추가 되는 요소입니다.

### <a name="example"></a>예제

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a><a name="empty"></a> 비우려면

deque가 비어 있는지 여부를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** deque이 비어 있으면이 고, 그렇지 않으면입니다. **`false`** deque이 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a><a name="end"></a> end

deque에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

deque에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 임의 액세스 반복기입니다. deque가 비어 있으면 deque::end == deque::begin입니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 deque의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다.

### <a name="example"></a>예제

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> 지우는

deque의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>매개 변수

*_Where*\
deque에서 제거할 요소의 위치입니다.

*기본*\
deque에서 제거되는 첫 번째 요소의 위치입니다.

*최신*\
deque에서 제거되는 마지막 요소 바로 뒤의 위치입니다.

### <a name="return-value"></a>반환 값

제거되는 요소 뒤에 남아 있는 첫 번째 요소를 지정하는 임의 액세스 반복기이거나, 남아 있는 요소가 없는 경우에는 deque 끝에 대한 포인터입니다.

### <a name="remarks"></a>설명

`erase`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a><a name="front"></a> 앞뒤

deque의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>반환 값

deque가 비어 있으면 반환이 정의 해제됩니다.

### <a name="remarks"></a>설명

`front`의 반환 값이 `const_reference`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `front`의 반환 값이 `reference`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 deque의 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

deque를 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

deque에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

deque 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> 넣거나

요소 하나 또는 여러 개나 요소의 범위를 deque의 지정된 위치에 삽입합니다.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 deque에서 첫 번째 요소를 삽입하는 위치입니다.

*짧은*\
deque에 삽입되는 요소의 값입니다.

*수*\
deque에 삽입되는 요소의 수입니다.

*기본*\
인수 deque에서 복사할 요소 범위에 있는 첫 번째 요소의 위치입니다.

*최신*\
인수 deque에서 복사할 요소 범위를 벗어난 첫 번째 요소의 위치입니다.

*IList*\
삽입할 요소의 initializer_list입니다.

### <a name="return-value"></a>반환 값

처음 두 insert 함수는 새 요소가 deque에 삽입된 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

모든 삽입 작업에서는 많은 계산을 수행해야 할 수 있습니다.

## <a name="iterator"></a><a name="iterator"></a> 반복

deque에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

[begin](#begin)의 예제를 참조하세요.

## <a name="max_size"></a><a name="max_size"></a> max_size

deque의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

deque의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> operator[]

지정된 위치에 있는 deque 요소에 대한 참조를 반환합니다.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>매개 변수

*pos*\
참조할 deque 요소의 위치입니다.

### <a name="return-value"></a>반환 값

인수에 해당 위치가 지정된 요소에 대한 참조입니다. 지정된 위치가 deque의 크기보다 클 경우 결과가 정의 해제됩니다.

### <a name="remarks"></a>설명

`operator[]`의 반환 값이 `const_reference`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `operator[]`의 반환 값이 `reference`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 deque 범위를 벗어난 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

다른 deque의 요소를 사용하여 이 deque의 요소를 대체합니다.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
새 콘텐츠를 제공하는 deque입니다.

### <a name="remarks"></a>설명

첫 번째 재정의는 할당의 원본인이 deque에 *요소를 복사* 합니다. 두 번째 재정의는 요소를이 deque *오른쪽* 으로 이동 합니다.

연산자가 실행되기 전에 이 deque에 포함된 요소는 제거됩니다.

### <a name="example"></a>예제

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a><a name="pointer"></a> 포인터

[deque](../standard-library/deque-class.md)에 있는 요소에 대한 포인터를 제공합니다.

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다. [iterator](#iterator)는 deque 요소에 액세스하는 데 사용되는 경우가 더 많습니다.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

deque의 끝에 있는 요소를 삭제합니다.

```cpp
void pop_back();
```

### <a name="remarks"></a>설명

마지막 요소는 비워 둘 수 없습니다. `pop_back`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

deque의 시작 부분에 있는 요소를 삭제합니다.

```cpp
void pop_front();
```

### <a name="remarks"></a>설명

첫 번째 요소는 비워 둘 수 없습니다. `pop_front`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

deque 끝에 요소를 추가합니다.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
deque 끝에 추가되는 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 deque는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

## <a name="push_front"></a><a name="push_front"></a> push_front

deque의 시작 부분에 요소를 추가합니다.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
deque의 시작 부분에 추가할 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 deque는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

역방향 deque의 첫 번째 요소에 대한 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 deque에서 첫 번째 요소의 주소를 지정하거나 역방향이 해제된 deque에서 마지막 요소의 주소를 지정하는 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 deque에서 [begin](#begin)이 사용되는 것처럼 역방향 deque에 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

`rbegin`은 deque를 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a><a name="reference"></a> 참조일

deque에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>예제

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a><a name="rend"></a> rend

역방향 deque에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 deque에서 마지막 요소 다음의 위치(역방향이 해제된 deque의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 deque에서 [end](#end)가 사용되는 것처럼 역방향 deque에 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당되는 경우에는 deque 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 deque 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 deque 끝에 도달했는지 여부를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> 조정해

deque의 새 크기를 지정합니다.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>매개 변수

*_Newsize*\
deque의 새 크기입니다.

*짧은*\
새 크기가 원래 크기보다 클 경우 deque에 추가되는 새 요소의 값입니다. 값을 생략하면 새 요소에 클래스의 기본값이 할당됩니다.

### <a name="remarks"></a>설명

Deque의 크기가 요청 된 *_Newsize* 크기 보다 작은 경우에는 요청한 크기에 도달할 때까지 deque에 요소가 추가 됩니다.

Deque의 크기가 요청 된 크기 보다 크면 deque가 *_Newsize* 크기에 도달할 때까지 deque의 끝에 가장 가까운 요소가 삭제 됩니다.

deque의 현재 크기와 요청된 크기가 동일하면 아무런 작업도 실행되지 않습니다.

[크기](#size)는 deque의 현재 크기를 반영합니다.

### <a name="example"></a>예제

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

역방향 deque에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 deque를 반복하는 데 사용됩니다.

### <a name="example"></a>예제

rbegin의 예제를 참조하세요.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

여분의 용량을 삭제합니다.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>설명

`shrink_to_fit`가 [deque](../standard-library/deque-class.md)에서 사용되는 스토리지를 줄이는지 확인하는 간편한 방법은 없습니다.

### <a name="example"></a>예제

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a><a name="size"></a> 크기가

deque의 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

deque의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

deque의 요소 수를 계산하는 형식입니다.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>예제

[size](#size)의 예제를 참조하세요.

## <a name="swap"></a><a name="swap"></a> 스왑을

두 deque의 요소를 교환합니다.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공하는 deque 또는 `left` deque와 요소를 교환할 deque입니다.

*비어*\
Deque *right* 의 요소와 교환할 요소를 포함 하는 deque입니다.

### <a name="example"></a>예제

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

deque에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>설명

`value_type`는 템플릿 매개 변수 `Type`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
