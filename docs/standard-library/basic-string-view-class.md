---
title: basic_string_view 클래스
description: 에 대 한 API 참조 `basic_string_view` 는 문자 형식의 일정 한 연속 시퀀스를 참조 합니다.
ms.date: 9/8/2020
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::ends_with
- xstring/std::basic_string_view::starts_with
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, ends_with
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, starts_with
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 8eddf4bc6aae0338dc2e914aa57e6c1e7cc5c912
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040212"
---
# <a name="basic_string_view-class"></a>basic_string_view 클래스

클래스 템플릿은 함수를 사용 하 여 `basic_string_view<charT>` 해당 형식에 대 한 템플릿 화 필요가 없는 여러 관련 없는 문자열 형식을 허용 하는 안전 하 고 효율적인 방법으로 사용할 수 있도록 c + + 17에서 추가 되었습니다. 클래스는 문자 데이터의 연속 시퀀스에 대 한 소유 하지 않는 포인터와 시퀀스의 문자 수를 지정 하는 길이를 포함 합니다. 시퀀스가 null로 종결 되었는지 여부에 대 한 가정을 하지 않습니다.

표준 라이브러리는 요소의 형식에 따라 몇 가지 특수화를 정의 합니다.

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

이 문서에서 "string_view" 이라는 용어는 일반적으로 이러한 형식 정의 중 하나를 의미 합니다.

String_view는 문자열 데이터를 읽는 데 필요한 최소 공통 인터페이스에 대해 설명 합니다. 기본 데이터에 대 한 const 액세스를 제공 합니다. 복사본을 만듭니다 ( `copy` 함수 제외). 데이터에는 임의의 위치에 null 값 (' \ 0 ')이 포함 되거나 포함 되지 않을 수 있습니다. String_view는 개체의 수명을 제어 하지 않습니다. 기본 문자열 데이터가 유효한 지 확인 하는 것은 호출자의 책임입니다.

String_view 형식의 매개 변수를 허용 하는 함수는 함수를 템플릿으로 설정 하거나 함수를 특정 문자열 형식의 하위 집합으로 제한 하지 않고도 문자열 형식으로 작업 하도록 만들 수 있습니다. 유일한 요구 사항은 string_view 하는 문자열 형식에서 암시적 변환이 존재 한다는 것입니다. 모든 표준 문자열 형식은 동일한 요소 형식을 포함 하는 string_view으로 암시적으로 변환할 수 있습니다. 즉,는로 `std::string` 변환할 수 있지만는로 변환할 수 `string_view` 없습니다 `wstring_view` .

다음 예제에서는 `f` 형식의 매개 변수를 사용 하는 비템플릿 함수를 보여 줍니다 `wstring_view` . , 및 형식의 인수를 사용 하 여 호출할 수 있습니다 `std::wstring` `wchar_t*` `winrt::hstring` .

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>구문

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>매개 변수

*CharType*\
String_view에 저장 된 문자 형식입니다. C + + 표준 라이브러리는이 템플릿의 특수화에 대해 다음과 같은 형식 정의를 제공 합니다.

- 형식의 요소에 대 한 [string_view](../standard-library/string-view-typedefs.md#string_view)**`char`**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view),의 경우 **`wchar_t`**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view)**`char16_t`**
- 에 대 한 [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **`char32_t`** 입니다.

*특징이*\
기본값은 [char_traits](char-traits-struct.md) < *chartype*>입니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_string_view](#basic_string_view)|비어 있거나 다른 문자열 개체 데이터의 전체 또는 일부 또는 C 스타일 문자 배열을 가리키는 string_view를 생성 합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|**const_iterator**|요소를 읽을 수 있는 임의 액세스 반복기입니다 **`const`** .|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**반복**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**놓고**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>멤버 연산자

|연산자|Description|
|-|-|
|[연산자 =](#op_eq)|String_view 또는 변환할 수 있는 문자열 개체를 다른 string_view에 할당 합니다.|
|[연산자\[\]](#op_at)|지정한 인덱스의 요소를 반환합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[at](#at)|지정 된 위치에 있는 요소에 대 한 const_reference를 반환 합니다.|
|[뒤로](#back)|마지막 요소에 대 한 const_reference를 반환 합니다.|
|[시작](#begin)|첫 번째 요소를 주소 지정 하는 상수 반복기를 반환 합니다. (string_views 변경할 수 없습니다.)|
|[cbegin](#cbegin)|[Begin](#begin)과 동일 합니다.|
|[cend](#cend)|마지막 요소를 지난 요소를 가리키는 상수 반복기를 반환 합니다.|
|[copy](#copy)|소스 string_view의 인덱싱된 위치에서 대상 문자 배열로 지정 된 수 만큼의 문자를 복사 합니다. 권장 하지 않습니다. 대신 _Copy_s를 사용 하십시오.)|
|[_Copy_s](#_copy_s)|보안 CRT 복사 함수입니다.|
|[과](#compare)|String_view를 지정 된 string_view와 비교 하 여 같은지 확인 하거나 한 다른 보다 더 작은 사전순으로 확인 합니다.|
|[crbegin](#crbegin)|[Rbegin](#rbegin)과 동일 합니다.|
|[crend](#crend)|[Rend](#rend)와 동일 합니다.|
|[data](#data)|문자 시퀀스에 대 한 소유 하지 않은 원시 포인터를 반환 합니다.|
|[empty](#empty)|String_view에 문자가 포함 되어 있는지 여부를 테스트 합니다.|
|[종단](#end)|[Cend](#cend)와 동일 합니다.|
|[ends_with](#ends_with)<sup>c + + 20</sup>|문자열 뷰가 지정 된 접미사로 끝나는지 여부를 확인 합니다.|
|[find](#find)|지정 된 문자 시퀀스와 일치 하는 첫 번째 하위 문자열을 정방향 방향으로 검색 합니다.|
|[find_first_not_of](#find_first_not_of)|지정 된 string_view 또는 변환할 수 있는 문자열 개체의 요소가 아닌 첫 번째 문자를 검색 합니다.|
|[find_first_of](#find_first_of)|지정 된 string_view 또는 변환할 수 있는 문자열 개체의 요소와 일치 하는 첫 번째 문자를 검색 합니다.|
|[find_last_not_of](#find_last_not_of)|지정 된 string_view 또는 변환할 수 있는 문자열 개체의 요소가 아닌 마지막 문자를 검색 합니다.|
|[find_last_of](#find_last_of)|지정 된 string_view 또는 변환할 수 있는 문자열 개체의 요소인 마지막 문자를 검색 합니다.|
|[앞뒤](#front)|첫 번째 요소에 대 한 const_reference를 반환 합니다.|
|[length](#length)|현재 요소 수를 반환 합니다.|
|[max_size](#max_size)|String_view에 포함할 수 있는 최대 문자 수를 반환 합니다.|
|[rbegin](#rbegin)|역방향 string_view에서 첫 번째 요소의 주소를 처리 하는 상수 반복기를 반환 합니다.|
|[remove_prefix](#remove_prefix)|포인터를 지정 된 요소 수 만큼 앞으로 이동 합니다.|
|[remove_suffix](#remove_suffix)|뒤로부터 지정 된 요소 수 만큼 뷰의 크기를 줄입니다.|
|[rend](#rend)|역방향 string_view에서 마지막 요소를 지난 요소를 가리키는 상수 반복기를 반환 합니다.|
|[rfind](#rfind)|String_view에서 지정 된 문자 시퀀스와 일치 하는 첫 번째 하위 문자열을 역방향으로 검색 합니다.|
|[size](#size)|현재 요소 수를 반환 합니다.|
|[starts_with](#starts_with)<sup>c + + 20</sup>|문자열 뷰가 지정 된 접두사로 시작 하는지 여부를 확인 합니다.|
|[substr](#substr)|지정 된 인덱스에서 시작 하 여 지정 된 길이의 부분 문자열을 반환 합니다.|
|[스왑을](#swap)|두 string_views의 내용을 교환 합니다.|

## <a name="remarks"></a>설명

함수는 [max_size](#max_size) 요소보다 긴 시퀀스를 생성하라는 요청을 받으면 [length_error](../standard-library/length-error-class.md) 형식의 개체를 throw하여 길이 오류를 보고합니다.

## <a name="requirements"></a>요구 사항

[std: c + + 17](../build/reference/std-specify-language-standard-version.md) 이상

**헤더:**\<string_view>

**네임스페이스:** std

## <a name="basic_string_viewat"></a><a name="at"></a> basic_string_view:: at

지정 된 인덱스 (0부터 사용)의 문자에 대 한 const_reference를 반환 합니다.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>매개 변수

*이동*\
참조할 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

매개 변수 인덱스에 지정 된 위치에 있는 문자에 대 한 const_reference입니다.

### <a name="remarks"></a>설명

첫 번째 요소의 인덱스는 0이 고 다음 요소는 양의 정수로 연속적으로 인덱싱됩니다. 따라서 길이 *n* 의 string_view n 번째 요소가 숫자 *n-* 1로 인덱싱된 *n*번째 요소가 있습니다. **에서** [ \[ 연산자 \] ](#op_at)와는 달리 잘못 된 인덱스에 대해 예외를 throw 합니다.

일반적으로 및 string_view와 같은 **시퀀스에는를** 사용 하지 않는 것이 좋습니다 `std::vector` . 시퀀스에 전달 된 잘못 된 인덱스는 개발 중에 검색 되 고 수정 되어야 하는 논리 오류입니다. 프로그램에서 해당 인덱스가 유효 하다 고 확신할 수 없는 경우 ()에서 호출 하는 것이 아니라 테스트를 수행 하 고 부주의 프로그래밍을 방지 하기 위해 예외를 사용 합니다.

자세한 내용은 [basic_string_view:: \[ \] operator](#op_at) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a> basic_string_view:: back

마지막 요소에 대 한 const_reference를 반환 합니다.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>반환 값

String_view의 마지막 요소에 대 한 const_reference입니다.

### <a name="remarks"></a>설명

String_view 비어 있는 경우 예외를 throw 합니다.

예를 들어를 호출 하 여 string_view를 수정한 후에는 `remove_suffix` 이 함수에서 반환 된 요소가 더 이상 기본 데이터의 마지막 요소가 되지 않는다는 점에 유의 하세요.

### <a name="example"></a>예제

`string_view`C 문자열 리터럴을 사용 하 여 생성 된에는 종료 null이 포함 되지 않습니다. 따라서 다음 예제에서는을 `back` 반환 `'p'` 하 고는 반환 하지 않습니다 `'\0'` .

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

포함 된 null은 다른 문자로 처리 됩니다.

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a> basic_string_view:: basic_string_view

String_view를 생성 합니다.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>매개 변수

*문자열*\
문자 값에 대 한 포인터입니다.

*길이가*\
뷰에 포함할 문자 수입니다.

### <a name="remarks"></a>설명

차트 * 매개 변수를 사용 하는 생성자는 입력이 null로 종료 된 것으로 가정 하지만 종료 null은 string_view에 포함 되지 않습니다.

리터럴을 사용 하 여 string_view을 생성할 수도 있습니다. [연산자 "" sv](string-view-operators.md#op_sv)를 참조 하세요.

## <a name="basic_string_viewbegin"></a><a name="begin"></a> basic_string_view:: begin

[Cbegin](#cbegin)과 동일 합니다.

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>반환 값

첫 번째 요소를 주소 지정 하는 const_iterator을 반환 합니다.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a> basic_string_view:: cbegin

범위에 있는 첫 번째 요소의 주소를 처리 하는 const_iterator를 반환 합니다.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 임의 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

## <a name="basic_string_viewcend"></a><a name="cend"></a> basic_string_view:: cend

범위에서 마지막 요소 바로 다음 위치의 주소를 나타내는 const_iterator을 반환 합니다.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>반환 값

**`const`** 범위 끝의 바로 다음을 가리키는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

에서 반환 된 값은 `cend` 역참조 되지 않아야 합니다.

## <a name="basic_string_viewcompare"></a><a name="compare"></a> basic_string_view::compare

는 지정 된 string_view (또는 변환 가능한 문자열 형식)에 대 한 대/소문자를 구분 하 여 두 개체가 같은지 또는 한 개체가 다른 개체 보다 사전순으로 여부를 확인 합니다. [ \<string_view> 연산자](string-view-operators.md) 는이 멤버 함수를 사용 하 여 비교를 수행 합니다.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>매개 변수

*strv*\
이 string_view와 비교할 string_view입니다.

*pos*\
비교가 시작 되는이 string_view의 인덱스입니다.

*num*\
이 string_view에서 비교할 최대 문자 수입니다.

*num2*\
비교할 *strv* 의 최대 문자 수입니다.

*이동*\
비교가 시작 되는 *strv* 의 인덱스입니다.

*ptr*\
이 string_view 비교할 C 문자열입니다.

### <a name="return-value"></a>반환 값

- 이 값이 `string_view` *strv* 또는 *ptr* 보다 작은 경우 음수 값입니다.
- 두 문자 시퀀스가 같으면 0입니다.
- 이 값이 `string_view` *strv* 또는 *ptr* 보다 큰 경우 양수 값입니다.

### <a name="remarks"></a>설명

`compare`멤버 함수는 각 문자 시퀀스의 전체 또는 일부에 대 한 대/소문자를 구분 하는 비교를 수행 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a> basic_string_view:: copy

소스 string_view의 인덱싱된 위치에서 대상 문자 배열로 지정 된 수 만큼의 문자를 복사 합니다. 대신 보안 함수 [basic_string_view:: _Copy_s](#_copy_s) 를 사용 하는 것이 좋습니다.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*ptr*\
요소를 복사할 대상 문자 배열입니다.

*수*\
원본 string_view에서 복사할 문자 수입니다.

*이동*\
복사본을 만들 원본 string_view의 시작 위치입니다.

### <a name="return-value"></a>반환 값

복사한 문자 수입니다.

### <a name="remarks"></a>설명

Null 문자는 복사본의 끝에 추가되지 않습니다.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a> basic_string_view:: _Copy_s

[복사](#copy)대신 사용 되는 보안 CRT 복사 함수를 사용 합니다.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>매개 변수

*dest*\
요소를 복사할 대상 문자 배열입니다.

*dest_size*\
*대상*의 크기입니다.

_ 원본 문자열부터 복사할 문자 수를 *계산* 합니다.

*_Off*\
복사본을 만들 원본 문자열의 시작 위치입니다.

### <a name="return-value"></a>반환 값

복사한 문자 수입니다.

### <a name="remarks"></a>설명

Null 문자는 복사본의 끝에 추가되지 않습니다.

자세한 내용은 [c 런타임 라이브러리/보안](../c-runtime-library/security-features-in-the-crt.md)기능-crt를 참조 하세요.

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a> basic_string_view:: crbegin

역방향 string_view에서 첫 번째 요소의 주소를 처리 하는 const_reverse_iterator를 반환 합니다.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 string_view에서 첫 번째 요소의 주소를 처리 하는 const_reverse_iterator입니다.

## <a name="basic_string_viewcrend"></a><a name="crend"></a> basic_string_view:: crend

[Rend](#rend)와 동일 합니다.

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 string_view의 끝을 지나서 주소를 const_reverse_iterator를 반환 합니다.

## <a name="basic_string_viewdata"></a><a name="data"></a> basic_string_view: ata:d

String_view를 생성 하는 데 사용 된 개체의 const 문자 시퀀스에 대 한 소유 하지 않은 원시 포인터를 반환 합니다.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>반환 값

문자 시퀀스의 첫 번째 요소에 대 한 const 포인터입니다.

### <a name="remarks"></a>설명

포인터는 문자를 수정할 수 없습니다.

String_view 문자의 시퀀스가 반드시 null로 종료 되는 것은 아닙니다. Null 문자는 추가 되지 않으므로의 반환 형식은 `data` 유효한 C 문자열이 아닙니다. Null 문자 ' \ 0 '은 string_view 형식의 개체에서 특별 한 의미가 없으며 다른 문자와 마찬가지로 string_view 개체의 일부일 수 있습니다.

## <a name="basic_string_viewempty"></a><a name="empty"></a> basic_string_view:: empty

String_view에 문자가 포함 되어 있는지 여부를 테스트 합니다.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** string_view 개체에 문자가 포함 되어 있지 않으면이 고, 그렇지 않으면입니다. **`false`** 하나 이상의 문자가 있는 경우입니다.

### <a name="remarks"></a>설명

멤버 함수는 [size](#size)() = = 0과 동일 합니다.

## <a name="basic_string_viewend"></a><a name="end"></a> basic_string_view:: end

마지막 요소를 지난 요소를 가리키는 임의 액세스 const_iterator을 반환 합니다.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>반환 값

마지막 요소를 지난 요소를 가리키는 임의 액세스 const_iterator을 반환 합니다.

### <a name="remarks"></a>설명

`end` 는 const_iterator string_view의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다. 에서 반환 된 값은 `end` 역참조 되지 않아야 합니다.

## <a name="basic_string_viewends_with"></a><a name="ends_with"></a> basic_string_view:: ends_with

문자열 뷰가 지정 된 접미사로 끝나는지 여부를 확인 합니다.

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>매개 변수

*c*\
찾을 단일 문자 접미사입니다.

*sv*\
찾을 접미사를 포함 하는 문자열 뷰입니다.
를 전달 하 여 `std::basic_string` 문자열 뷰로 변환 합니다.

*.x*\
찾을 접미사를 포함 하는 Null로 끝나는 문자열입니다.

### <a name="return-value"></a>반환 값

`true` 문자열 뷰가 지정 된 접미사로 끝나면이 고, 그렇지 않으면입니다. `false` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

`ends_with()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

문자열 뷰가 지정 된 접두사로 시작 하는지 확인 하려면 [starts_with](#starts_with) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").ends_with('g') << '\n';
    std::cout << std::string_view("abcdefg").ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << std::string_view("abcdefg").ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_string_viewfind"></a><a name="find"></a> basic_string_view:: find

에서 `string_view` 지정 된 문자 시퀀스와 일치 하는 첫 번째 문자 또는 부분 문자열을 앞으로 검색 합니다.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*문자열*\
`string_view`멤버 함수가 검색할입니다.

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
첫 번째 문자부터 앞으로 계산 되는 *ptr*의 문자 수입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string_view:: find_first_not_of

지정 된 string_view 또는 변환할 수 있는 문자열 개체의 요소가 아닌 첫 번째 문자를 검색 합니다.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*문자열*\
멤버 함수가 검색할 string_view입니다.

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열에서 첫 번째 문자부터 앞으로 계산 되는 문자 수입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a> basic_string_view:: find_first_of

지정 된 string_view의 요소와 일치 하는 첫 번째 문자를 검색 합니다.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열에서 첫 번째 문자부터 앞으로 계산 되는 문자 수입니다.

*문자열*\
멤버 함수가 검색할 string_view입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string_view:: find_last_not_of

지정 된 string_view의 요소가 아닌 마지막 문자를 검색 합니다.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*문자열*\
멤버 함수가 검색할 string_view입니다.

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색이 완료 될 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
첫 번째 문자에서 앞으로 계산 되는 문자 수입니다 ( *ptr*).

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `string_view::npos`입니다.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a> basic_string_view:: find_last_of

지정 된 string_view의 요소와 일치 하는 마지막 문자를 검색 합니다.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*문자열*\
멤버 함수가 검색할 string_view입니다.

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색이 완료 될 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열에서 첫 번째 문자부터 앞으로 계산 되는 문자 수입니다.

### <a name="return-value"></a>반환 값

성공 시 검색되는 부분 문자열의 마지막 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

## <a name="basic_string_viewfront"></a><a name="front"></a> basic_string_view:: front

첫 번째 요소에 대 한 const_reference를 반환 합니다.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>반환 값

첫 번째 요소에 대 한 const_reference입니다.

### <a name="remarks"></a>설명

String_view 비어 있는 경우 예외를 throw 합니다.

## <a name="basic_string_viewlength"></a><a name="length"></a> basic_string_view::length

현재 요소 수를 반환 합니다.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>설명

멤버 함수는 [size](#size)와 동일합니다.

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a> basic_string_view:: max_size

String_view 포함할 수 있는 최대 문자 수를 반환 합니다.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>반환 값

String_view에 포함할 수 있는 최대 문자 수입니다.

### <a name="remarks"></a>설명

작업에서 길이가 보다 큰 string_view을 생성 하는 경우 [length_error](../standard-library/length-error-class.md) 형식의 예외가 throw 됩니다 `max_size()` .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a> basic_string_view:: operator =

String_view 또는 변환할 수 있는 문자열 개체를 다른 string_view에 할당 합니다.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>예제

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a> basic_string_view:: operator []

지정 된 인덱스를 사용 하 여 문자에 대 한 const_reference를 제공 합니다.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>매개 변수

*이동*\
참조할 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

매개 변수 인덱스에 지정 된 위치에 있는 문자에 대 한 const_reference입니다.

### <a name="remarks"></a>설명

첫 번째 요소의 인덱스는 0이 고, 다음 요소는 양의 정수로 연속적으로 인덱싱됩니다. 따라서 길이 *n* 의 string_view *n 번째 요소가*숫자 *n* -1로 인덱싱됩니다.

`operator[]` 는 string_view의 요소에 대 한 읽기 권한을 제공 [하기 위해의](#at) 멤버 함수 보다 빠릅니다.

`operator[]` 는 인수로 전달 된 인덱스가 유효한 지 여부를 확인 하지 않습니다. 에 잘못 된 인덱스가 전달 되 면 `operator[]` 정의 되지 않은 동작이 발생 합니다.

소유 하는 개체에서 기본 문자열 데이터를 수정 하거나 삭제 하는 경우 반환 되는 참조가 무효화 될 수 있습니다.

[ \_ 반복기 \_ 디버그 \_ 수준](../standard-library/iterator-debug-level.md) 을 1 또는 2로 설정 하 여 컴파일할 때 string_view 범위를 벗어난 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다. 자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a> basic_string_view:: rbegin

역방향 string_view의 첫 번째 요소에 대 한 const 반복기를 반환 합니다.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 string_view의 첫 번째 요소에 대 한 임의 액세스 반복기를 반환 하 여 해당 하는 역방향이 해제 된 string_view에서 마지막 요소가 될 항목을 해결 합니다.

### <a name="remarks"></a>설명

`rbegin` 는 [begin](#begin) 이 string_view에서 사용 되는 것 처럼 역방향 string_view와 함께 사용 됩니다. `rbegin` 반복을 뒤로 초기화 하는 데 사용할 수 있습니다.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a> basic_string_view::remove_prefix

포인터를 지정 된 요소 수 만큼 앞으로 이동 합니다.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>설명

기본 데이터를 변경 되지 않은 상태로 유지 합니다. String_view 포인터를 n 개 요소 앞으로 이동 하 고 개인 `size` 데이터 멤버를 크기-n으로 설정 합니다.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a> basic_string_view::remove_suffix

뒤로부터 지정 된 요소 수 만큼 뷰의 크기를 줄입니다.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>설명

기본 데이터와 포인터를 변경 하지 않고 그대로 둡니다. Private `size` 데이터 멤버를 size-n으로 설정 합니다.

## <a name="basic_string_viewrend"></a><a name="rend"></a> basic_string_view:: rend

역방향 string_view에서 마지막 요소를 지난 요소를 가리키는 상수 반복기를 반환 합니다.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>반환 값

역방향 string_view에서 마지막 요소를 지난 요소를 가리키는 const 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`rend` 는 string_view에서 [end](#end) 가 사용 되는 것 처럼 역방향 string_view와 함께 사용 됩니다. `rend` 는 역방향 반복기가 string_view 끝에 도달 했는지 여부를 테스트 하는 데 사용할 수 있습니다. 에서 반환 된 값은 `rend` 역참조 되지 않아야 합니다.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a> basic_string_view:: rfind

String_view에서 지정 된 문자 시퀀스와 일치 하는 하위 문자열을 역방향으로 검색 합니다.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*chVal*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열에서 첫 번째 문자부터 앞으로 계산 되는 문자 수입니다.

*문자열*\
멤버 함수가 검색할 string_view입니다.

### <a name="return-value"></a>반환 값

성공할 경우 하위 문자열의 첫 번째 문자 인덱스입니다. 그렇지 않으면 `npos` 입니다.

## <a name="basic_string_viewsize"></a><a name="size"></a> basic_string_view:: size

String_view의 요소 수를 반환 합니다.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>반환 값

String_view의 길이입니다.

### <a name="remarks"></a>설명

String_view는 및 등의 길이를 수정할 수 있습니다 `remove_prefix` `remove_suffix` . 이는 기본 문자열 데이터를 수정 하지 않으므로 string_view의 크기는 기본 데이터의 크기가 아닐 수도 있습니다.

## <a name="basic_string_viewstarts_with"></a><a name="starts_with"></a> basic_string_view:: starts_with

문자열 뷰가 지정 된 접두사로 시작 하는지 여부를 확인 합니다.

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>매개 변수

*c*\
찾을 단일 문자 접두사입니다.

*sv*\
찾을 접두사를 포함 하는 문자열 뷰입니다.
를 전달 하 여 `std::basic_string` 문자열 뷰로 변환 합니다.

*.x*\
찾을 접두사를 포함 하는 Null로 끝나는 문자열입니다.

### <a name="return-value"></a>반환 값

`true` 문자열이 지정 된 접두사로 시작 하면이 고, 그렇지 않으면입니다. `false` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

`starts_with()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

문자열이 접미사로 끝나는지 여부를 확인 하려면 [ends_with](#ends_with) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").starts_with('b') << '\n';
    std::cout << std::string_view("abcdefg").starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << std::string_view("abcdefg").starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_string_viewsubstr"></a><a name="substr"></a> basic_string_view:: substr

지정 된 위치에서 (최대) 지정 된 수의 문자를 나타내는 string_view을 반환 합니다.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>매개 변수

*이동*\
복사본이 생성 된 위치에서 요소를 찾는 인덱스 이며 기본값은 0입니다.

*수*\
하위 문자열 (있는 경우)에 포함할 문자 수입니다.

### <a name="return-value"></a>반환 값

지정 된 요소 하위 시퀀스를 나타내는 string_view 개체입니다.

## <a name="basic_string_viewswap"></a><a name="swap"></a> basic_string_view:: swap

두 개의 string_views, 즉 기본 문자열 데이터에 대 한 포인터와 크기 값을 교환 합니다.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>매개 변수

*sv*\
대상 string_view와 포인터 및 크기 값을 교환할 원본 string_view입니다.

## <a name="see-also"></a>참고 항목

[\<string_view>](../standard-library/string-view.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
