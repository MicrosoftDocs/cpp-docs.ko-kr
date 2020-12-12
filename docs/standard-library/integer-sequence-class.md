---
description: Integer_sequence 클래스에 대해 자세히 알아보세요.
title: integer_sequence 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: 321e41c2c3bfaa1f89c05f799dedc4f4250f0a2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323977"
---
# <a name="integer_sequence-class"></a>integer_sequence 클래스

정수 시퀀스를 나타냅니다. 는 함수에 인수로 전달 되는 std:: tuple와 같은 variadic 형식의 매개 변수 팩을 추론 하 고 확장 하는 데 사용할 수 있습니다 \<T...> .

## <a name="syntax"></a>구문

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>매개 변수

*트*\
값의 형식입니다. bool, char, char16_t, char32_t, wchar_t, 부호 있는 정수 또는 부호 없는 정수 등 정수 계열 형식이어야 합니다.

*Vals*\
정수 계열 형식 T 값의 시퀀스를 나타내는 비형식 매개 변수 팩입니다.

## <a name="members"></a>멤버

|Name|설명|
|-|-|
|`static size_t size() noexcept`|시퀀스의 요소 수입니다.|
|`typedef T value_type`|시퀀스에 있는 각 요소의 형식입니다. 정수 계열 형식이어야 합니다.|

## <a name="remarks"></a>설명

함수로 직접 전달되는 매개 변수 팩은 특별한 라이브러리 도우미 없이 압축을 풀 수 있습니다. 매개 변수 팩이 함수로 전달되는 형식의 일부이고 요소에 액세스하는 데 인덱스가 필요한 경우 `integer_sequence`와 관련 형식 별칭 `make_integer_sequence`, `index_sequence`, `make_index_sequence` 및 `index_sequence_for`를 사용하면 가장 쉽게 압축을 풀 수 있습니다.

## <a name="example"></a>예제

다음 예제는 최초 제안 [N3658](https://wg21.link/n3658)을 기반으로 합니다. 이 예제에서는 `integer_sequence`를 사용하여 `std::array<T,N>`에서 `std::tuple`을 만드는 방법 및 `integer_sequence`를 사용하여 튜플 멤버를 얻는 방법을 보여 줍니다.

`a2t` 함수에서 `index_sequence`는 `size_t` 정수 계열 형식을 기반으로 하는 `integer_sequence`의 별칭입니다. `make_index_sequence`는 컴파일 시간에 호출자에 의해 전달되는 배열과 동일한 수의 요소로 0부터 시작하는 `index_sequence`를 만드는 별칭입니다. `a2t`는 값별로 `index_sequence`를 `a2t_`에 전달합니다. 여기서 `a[I]...` 식은 `I`의 압축을 풉니다. 그러면 요소는 개별 인수로 사용되는 `make_tuple`에 공급됩니다. 예를 들어 시퀀스에 세 개의 요소가 포함되어 있으면 `make_tuple`이 make_tuple(a[0], a[1], a[2])로 호출됩니다. 물론 배열 요소 자체는 임의 형식일 수 있습니다.

Apply 함수는 [std:: tuple](../standard-library/tuple-class.md)을 허용 하 고 `integer_sequence` 도우미 클래스를 사용 하 여를 생성 합니다 `tuple_size` . [Tuple_size](../standard-library/tuple-size-class-tuple.md) 참조 형식에서 작동 하지 않기 때문에 [std::d ecay_t](../standard-library/decay-class.md) 가 필요 합니다. `apply_` 함수는 튜플 멤버의 압축을 풀고 별도의 인수로 함수 호출에 전달합니다. 이 예제에서 함수는 값을 출력하는 간단한 람다 식입니다.

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

`index_sequence`매개 변수 팩에 대 한을 만들려면 `index_sequence_for` \<T...> 에 대 한 별칭을 사용 합니다.`make_index_sequence`\<sizeof...(T)>

## <a name="requirements"></a>요구 사항

헤더: \<type_traits\>

네임스페이스: std

## <a name="see-also"></a>참고 항목

[줄임표 및 Variadic 템플릿](../cpp/ellipses-and-variadic-templates.md)
