---
title: reference_wrapper 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: 52e8876e1bd72259154a3be7518d91ba09ec2ffc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513492"
---
# <a name="referencewrapper-class"></a>reference_wrapper 클래스

참조를 래핑합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
class reference_wrapper
{
public:
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));

private:
    Ty *ptr; // exposition only
};
```

## <a name="remarks"></a>설명

`reference_wrapper<Ty>`는 `Ty` 형식의 개체 또는 함수에 대한 참조를 래핑하며 해당 형식의 개체를 가리키는 포인터가 포함된 복사본 생성/할당 가능 래퍼입니다. `reference_wrapper`를 사용하면 표준 컨테이너에 참조를 저장하고 `std::bind`에 대한 참조를 통해 개체를 전달할 수 있습니다.

`Ty` 형식은 개체 형식 또는 함수 형식이어야 하며, 그렇지 않으면 컴파일 시간에 정적 어설션이 실패합니다.

도우미 함수 [std::ref](functional-functions.md#ref) 및 [std::cref](functional-functions.md#cref)를 사용하여 `reference_wrapper` 개체를 만들 수 있습니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[reference_wrapper](#reference_wrapper)|`reference_wrapper`를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[result_type](#result_type)|래핑된 참조의 약한 결과 형식입니다.|
|[type](#type)|래핑된 참조 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[get](#get)|래핑된 참조를 가져옵니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[reference_wrapper::operator Ty&amp;](#op_ty_amp)|래핑된 참조에 대한 포인터를 가져옵니다.|
|[reference_wrapper::operator()](#op_call)|래핑된 참조를 호출합니다.|
## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="get"></a>  reference_wrapper::get

래핑된 참조를 가져옵니다.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>설명

구성원 함수는 래핑된 참조를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="op_ty_amp"></a>  reference_wrapper::operator Ty&amp;

래핑된 참조를 가져옵니다.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>설명

멤버 연산자는 `*ptr`을 반환합니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="op_call"></a>  reference_wrapper::operator()

래핑된 참조를 호출합니다.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>매개 변수

*유형*<br/>
인수 목록 유형입니다.

*인수*<br/>
인수 목록입니다.

### <a name="remarks"></a>설명

템플릿 구성원 `operator()`는 `std::invoke(get(), std::forward<Types>(args)...)`를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a>  reference_wrapper::reference_wrapper

`reference_wrapper`를 생성합니다.

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>매개 변수

*Ty*<br/>
래핑할 형식입니다.

*val*<br/>
래핑할 값입니다.

### <a name="remarks"></a>설명

생성자는 저장된 값 `ptr`을 `&val`로 설정합니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a>  reference_wrapper::result_type

래핑된 참조의 약한 결과 형식입니다.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>설명

`result_type` 형식 정의는 래핑된 함수의 취약한 결과 형식과 동일한 의미입니다. 이 형식 정의는 함수 형식에서만 의미가 있습니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a>  reference_wrapper::type

래핑된 참조 형식입니다.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>설명

typedef는 템플릿 인수 `Ty`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```

## <a name="see-also"></a>참고자료

[cref](../standard-library/functional-functions.md#cref)<br/>
[ref](../standard-library/functional-functions.md#ref)<br/>
