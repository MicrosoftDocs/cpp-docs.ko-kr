---
title: function 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 879999f279493c10509900c040ca6f5171c215b4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
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

`Fty` 래핑할 함수 형식입니다.

`Ax` 할당자 함수입니다.

## <a name="remarks"></a>설명

템플릿 클래스는 `Ret(T1, T2, ..., TN)` 호출 시그니처가 포함된 호출 래퍼입니다. 이를 사용하여 다양한 호출 가능 개체를 균일한 래퍼에 포함합니다.

일부 멤버 함수는 원하는 대상 개체를 명명하는 피연산자를 사용합니다. 그러한 피연산자를 여러 방법으로 지정할 수 있습니다.

`fn` -- 호출 가능 개체 `fn`, 호출 후에 `function` 개체가 `fn` 복사본을 포함함

`fnref` -- `fnref.get()`에 의해 명명된 호출 가능 개체, 호출 후에 `function` 개체가 `fnref.get()`에 대한 참조를 포함함

`right` -- `function` 개체 `right`의 해 포함된 호출 가능 개체(있는 경우)

`npc` -- null 포인터, 호출 후에 `function` 개체가 비어 있음

모든 경우에 `INVOKE(f, t1, t2, ..., tN)`(여기서 `f`는 호출 가능 개체이고 `t1, t2, ..., tN`은 각각 `T1, T2, ..., TN` 형식의 lvalue임)은 올바른 형식이어야 하고 `Ret`가 void가 아니면 `Ret`로 변환 가능해야 합니다.

빈 `function` 개체는 호출 가능 개체나 호출 가능 개체에 대한 참조를 포함하지 않습니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[function](#function)|비어 있거나 고정된 시그니처가 포함된 임의 형식의 호출 가능 개체를 저장하는 래퍼를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[result_type](#result_type)|호출 가능 개체의 반환 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[assign](#assign)|이 함수 개체에 호출 가능 개체를 할당합니다.|
|[swap](#swap)|두 개의 호출 가능 개체를 바꿉니다.|
|[target](#target)|저장된 호출 가능 개체가 지정된 대로 호출 가능한지 테스트합니다.|
|[target_type](#target_type)|호출 가능 개체에 대한 형식 정보를 가져옵니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[function::operator unspecified](#op_unspecified)|저장된 호출 가능 개체가 있는지 테스트합니다.|
|[function::operator()](#op_call)|호출 가능 개체를 호출합니다.|
|[function::operator=](#op_eq)|저장된 호출 가능 개체를 바꿉니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="assign"></a>  function::assign

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

`_Func` 호출 가능 개체입니다.

`_Fnref` 호출 가능 개체를 포함 하는 참조 래퍼.

`Ax` 할당자 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 각각 `*this`에 의해 포함된 `callable object`를 `operand`로 전달된 호출 가능 개체로 바꿉니다. 두 멤버 함수 모두 할당자 개체 `Ax`를 사용하여 저장소를 할당합니다.

## <a name="function"></a>  function::function

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

`right` 복사할 함수 개체입니다.

`Fx` 호출 가능 개체의 형식입니다.

`_Func` 래핑하는 호출 가능 개체입니다.

`Alloc` 할당자 형식입니다.

`Ax` 할당자입니다.

`_Fnref` 줄 바꿈에 대 한 호출 가능 개체 참조입니다.

### <a name="remarks"></a>설명

처음 두 개의 생성자는 빈 `function` 개체를 생성합니다. 다음 세 개의 생성자는 피연산자로 전달된 호출 가능 개체를 포함하는 `function` 개체를 생성합니다. 마지막 두 개의 생성자는 할당자 개체 Ax를 사용하여 저장소를 할당합니다.

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

## <a name="op_unspecified"></a>  function::operator unspecified

저장된 호출 가능 개체가 있는지 테스트합니다.

```cpp
operator unspecified();
```

### <a name="remarks"></a>설명

연산자는 개체가 비어 있지 않은 경우에만 true 값이 포함된 `bool`로 변환할 수 있는 값을 반환합니다. 이를 사용하여 개체가 비어 있는지 테스트합니다.

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

## <a name="op_call"></a>  function::operator()

호출 가능 개체를 호출합니다.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>매개 변수

`TN` N 번째 형식 인수를 호출 합니다.

`tN` N 번째 호출 인수입니다.

### <a name="remarks"></a>설명

멤버 함수는 `INVOKE(fn, t1, t2, ..., tN, Ret)`를 반환합니다. 여기서 `fn`은 `*this`에 저장된 대상 개체입니다. 이를 사용하여 래핑된 호출 가능 개체를 호출합니다.

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

## <a name="op_eq"></a>  function::operator=

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

`npc` Null 포인터 상수입니다.

`right` 복사할 함수 개체입니다.

`fn` 래핑하는 호출 가능 개체입니다.

`fnref` 줄 바꿈에 대 한 호출 가능 개체 참조입니다.

### <a name="remarks"></a>설명

멤버 함수는 각각 `*this`에 의해 포함된 호출 가능 개체를 피연산자로 전달된 호출 가능 개체로 바꿉니다.

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

## <a name="result_type"></a>  function::result_type

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

## <a name="swap"></a>  function::swap

두 개의 호출 가능 개체를 바꿉니다.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>매개 변수

`right` 함수 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 `*this`와 `right` 사이에 대상 개체를 바꿉니다. 일정한 시간에 이 작업을 수행하고 예외를 throw하지 않습니다.

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

## <a name="target"></a>  function::target

저장된 호출 가능 개체가 지정된 대로 호출 가능한지 테스트합니다.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>매개 변수

`Fty2` 테스트 대상 호출 가능 개체 형식입니다.

### <a name="remarks"></a>설명

`Fty2` 형식은 인수 형식 `T1, T2, ..., TN` 및 반환 형식 `Ret`에 대해 호출 가능해야 합니다. `target_type() == typeid(Fty2)`인 경우 멤버 템플릿 함수는 대상 개체의 주소를 반환하고, 그렇지 않으면 0을 반환합니다.

`Fty2, T1, T2, ..., TN` 형식의 lvalue `fn, t1, t2, ..., tN`에 대해 각각 `INVOKE(fn, t1, t2, ..., tN)`이 올바른 형식이고 `Ret`가 `Ret`로 변환할 수 있는 `void`가 아닌 경우, `Fty2` 형식은 인수 형식 `T1, T2, ..., TN` 및 반환 형식 `Ret`에 대해 호출 가능합니다.

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

## <a name="target_type"></a>  function::target_type

호출 가능 개체에 대한 형식 정보를 가져옵니다.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `*this`가 비어 있으면 `typeid(void)`를 반환하고, 그렇지 않으면 `typeid(T)`를 반환합니다. 여기서 `T`는 대상 개체의 형식입니다.

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

## <a name="see-also"></a>참고자료

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper 클래스](../standard-library/reference-wrapper-class.md)<br/>
