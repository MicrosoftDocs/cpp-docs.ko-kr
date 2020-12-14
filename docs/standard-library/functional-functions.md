---
description: '자세한 정보: &lt; &gt; 함수 함수'
title: '&lt;functional&gt; 함수'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
ms.openlocfilehash: f3ae9fca75801555c0341923d0fc42db94546cd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232163"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; 함수

이러한 함수는 c + + 11에서 더 이상 사용 되지 않으며 c + + 17에서 제거 되었습니다.

[bind1st](#bind1st)\
[bind2nd](#bind2nd)\
[mem_fun](#mem_fun)\
[mem_fun_ref](#mem_fun_ref)\
[ptr_fun](#ptr_fun)

이러한 함수는 c + + 17에서 더 이상 사용 되지 않습니다.

[not1](#not1)\
[not2](#not2)

## <a name="bind"></a><a name="bind"></a> 바인딩하며

호출 가능 개체에 인수를 바인딩합니다.

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>매개 변수

*Fey*\
호출할 개체의 형식입니다.

*TN*\
N번째 인수의 형식입니다.

*fn*\
호출할 개체입니다.

*tN*\
N번째 호출 인수입니다.

### <a name="remarks"></a>설명

형식은 생성 가능 이어야 하며 `FT, T1, T2, ..., TN` `INVOKE(fn, t1, ..., tN)` 일부 값에 대해 유효한 식 이어야 합니다 `w1, w2, ..., wN` .

첫 번째 템플릿 함수는 약한 결과 형식이 포함된 전달 호출 래퍼 `g`를 반환합니다. 의 효과는 `g(u1, u2, ..., uM)` `INVOKE(f, v1, v2, ..., vN,` [invoke_result](../standard-library/invoke-result-class.md)입니다 `<FT cv (V1, V2, ..., VN)>::type)` . 여기서 `cv` 는의 cv 한정자이 `g` 고 바인딩된 인수의 값과 형식은 `v1, v2, ..., vN` 아래 지정 된 대로 결정 됩니다. 이를 사용하여 인수를 호출 가능 개체에 바인딩하면 맞춤형 인수 목록이 포함된 호출 가능 개체가 생성됩니다.

두 번째 템플릿 함수는 `RTy`의 동의어인 중첩된 형식 `result_type`이 포함된 전달 호출 래퍼 `g`를 반환합니다. `g(u1, u2, ..., uM)`의 결과는 `INVOKE(f, v1, v2, ..., vN, RTy)`입니다. 여기서 `cv`는 `g`의 cv 한정자이고 바인딩된 인수 `v1, v2, ..., vN`의 값과 형식은 아래 지정된 대로 결정됩니다. 이를 사용하여 인수를 호출 가능 개체에 바인딩하면 맞춤형 인수 목록 및 지정된 반환 형식이 포함된 호출 가능 개체가 생성됩니다.

바인딩된 인수 `v1, v2, ..., vN` 및 해당 형식 `V1, V2, ..., VN`의 값은 다음과 같이 `bind` 호출 시 `Ti` 형식에 대한 해당 인수 `ti`의 형식 및 호출 래퍼 `g`의 cv 한정자 `cv`에 따라 결정됩니다.

`ti`가 `reference_wrapper<T>` 형식인 경우 `vi` 인수의 값은 `ti.get()`이고 해당 형식 `Vi`의 값은 `T&`입니다.

의 값이이 `std::is_bind_expression<Ti>::value` **`true`** 고 인수가이 `vi` 고 형식이 이면이 고 `ti(u1, u2, ..., uM)` `Vi` `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type` , 그렇지 않으면입니다.

의 값이 `j` 0이 아닌 경우 인수는이 `std::is_placeholder<Ti>::value` `vi` `uj` 고 해당 형식은입니다 `Vi` `Uj&` .

그렇지 않으면 인수가 `vi` 이 `ti` 고 해당 형식은 `Vi` `Ti` `cv` `&` 입니다.

예를 들어 `f(int, int)` 함수의 경우 `bind(f, _1, 0)` 식은 전달 호출 래퍼 `cw`를 반환하므로 `cw(x)`가 `f(x, 0)`을 호출합니다. `bind(f, 0, _1)` 식은 전달 호출 래퍼 `cw`를 반환하므로 `cw(x)`가 `f(0, x)`를 반환합니다.

및 인수에 대 한 호출의 인수 개수는 `bind` `fn` 호출 가능 개체에 전달할 수 있는 인수 수와 같아야 합니다 `fn` . 예를 들어, `bind(cos, 1.0)` 는 올바르지만 `bind(cos)` 와는 모두 `bind(cos, _1, 0.0)` 올바르지 않습니다.

`bind`에서 반환된 호출 래퍼에 대한 함수 호출의 인수 개수는 `bind` 호출의 모든 자리 표시자 인수에 대한 `is_placeholder<PH>::value`의 번호가 가장 높은 값보다 크거나 같아야 합니다. 예를 들어 `bind(cos, _2)(0.0, 1.0)` 은 올바르고을 반환 하며 `cos(1.0)` `bind(cos, _2)(0.0)` 는 올바르지 않습니다.

### <a name="example"></a>예제

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a><a name="bind1st"></a> bind1st

이항 함수 개체를 단항 함수 개체로 변환 하는 어댑터를 만드는 도우미 템플릿 함수입니다. 이항 함수의 첫 번째 인수를 지정 된 값에 바인딩합니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>매개 변수

*func*\
단항 함수 개체로 변환할 이항 함수 개체입니다.

*비어*\
이항 함수 개체의 첫 번째 인수가 바인딩되는 값입니다.

### <a name="return-value"></a>반환 값

이항 함수 개체의 첫 번째 인수를 *왼쪽* 값에 바인딩하여 생성 되는 단항 함수 개체입니다.

### <a name="remarks"></a>설명

함수 바인더는 일종의 함수 어댑터입니다. 함수 개체를 반환 하므로 특정 형식의 함수 컴퍼지션에서 사용 하 여 더 복잡 하 고 강력한 식을 생성할 수 있습니다.

*Func* 가 형식의 개체이 `Operation` 고 `c` 가 상수인 경우 `bind1st( func, c )` 은 [binder1st](../standard-library/binder1st-class.md) 클래스 생성자와 같으며를 `binder1st<Operation>(func, c)` 사용 하는 것이 더 편리 합니다.

### <a name="example"></a>예제

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a><a name="bind2nd"></a> bind2nd

이항 함수 개체를 단항 함수 개체로 변환 하는 어댑터를 만드는 도우미 템플릿 함수입니다. 이항 함수의 두 번째 인수를 지정 된 값에 바인딩합니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>매개 변수

*func*\
단항 함수 개체로 변환할 이항 함수 개체입니다.

*오른쪽*\
이항 함수 개체의 두 번째 인수가 바인딩되는 값입니다.

### <a name="return-value"></a>반환 값

이항 함수 개체의 두 번째 인수를 *right* 에 바인딩한 단항 함수 개체의 결과입니다.

### <a name="remarks"></a>설명

함수 바인더는 일종의 함수 어댑터입니다. 함수 개체를 반환 하므로 특정 형식의 함수 컴퍼지션에서 사용 하 여 더 복잡 하 고 강력한 식을 생성할 수 있습니다.

*Func* 가 형식의 개체이 `Operation` 고 `c` 가 상수인 경우 `bind2nd(func, c)` 은 [binder2nd](../standard-library/binder2nd-class.md) 클래스 생성자와 동일 하 `binder2nd<Operation>(func, c)` 고 더 편리 하 게 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a><a name="bit_and"></a> bit_and

인수에서 비트 AND 연산 (이진)을 수행 하는 미리 정의 된 함수 개체 `operator&` 입니다.

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator&`를 지원하는 모든 형식입니다.

*비어*\
비트 AND 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
비트 AND 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

### <a name="return-value"></a>반환 값

`Left & Right`의 결과입니다. 특수화된 템플릿은 `operator&`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

### <a name="remarks"></a>설명

`bit_and` 함수는 기본 데이터 형식에 대한 필수 형식이나 이항 `operator&`를 구현하는 사용자 정의 형식으로 제한됩니다.

## <a name="bit_not"></a><a name="bit_not"></a> bit_not

인수에 대해 비트 보수 (NOT) 연산 (단항)을 수행 하는 미리 정의 된 함수 개체입니다 `operator~` . C + + 14에 추가 되었습니다.

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
{
    Type operator()(const Type& Right) const;
};

// specialized transparent functor for operator~
template <>
struct bit_not<void>
{
    template <class Type>
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>매개 변수

*입력할*\
이항 `operator~`를 지원하는 형식입니다.

*오른쪽*\
비트 보수 연산의 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *형식의* lvalue 또는 rvalue 참조 인수를 완벽 하 게 전달 합니다.

### <a name="return-value"></a>반환 값

`~ Right`의 결과입니다. 특수화된 템플릿은 `operator~`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

### <a name="remarks"></a>설명

`bit_not` 함수는 기본 데이터 형식에 대한 필수 형식이나 이항 `operator~`를 구현하는 사용자 정의 형식으로 제한됩니다.

## <a name="bit_or"></a><a name="bit_or"></a> bit_or

인수에 대해 비트 OR 연산 ()을 수행 하는 미리 정의 된 함수 개체 `operator|` 입니다.

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator|`를 지원하는 모든 형식입니다.

*비어*\
비트 OR 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
비트 OR 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

### <a name="return-value"></a>반환 값

`Left | Right`의 결과입니다. 특수화된 템플릿은 `operator|`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

### <a name="remarks"></a>설명

`bit_or` 함수는 기본 데이터 형식에 대한 필수 형식이나 `operator|`를 구현하는 사용자 정의 형식으로 제한됩니다.

## <a name="bit_xor"></a><a name="bit_xor"></a> bit_xor

인수에 대해 비트 XOR 연산 (이진)을 수행 하는 미리 정의 된 함수 개체 `operator^` 입니다.

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator^`를 지원하는 모든 형식입니다.

*비어*\
비트 XOR 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
비트 XOR 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

### <a name="return-value"></a>반환 값

`Left ^ Right`의 결과입니다. 특수화된 템플릿은 `operator^`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

### <a name="remarks"></a>설명

`bit_xor` 함수는 기본 데이터 형식에 대한 필수 형식이나 이항 `operator^`를 구현하는 사용자 정의 형식으로 제한됩니다.

## <a name="cref"></a><a name="cref"></a> cref

인수에서 const `reference_wrapper`를 생성합니다.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>매개 변수

*Ty*\
래핑할 인수의 형식입니다.

*인수가*\
래핑할 인수입니다.

### <a name="remarks"></a>설명

첫 번째 함수는 `reference_wrapper<const Ty>(arg.get())`를 반환합니다. 이를 사용하여 상수 참조를 래핑합니다. 두 번째 함수는 `reference_wrapper<const Ty>(arg)`를 반환합니다. 이 함수를 사용하여 래핑된 참조를 상수 참조로 다시 래핑합니다.

### <a name="example"></a>예제

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }
```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="invoke"></a><a name="invoke"></a> 호출

지정 된 인수를 사용 하 여 호출 가능 개체를 호출 합니다. C + + 17에 추가 되었습니다.

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>매개 변수

*호출*\
호출할 개체의 형식입니다.

*Args*\
호출 인수의 형식입니다.

*fn*\
호출할 개체입니다.

*args*\
호출 인수입니다.

*사양의*\
**`noexcept`** 사양 `std::is_nothrow_invocable_v<Callable, Args>)` 입니다.

### <a name="remarks"></a>설명

매개 변수 *인수* 를 사용 하 여 호출 가능 개체 *fn* 을 호출 합니다. 실제로 `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)` 의사 (pseudo) 함수는 `INVOKE(f, t1, t2, ..., tN)` 다음 중 하나를 의미 합니다.

- `f`가 `T` 클래스의 멤버 함수에 대한 포인터이고, `t1`이 `T` 형식의 개체이거나 `T` 형식의 개체에 대한 참조 또는 `T`에서 파생된 형식의 개체에 대한 참조인 경우 `(t1.*f)(t2, ..., tN)`입니다. 즉,가 true 인 경우입니다 `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` .

- `(t1.get().*f)(t2, ..., tN)``f`가 클래스의 멤버 함수에 대 한 포인터 `T` 이 고는 `std::decay_t<decltype(t1)>` 의 특수화입니다 `std::reference_wrapper` .

- `((*t1).*f)(t2, ..., tN)``f`가 클래스의 멤버 함수에 대 한 포인터이 `T` 고가 `t1` 이전 형식 중 하나가 아닌 경우

- N == 1이며 `f`가 `T` 클래스의 멤버 데이터에 대한 포인터이고, `t1`이 `T` 형식의 개체이거나 `T` 형식의 개체에 대한 참조 또는 `T`에서 파생된 형식의 개체에 대한 참조인 경우 `t1.*f`입니다.  즉,가 true 인 경우입니다 `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` .

- `t1.get().*f` N = = 1이 고는 `f` 클래스의 멤버 데이터에 대 한 포인터이 `T` 고는 `std::decay_t<decltype(t1)>` 의 특수화입니다 `std::reference_wrapper` .

- `(*t1).*f` N = = 1이 고 `f` 는 클래스의 멤버 데이터에 대 한 포인터이 `T` 고는 `t1` 이전 형식 중 하나가 아닙니다.

- 다른 모든 경우에는 `f(t1, t2, ..., tN)`.

호출 가능 개체의 결과 형식에 대 한 자세한 내용은 [invoke_result](invoke-result-class.md)를 참조 하세요. 호출 가능 형식에 대 한 조건자는 [is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r 클래스](is-invocable-classes.md)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a><a name="mem_fn"></a> mem_fn

단순 호출 래퍼를 생성합니다.

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>매개 변수

*RTy*\
래핑된 함수의 반환 형식입니다.

*Ty*\
멤버 함수 포인터의 형식입니다.

### <a name="remarks"></a>설명

템플릿 함수는 약한 결과 형식의 간단한 호출 래퍼를 반환 합니다 .이는 `cw` 식이 `cw(t, a2, ..., aN)` 와 동일 합니다 `INVOKE(pm, t, a2, ..., aN)` . 예외를 throw 하지 않습니다.

반환 된 호출 래퍼는 해당 `std::unary_function<cv Ty*, RTy>` `result_type`  `argument_type` `cv Ty*` 형식이 인수 *를* `cv` 사용 하지 않는 cv 한정자를 사용 하는 멤버 함수에 대 한 포인터인 경우에만에서 파생 되 고 중첩 된 형식을 rty 및 중첩 형식의 동의어로 정의 합니다.

반환 된 호출 래퍼는 `std::binary_function<cv Ty*, T2, RTy>` `result_type`  `first argument_type` `cv Ty*` `second argument_type` `T2` *Ty* 형식이 형식의 `cv` 인수 하나를 사용 하는 cv 한정자를 사용 하는 멤버 함수에 대 한 포인터인 경우에만 `T2` (및에서 중첩 된 형식을 rty의 동의어로, 중첩 된 형식을의 동의어로, 중첩 된 형식을의 동의어로 정의)에서 파생 됩니다.

### <a name="example"></a>예제

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }
```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a><a name="mem_fun"></a> mem_fun

포인터 인수를 사용하여 초기화할 때 멤버 함수에 대한 함수 개체 어댑터를 생성하는 데 사용되는 도우미 템플릿 함수입니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되는 [mem_fn](#mem_fn) 및 [바인딩입니다](#bind).

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>매개 변수

*pMem*\
함수 개체로 변환할 `Type` 클래스의 멤버 함수 포인터입니다.

### <a name="return-value"></a>반환 값

**`const`** 또는 형식의 또는 **non_const** 함수 개체입니다 `mem_fun_t` `mem_fun1_t` .

### <a name="example"></a>예제

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a><a name="mem_fun_ref"></a> mem_fun_ref

참조 인수를 사용하여 초기화할 때 멤버 함수에 대한 함수 개체 어댑터를 생성하는 데 사용되는 도우미 템플릿 함수입니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>매개 변수

*pMem*\
함수 개체로 변환할 `Type` 클래스의 멤버 함수 포인터입니다.

### <a name="return-value"></a>반환 값

**`const`** `non_const` 또는 형식의 함수 개체입니다 `mem_fun_ref_t` `mem_fun1_ref_t` .

### <a name="example"></a>예제

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a><a name="not1"></a> not1

단항 조건자의 보수를 반환합니다. C + + 17의 [not_fn](#not_fn) 에는 사용 되지 않습니다.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>매개 변수

*가*\
부정할 단항 조건자입니다.

### <a name="return-value"></a>반환 값

수정된 단항 조건자의 부정을 나타내는 단항 조건자입니다.

### <a name="remarks"></a>설명

`unary_negate`이 단항 조건자에서 생성 되 면이 `predicate(x)` 반환 됩니다 `!predicate(x)` .

### <a name="example"></a>예제

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a><a name="not2"></a> not2

이항 조건자의 보수를 반환합니다. C + + 17의 [not_fn](#not_fn) 에는 사용 되지 않습니다.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>매개 변수

*func*\
부정할 이항 조건자입니다.

### <a name="return-value"></a>반환 값

수정된 이항 조건자의 부정을 나타내는 이항 조건자입니다.

### <a name="remarks"></a>설명

`binary_negate`이 이진 조건자에서 생성 된 경우를 `binary_predicate(x, y)` 반환 `!binary_predicate(x, y)` 합니다.

### <a name="example"></a>예제

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="not_fn"></a><a name="not_fn"></a> not_fn

`not_fn`함수 템플릿은 호출 가능 개체를 사용 하 여 호출 가능 개체를 반환 합니다. 반환 된 호출 가능 개체는 나중에 일부 인수를 사용 하 여 호출 될 때 해당 개체를 원래 호출 가능 개체로 전달 하 고 결과를 논리적으로 부정 합니다. 래핑된 호출 가능 개체의 const 한정자 및 값 범주 동작을 유지 합니다. `not_fn` 는 c + + 17에서 새로 사용 되며, 더 이상 사용 되지 않는 `std::not1` ,, 및를 대체 합니다 `std::not2` `std::unary_negate` `std::binary_negate` .

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>매개 변수

*func*\
전달 호출 래퍼를 생성 하는 데 사용 되는 호출 가능 개체입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `return call_wrapper(std::forward<Callable>(func))` 이 표시 클래스를 기반으로 하 여와 같은 호출 래퍼를 반환 합니다.

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

호출 가능 개체 *func* 의 명시적 생성자에는 `std::decay_t<Callable>` 의 요구 사항을 충족 하는 형식이 필요 `MoveConstructible` 하며,이는 true 여야 합니다 `is_constructible_v<FD, Callable>` . 에서 래핑된 호출 가능 개체를 `fd` 초기화 `std::forward<Callable>(func)` 하 고 생성 시 throw 되는 예외를 throw `fd` 합니다.

래퍼는 다음과 같이 lvalue 또는 rvalue 참조 범주 및 const 한정자로 구분 된 호출 연산자를 노출 합니다.

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

처음 두 개는와 동일 합니다 `return !std::invoke(fd, std::forward<Args>(args)...)` . 두 번째 두 개는와 동일 합니다 `return !std::invoke(std::move(fd), std::forward<Args>(args)...)` .

### <a name="example"></a>예제

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a><a name="ptr_fun"></a> ptr_fun

단항 및 이항 함수 포인터를 각각 조정 가능한 단항 및 이항 함수로 변환하는 데 사용되는 도우미 템플릿 함수입니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>매개 변수

*pfunc*\
조정 가능한 함수로 변환할 단항 또는 이항 함수 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 템플릿 함수는 단항 함수 [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)  < `Arg` , **Result**> ()을 반환 합니다 \* `pfunc` .

두 번째 템플릿 함수는 이진 함수 [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \<**Arg1**, **Arg2**, **Result**> ()을 반환 합니다 \* `pfunc` .

### <a name="remarks"></a>설명

함수 포인터는 함수 개체입니다. 이 함수는 매개 변수로 함수를 필요로 하는 모든 알고리즘에 전달 될 수 있지만,이는 조정할 수 없습니다. 해당 중첩 형식에 대 한 정보는 어댑터와 함께 사용 하는 데 필요 합니다. 예를 들어 값을에 바인딩하거나 부정 하는 데 사용 해야 합니다. `ptr_fun` 도우미 함수를 통해 단항 및 이행 함수 포인터를 변환하면 함수 어댑터를 단항 및 이행 함수 포인터와 함께 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a><a name="ref"></a> 행위자

인수에서 `reference_wrapper` 를 생성합니다.

```cpp
template <class Ty>
    reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
    reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>반환 값

`arg`, 특히 `reference_wrapper<Ty>(arg)`에 대한 참조입니다.

### <a name="example"></a>예제

다음 예제에서는 문자열 변수에 바인딩된 함수 및 `ref`호출에서 계산된 문자열 변수의 참조에 바인딩된 함수의 두 함수를 정의합니다. 변수의 값이 변경될 경우 첫 번째 함수는 이전 값을 계속 사용하고 두 번째 함수는 새 값을 사용합니다.

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 `function` 개체를 교환합니다.

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>매개 변수

*FT*\
함수 개체에서 제어되는 형식입니다.

*보려면*\
첫 번째 함수 개체입니다.

*키*\
두 번째 함수 개체입니다.

### <a name="remarks"></a>설명

함수에서 `f1.swap(f2)`을 반환합니다.

### <a name="example"></a>예제

```cpp
// std__functional__swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    swap(fn0, fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```
