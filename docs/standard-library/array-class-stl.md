---
title: array 클래스(C++ 표준 라이브러리)| Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
dev_langs:
- C++
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c52a68e87e29aaa827a61e657e04364acf6205b4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318793"
---
# <a name="array-class-c-standard-library"></a>array 클래스(C++ 표준 라이브러리)

길이가 `N`인 `Ty` 형식의 요소 시퀀스를 제어하는 개체를 설명합니다. 시퀀스는 `array<Ty, N>` 개체에 포함된 `Ty`의 배열로 저장됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|`Ty`|요소의 형식입니다.|
|`N`|요소의 수입니다.|

## <a name="members"></a>멤버

|형식 정의|설명|
|-|-|
|[const_iterator](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[const_pointer](#const_pointer)|요소에 대한 상수 포인터의 형식입니다.|
|[const_reference](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[const_reverse_iterator](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|
|[difference_type](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[iterator](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[pointer](#pointer)|요소에 대한 포인터의 형식입니다.|
|[reference](#reference)|요소에 대한 참조의 형식입니다.|
|[reverse_iterator](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|
|[size_type](#size_type)|두 요소 사이의 부호가 없는 거리의 형식입니다.|
|[value_type](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|-|-|
|[array](#array)|배열 개체를 생성합니다.|
|[assign](#assign)|모든 요소를 바꿉니다.|
|[at](#at)|지정된 위치에 있는 요소에 액세스합니다.|
|[back](#back)|마지막 요소에 액세스합니다.|
|[begin](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[cbegin](#cbegin)|배열의 첫 번째 요소에 대한 임의 액세스 const 반복기를 반환합니다.|
|[cend](#cend)|배열 끝의 바로 다음을 가리키는 임의 액세스 const 반복기를 반환합니다.|
|[crbegin](#crbegin)|역방향 배열의 첫 번째 요소에 대해 const 반복기를 반환합니다.|
|[crend](#crend)|역방향 배열 끝에 대해 const 반복기를 반환합니다.|
|[data](#data)|첫 번째 요소의 주소를 가져옵니다.|
|[empty](#empty)|요소가 있는지 테스트합니다.|
|[end](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[fill](#fill)|지정된 값을 가진 모든 요소를 바꿉니다.|
|[front](#front)|첫 번째 요소에 액세스합니다.|
|[max_size](#max_size)|요소 수를 계산합니다.|
|[rbegin](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|
|[rend](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|
|[size](#size)|요소 수를 계산합니다.|
|[swap](#swap)|두 컨테이너의 내용을 바꿉니다.|

|연산자|설명|
|-|-|
|[array::operator=](#op_eq)|제어되는 시퀀스를 바꿉니다.|
|[array::operator[]](#op_at)|지정된 위치에 있는 요소에 액세스합니다.|

## <a name="remarks"></a>설명

형식에 기본 생성자 `array()`와 기본 대입 연산자 `operator=`가 있고 `aggregate`에 대한 요구 사항을 충족합니다. 따라서 집계 이니셜라이저를 사용하여 `array<Ty, N>` 형식의 개체를 초기화할 수 있습니다. 예를 들어 개체에 적용된

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

4개의 정수 값을 보유하는 `ai` 개체를 만들고, 처음 세 개의 요소를 값 1, 2, 3으로 각각 초기화한 다음 네 번째 요소를 0으로 초기화합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<array>

**네임스페이스:** std

## <a name="array"></a>  array::array

배열 개체를 생성합니다.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>매개 변수

*right*<br/>
삽입할 개체 또는 범위입니다.

### <a name="remarks"></a>설명

기본 생성자 `array()`는 제어되는 시퀀스를 초기화되지 않은 상태(또는 기본 시퀀스를 초기화된 상태)로 유지합니다. 초기화되지 않은 제어되는 시퀀스를 지정하려면 이 생성자를 사용합니다.

복사 생성자 `array(const array& right)`는 시퀀스 [*right*`.begin()`, *right*`.end()`)로 제어되는 시퀀스를 초기화합니다. 배열 개체 *right*에 의해 제어되는 시퀀스의 복사본인 초기의 제어되는 시퀀스를 지정하려면 이 생성자를 사용합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_array.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1(c0);

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="assign"></a>  array::assign

C++11에서는 사용되지 않으며, [fill](#fill)로 대체되었습니다. 모든 요소를 바꿉니다.

```cpp
void assign(const Ty& val);
```

### <a name="parameters"></a>매개 변수

*val*<br/>
할당할 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 하는 시퀀스를 바꿉니다 `*this` 반복을 사용 하 여 `N` 값의 요소나 *val*합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_assign.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1.assign(4);

// display contents " 4 4 4 4"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4 4 4 4
```

## <a name="at"></a>  array::at

지정된 위치에 있는 요소에 액세스합니다.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>매개 변수

*해제*<br/>
액세스할 요소의 위치입니다.

### <a name="remarks"></a>설명

멤버 함수는 위치에서 제어 된 시퀀스의 요소에 대 한 참조를 반환 *해제*합니다. 해당 위치가 잘못된 경우 함수는 `out_of_range` 클래스의 개체를 throw합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_at.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
    }

```

## <a name="back"></a>  array::back

마지막 요소에 액세스합니다.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어된 시퀀스의 마지막 요소에 대한 참조를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_back.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="begin"></a>  array::begin

제어되는 시퀀스의 시작을 지정합니다.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>설명

멤버 함수는 시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 임의 액세스 반복기를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_begin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="cbegin"></a>  array::cbegin

반환 된 **const** 반복기 범위에서 첫 번째 요소를 주소입니다.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>반환 값

A **상수** 범위 또는 빈 범위의 끝 바로 다음 위치 중 첫 번째 요소를 가리키는 임의 액세스 반복기 (빈 범위의 경우 `cbegin() == cend()`).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 예에서 고려 `Container` 수정 되도록 (비 **const**)를 지 원하는 모든 종류의 컨테이너 `begin()` 및 `cbegin()`합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  array::cend

반환 된 **const** 반복기 범위에서 마지막 요소 바로 다음 위치를 주소입니다.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 예에서 고려 `Container` 수정 되도록 (비 **const**)를 지 원하는 모든 종류의 컨테이너 `end()` 및 `cend()`합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="const_iterator"></a>  array::const_iterator

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

형식은 제어되는 시퀀스의 상수 임의 액세스 반복기로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_const_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::const_iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="const_pointer"></a>  array::const_pointer

요소에 대한 상수 포인터의 형식입니다.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>설명

이 형식은 시퀀스의 요소에 대한 상수 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_const_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reference"></a>  array::const_reference

요소에 대한 상수 참조의 형식입니다.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 상수 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_const_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reverse_iterator"></a>  array::const_reverse_iterator

제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 상수 역방향 반복기로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_const_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="crbegin"></a>  array::crbegin

역방향 배열의 첫 번째 요소에 대해 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 배열에서 첫 번째 요소의 주소를 지정하거나 정방향 배열에서 마지막 요소의 주소를 지정하는 const 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

반환 값이 `crbegin`인 배열 개체는 수정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// array_crbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="crend"></a>  array::crend

역방향 배열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 배열에서 마지막 요소 다음의 위치(역방향이 해제된 배열의 첫 번째 요소 앞의 위치) 주소를 지정하는 const 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 배열에서 [array::cend](#cend)가 사용되는 것처럼 역방향 배열에 사용됩니다.

반환 값이 `crend`(적절하게 감소)인 배열 개체는 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 배열 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// array_crend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>  array::data

첫 번째 요소의 주소를 가져옵니다.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스에서 첫 번째 요소의 주소를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_data.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="difference_type"></a>  array::difference_type

두 요소 사이의 부호가 있는 거리의 형식입니다.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>설명

부호 있는 정수 형식은 제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다. 이 형식은 `std::ptrdiff_t` 형식의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__array__array_difference_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
-4
```

## <a name="empty"></a>  array::empty

요소가 있는지 여부를 테스트합니다.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `N == 0`인 경우에만 true를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_empty.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

// display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
false
true
```

## <a name="end"></a>  array::end

제어되는 시퀀스의 끝을 지정합니다.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>설명

멤버 함수는 시퀀스 끝의 바로 다음을 가리키는 임의 액세스 반복기를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_end.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="fill"></a>  array::fill

배열을 삭제하고 지정된 요소를 빈 배열에 복사합니다.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|*val*|배열에 삽입되는 요소의 값입니다.|

### <a name="remarks"></a>설명

`fill`은 배열의 각 요소를 지정된 값으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// array_fill.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator iter;

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v1.fill(3);
   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="front"></a>  array::front

첫 번째 요소에 액세스합니다.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어된 시퀀스의 첫 번째 요소에 대한 참조를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_front.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="iterator"></a>  array::iterator

제어되는 시퀀스에 대한 반복기의 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 임의 액세스 반복기로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3

it2: 0

```

## <a name="max_size"></a>  array::max_size

요소 수를 계산합니다.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `N`를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_max_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="op_at"></a>  array::operator[]

지정된 위치에 있는 요소에 액세스합니다.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>매개 변수

*해제*<br/>
액세스할 요소의 위치입니다.

### <a name="remarks"></a>설명

멤버 함수는 위치에서 제어 된 시퀀스의 요소에 대 한 참조를 반환 *해제*합니다. 해당 위치가 유효하지 않을 경우 동작이 정의되지 않습니다.

비 멤버 이기도 [가져옵니다](array-functions.md#get) 요소에 대 한 참조를 가져올 수 있는 함수는 **배열**합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_operator_sub.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
1 3
```

## <a name="op_eq"></a>  array::operator=

제어되는 시퀀스를 바꿉니다.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>매개 변수

*right*<br/>
복사할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 연산자의 각 요소를 할당 *오른쪽* 제어 된 시퀀스의 해당 요소를 반환 `*this`합니다. 제어 되는 시퀀스에서 제어 된 시퀀스의 복사본으로 대체 하는 데 사용할 있습니다 *오른쪽*합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_operator_as.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

// display copied contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="pointer"></a>  array::pointer

요소에 대한 포인터의 형식입니다.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>설명

이 형식은 시퀀스의 요소에 대한 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rbegin"></a>  array::rbegin

제어되는 역방향 시퀀스의 시작을 지정합니다.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스 끝의 바로 다음을 가리키는 역방향 반복기를 반환합니다. 따라서 역방향 시퀀스의 시작을 지정합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_rbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="reference"></a>  array::reference

요소에 대한 참조의 형식입니다.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rend"></a>  array::rend

제어되는 역방향 시퀀스의 끝을 지정합니다.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>설명

멤버 함수는 시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 역방향 반복기를 반환합니다. 따라서 역방향 시퀀스의 끝을 지정합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_rend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="reverse_iterator"></a>  array::reverse_iterator

제어되는 시퀀스에 대한 반대 반복기의 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 역방향 반복기로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="size"></a>  array::size

요소 수를 계산합니다.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `N`를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__array__array_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="size_type"></a>  array::size_type

두 요소 사이의 부호가 없는 거리의 형식입니다.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>설명

부호 없는 정수 형식은 제어되는 시퀀스의 길이를 나타낼 수 있는 개체를 설명합니다. 이 형식은 `std::size_t` 형식의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__array__array_size_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="swap"></a>  array::swap

이 배열의 내용을 다른 배열과 교환합니다.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>매개 변수

*right*<br/>
내용을 교환할 배열입니다.

### <a name="remarks"></a>설명

멤버 함수 간에 제어 된 시퀀스를 교환 `*this` 하 고 *오른쪽*합니다. `N`에 비례하여 많은 요소 할당과 생성자 호출을 수행합니다.

비 멤버 이기도 [스왑](array-functions.md#swap) 두 교환 하는 데 사용할 수 있는 함수가 **배열** 인스턴스.

### <a name="example"></a>예제

```cpp
// std__array__array_swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};
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

## <a name="value_type"></a>  array::value_type

요소의 형식입니다.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Ty`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__array__array_value_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        {
        Myarray::value_type val = *it;
        std::cout << " " << val;
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>참고자료

[\<array>](../standard-library/array.md)<br/>
