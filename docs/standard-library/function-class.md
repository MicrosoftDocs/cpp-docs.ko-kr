---
description: '자세한 정보: 함수 클래스'
title: function 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
ms.openlocfilehash: 30e81e297791691ba5736b4e116fc08ab4229f0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232176"
---
# <a name="function-class"></a>function 클래스

호출 가능 개체용 래퍼입니다.

## <a name="syntax"></a>구문

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>매개 변수

*Fty*\
래핑할 함수 형식입니다.

*Ax*\
할당자 함수입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 호출 시그니처가 인 호출 래퍼입니다 `Ret(T1, T2, ..., TN)` . 이를 사용하여 다양한 호출 가능 개체를 균일한 래퍼에 포함합니다.

일부 멤버 함수는 원하는 대상 개체를 명명하는 피연산자를 사용합니다. 그러한 피연산자를 여러 방법으로 지정할 수 있습니다.

`fn` -- 호출 가능 개체 `fn`, 호출 후에 `function` 개체가 `fn` 복사본을 포함함

`fnref` -- `fnref.get()`에 의해 명명된 호출 가능 개체, 호출 후에 `function` 개체가 `fnref.get()`에 대한 참조를 포함함

`right` -- `function` 개체 `right`의 해 포함된 호출 가능 개체(있는 경우)

`npc` -- null 포인터, 호출 후에 `function` 개체가 비어 있음

모든 경우에 `INVOKE(f, t1, t2, ..., tN)`(여기서 `f`는 호출 가능 개체이고 `t1, t2, ..., tN`은 각각 `T1, T2, ..., TN` 형식의 lvalue임)은 올바른 형식이어야 하고 `Ret`가 void가 아니면 `Ret`로 변환 가능해야 합니다.

빈 `function` 개체는 호출 가능 개체나 호출 가능 개체에 대한 참조를 포함하지 않습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[function](#function)|비어 있거나 고정된 시그니처가 포함된 임의 형식의 호출 가능 개체를 저장하는 래퍼를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[result_type](#result_type)|호출 가능 개체의 반환 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[assign](#assign)|이 함수 개체에 호출 가능 개체를 할당합니다.|
|[스왑을](#swap)|두 개의 호출 가능 개체를 바꿉니다.|
|[대상](#target)|저장된 호출 가능 개체가 지정된 대로 호출 가능한지 테스트합니다.|
|[target_type](#target_type)|호출 가능 개체에 대한 형식 정보를 가져옵니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 지정 되지 않음](#op_unspecified)|저장된 호출 가능 개체가 있는지 테스트합니다.|
|[연산자 ()](#op_call)|호출 가능 개체를 호출합니다.|
|[연산자 =](#op_eq)|저장된 호출 가능 개체를 바꿉니다.|

## <a name="assign"></a><a name="assign"></a> 할당

이 함수 개체에 호출 가능 개체를 할당합니다.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>매개 변수

*_Func*\
호출 가능 개체입니다.

*_Fnref*\
호출 가능 개체가 포함된 참조 래퍼입니다.

*Ax*\
할당자 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 각각에 있는를로 `callable object` **`*this`** 전달 된 호출 가능 개체로 바꿉니다 `operand` . 둘 다 할당자 개체 *Ax* 를 사용 하 여 저장소를 할당 합니다.

## <a name="function"></a><a name="function"></a> 함수

비어 있거나 고정된 시그니처가 포함된 임의 형식의 호출 가능 개체를 저장하는 래퍼를 생성합니다.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
복사할 함수 개체입니다.

*Fx*\
호출 가능 개체의 형식입니다.

*_Func*\
래핑할 호출 가능 개체입니다.

*#C4*\
할당자 형식입니다.

*Ax*\
할당자입니다.

*_Fnref*\
래핑할 호출 가능 개체 참조입니다.

### <a name="remarks"></a>설명

처음 두 개의 생성자는 빈 `function` 개체를 생성합니다. 다음 세 개의 생성자는 피연산자로 전달된 호출 가능 개체를 포함하는 `function` 개체를 생성합니다. 마지막 두 개의 생성자는 할당자 개체 Ax를 사용하여 스토리지를 할당합니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="operator-unspecified"></a><a name="op_unspecified"></a> 연산자 지정 되지 않음

저장된 호출 가능 개체가 있는지 테스트합니다.

```cpp
operator unspecified();
```

### <a name="remarks"></a>설명

연산자는 **`bool`** 개체가 비어 있지 않은 경우에만 true 값으로 변환할 수 있는 값을 반환 합니다. 이를 사용하여 개체가 비어 있는지 테스트합니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="operator"></a><a name="op_call"></a> 연산자 ()

호출 가능 개체를 호출합니다.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>매개 변수

*TN*\
N번째 인수의 형식입니다.

*tN*\
N번째 호출 인수입니다.

### <a name="remarks"></a>설명

멤버 함수는 `INVOKE(fn, t1, t2, ..., tN, Ret)` 를 반환 합니다 `fn` . 여기서는에 저장 된 대상 개체입니다 **`*this`** . 이를 사용하여 래핑된 호출 가능 개체를 호출합니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

저장된 호출 가능 개체를 바꿉니다.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>매개 변수

*npc*\
null 포인터 상수입니다.

*오른쪽*\
복사할 함수 개체입니다.

*fn*\
래핑할 호출 가능 개체입니다.

*fnref*\
래핑할 호출 가능 개체 참조입니다.

### <a name="remarks"></a>설명

각 연산자는에 보유 한 호출 가능 개체를 **`*this`** 피연산자로 전달 된 호출 가능 개체로 바꿉니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_operator_as.cpp
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
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a><a name="result_type"></a> result_type

호출 가능 개체의 반환 형식입니다.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>설명

형식 정의는 템플릿의 호출 시그니처에서 `Ret` 형식의 동의어입니다. 이를 사용하여 래핑된 호출 가능 개체의 반환 형식을 결정합니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 개의 호출 가능 개체를 바꿉니다.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
바꿀 함수 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 대상 개체를 **`*this`** 와 *오른쪽* 으로 바꿉니다. 일정한 시간에 이 작업을 수행하고 예외를 throw하지 않습니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_swap.cpp
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

    fn0.swap(fn1);
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

## <a name="target"></a><a name="target"></a> 대상을

저장된 호출 가능 개체가 지정된 대로 호출 가능한지 테스트합니다.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>매개 변수

*Fty2*\
테스트할 대상 호출 가능 개체 형식입니다.

### <a name="remarks"></a>설명

*Fty2* 형식은 인수 형식 및 반환 형식에 대해 호출할 수 있어야 합니다 `T1, T2, ..., TN` `Ret` . `target_type() == typeid(Fty2)`인 경우 멤버 템플릿 함수는 대상 개체의 주소를 반환하고, 그렇지 않으면 0을 반환합니다.

*Fty2* 형식은 인수 형식 및 반환 형식에 대해 호출할 수 `T1, T2, ..., TN` 있습니다. 즉, `Ret` 형식의 lvalue에 대해 각각 형식이 올바른 형식이 면이 고, `fn, t1, t2, ..., tN` `Fty2, T1, T2, ..., TN` `INVOKE(fn, t1, t2, ..., tN)` `Ret` 이이 아니면 **`void`** 로 변환할 수 있는 경우 `Ret` 입니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }
```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a><a name="target_type"></a> target_type

호출 가능 개체에 대한 형식 정보를 가져옵니다.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>설명

멤버 함수는가 비어 있으면를 반환 하 고 `typeid(void)` **`*this`** 그렇지 않으면를 반환 합니다 `typeid(T)` `T` . 여기서는 대상 개체의 형식입니다.

### <a name="example"></a>예제

```cpp
// std__functional__function_target_type.cpp
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
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```
