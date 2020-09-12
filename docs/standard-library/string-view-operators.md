---
title: '&lt;string_view &gt; 연산자'
description: '`string_view`두 개체를 비교 하는 데 사용 되는 연산자에 대 한 API 참조 `string_view` 또는 `string_view` 및 기타 문자열 개체'
ms.date: 9/4/2020
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 832e49aaf01a4ea124b7a6881b93bd93b7337215
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039887"
---
# <a name="ltstring_viewgt-operators"></a>&lt;string_view &gt; 연산자

이러한 연산자를 사용 하 여 두 개의 string_view 개체, string_view 및 암시적 변환이 제공 되는 다른 문자열 개체 (예 [: std:: string](basic-string-class.md)또는 **char \* **)를 비교 합니다.

[연산자! =](#op_neq)\
[연산자&gt;](#op_gt)\
[연산자&gt;=](#op_gt_eq)\
[연산자&lt;](#op_lt)\
[연산자&lt;&lt;](#op_lt_lt)\
[연산자&lt;=](#op_lt_eq)\
[연산자 = =](#op_eq_eq)\
[연산자 "" sv](#op_sv)

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 개체가 우변에 있는 개체와 같지 않은지 테스트합니다.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 개체와 사전순으로 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

*Convertible_string_type* 에서 다른 쪽의 string_view에 대 한 암시적 변환이 존재 해야 합니다.

비교는 문자 시퀀스에 대 한 쌍으로 사전순으로 비교 됩니다. 동일한 수의 요소를 포함 하 고 요소가 모두 같으면 두 개체가 같습니다. 그렇지 않으면 목록은 같지 않은 것입니다.

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 개체가 우변에 있는 개체와 같은지 테스트합니다.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 개체와 같으면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

*Convertible_string_type* 에서 다른 쪽의 string_view에 대 한 암시적 변환이 존재 해야 합니다.

비교는 문자 시퀀스에 대 한 쌍으로 사전순으로 비교 됩니다. 동일한 수의 요소를 포함 하 고 요소가 모두 같으면 두 개체가 같습니다.

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 작음을 테스트 sidestring_view

```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 사전순으로 면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

*Convertible_string_type* 에서 다른 쪽의 string_view에 대 한 암시적 변환이 존재 해야 합니다.

비교는 문자 시퀀스에 대 한 쌍으로 사전순으로 비교 됩니다. 동일 하지 않은 첫 번째 문자 쌍이 발견 되 면 해당 비교 결과가 반환 됩니다. 같지 않은 문자를 찾을 수 없지만 한 시퀀스가 짧으면 더 짧은 시퀀스가 더 짧은 시퀀스 보다 작습니다. 즉, "cat"은 "cats" 보다 낮습니다.

### <a name="example"></a>예제

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

연산자의 좌변에 있는 개체가 우변에 있는 개체보다 작거나 같은지 테스트합니다.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 작거나 같으면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

[Operator &lt; ](#op_lt)를 참조 하세요.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

String_view를 출력 스트림에 씁니다.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>매개 변수

*Ostr*\
쓸 출력 스트림입니다.

*문자열*\
출력 스트림에 입력 될 string_view입니다.

### <a name="return-value"></a>반환 값

쓸 출력 스트림입니다.

### <a name="remarks"></a>설명

이 연산자를 사용 하 여 string_view 콘텐츠를 출력 스트림에 삽입 합니다. 예를 들어 [std:: cout](iostream.md#cout)을 사용 합니다.

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 개체가 우변에 있는 개체보다 큰지 테스트합니다.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 string_view 개체 보다 크면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

[Operator &lt; ](#op_lt)를 참조 하세요.

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

연산자의 좌변에 있는 개체가 우변에 있는 개체보다 크거나 같은지 테스트합니다.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

*오른쪽*\
변환할 수 있는 문자열 형식 이거나 비교할 형식의 개체 `basic_string_view` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 크거나 같으면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

[Operator &lt; ](#op_lt)를 참조 하세요.

## <a name="operator-sv-string_view-literal"></a><a name="op_sv"></a> 연산자 "" sv (string_view 리터럴)

문자열 리터럴에서 string_view를 생성 합니다. 네임 스페이스가 필요 `std::literals::string_view_literals` 합니다.

### <a name="example"></a>예제

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="requirements"></a>요구 사항

[/std:c++17](../build/reference/std-specify-language-standard-version.md)

## <a name="see-also"></a>참고 항목

[\<string_view>](../standard-library/string-view.md)
