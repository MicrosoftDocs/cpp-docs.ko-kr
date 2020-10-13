---
title: path 클래스
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: fb56afbc1d29f1d321b394342382f89b06768720
ms.sourcegitcommit: b5854134553db1d99a5761bec131841c374a3098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91958661"
---
# <a name="path-class"></a>path 클래스

**Path** 클래스는 표시의 목적으로 여기에 호출 되는 형식의 개체를 저장 `string_type` `myname` 합니다. 경로 이름으로 사용 하는 데 적합 합니다. `string_type` 는의 동의어입니다 `basic_string<value_type>` . 여기서 `value_type` 은 **`wchar_t`** Windows 또는 POSIX의 동의어입니다 **`char`** .

자세한 내용 및 코드 예제를 보려면 [파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
class path;
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[path](#path)|`path`를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[const_iterator](#const_iterator)|`iterator`의 동의어입니다.|
|[반복](#iterator)|의 구성 요소를 지정 하는 양방향 상수 반복기입니다 `path` `myname` .|
|[string_type](#string_type)|이 형식은 `basic_string<value_type>`의 동의어입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[append](#append)|필요에 따라 preferred_separator를 변환 하 고 삽입 하 여 지정 된 시퀀스를 추가 `mypath` 합니다.|
|[assign](#assign)|`mypath`필요에 따라 변환 된 지정 된 시퀀스로 대체 합니다.|
|[시작](#begin)|`path::iterator`경로 이름에서 첫 번째 경로 요소를 지정 하는를 반환 합니다 (있는 경우).|
|[c_str](#c_str)|의 첫 번째 문자에 대 한 포인터를 반환 합니다 `mypath` .|
|[clear](#clear)|`mypath.clear()`를 실행 합니다.|
|[과](#compare)|비교 값을 반환 합니다.|
|[concat](#compare)|`mypath`필요에 따라 변환 되었지만 구분 기호를 삽입 하지 않는 지정 된 시퀀스를에 추가 합니다.|
|[empty](#empty)|`mypath.empty()`를 반환합니다.|
|[end](#end)|형식의 시퀀스의 끝 반복기를 반환 합니다 `iterator` .|
|[확장](#extension)|의 접미사를 반환 합니다 `filename()` .|
|[filename](#filename)|myname의 루트 디렉터리 구성 요소(구체적으로는 `empty() ? path() : *--end()`)를 반환합니다. 구성 요소는 비어 있을 수 있습니다.|
|[generic_string](#generic_string)|슬래시로 변환된 백슬래시와 함께 `this->string<Elem, Traits, Alloc>(al)`를 반환합니다(Windows).|
|[generic_u16string](#generic_u16string)|슬래시로 변환된 백슬래시와 함께 `u16string()`를 반환합니다(Windows).|
|[generic_u32string](#generic_u32string)|슬래시로 변환된 백슬래시와 함께 `u32string()`를 반환합니다(Windows).|
|[generic_u8string](#generic_u8string)|슬래시로 변환된 백슬래시와 함께 `u8string()`를 반환합니다(Windows).|
|[generic_wstring](#generic_wstring)|슬래시로 변환된 백슬래시와 함께 `wstring()`를 반환합니다(Windows).|
|[has_extension](#has_extension)|`!extension().empty()`를 반환합니다.|
|[has_filename](#has_filename)|`!filename().empty()`를 반환합니다.|
|[has_parent_path](#has_parent_path)|`!parent_path().empty()`를 반환합니다.|
|[has_relative_path](#has_relative_path)|`!relative_path().empty()`를 반환합니다.|
|[has_root_directory](#has_root_directory)|`!root_directory().empty()`를 반환합니다.|
|[has_root_name](#has_root_name)|`!root_name().empty()`를 반환합니다.|
|[has_root_path](#has_root_path)|`!root_path().empty()`를 반환합니다.|
|[has_stem](#has_stem)|`!stem().empty()`를 반환합니다.|
|[is_absolute](#is_absolute)|Windows의 경우 함수는를 반환 `has_root_name() && has_root_directory()` 합니다. POSIX의 경우 함수는를 반환 `has_root_directory()` 합니다.|
|[is_relative](#is_relative)|`!is_absolute()`를 반환합니다.|
|[make_preferred](#make_preferred)|필요에 따라 각 구분 기호를 preferred_separator 변환 합니다.|
|[native](#native)|`myname`를 반환합니다.|
|[parent_path](#parent_path)|의 부모 경로 구성 요소를 반환 합니다 `myname` .|
|[preferred_separator](#preferred_separator)|상수 개체는 호스트 운영 체제에 따라 경로 구성 요소를 구분하는 기본 문자를 제공합니다. |
|[relative_path](#relative_path)|의 상대 경로 구성 요소를 반환 합니다 `myname` . |
|[remove_filename](#remove_filename)|파일 이름을 제거 합니다.|
|[replace_extension](#replace_extension)|의 확장을 바꿉니다 `myname` . |
|[replace_filename](#replace_filename)|파일 이름을 바꿉니다.|
|[root_directory](#root_directory)|의 루트 디렉터리 구성 요소를 반환 합니다 `myname` . |
|[root_name](#root_name)|의 루트 이름 구성 요소를 반환 합니다 `myname` . |
|[root_path](#root_path)|의 루트 경로 구성 요소를 반환 합니다 `myname` .|
|[stem](#stem)|`stem`의 구성 요소를 반환 합니다 `myname` .|
|[string](#string)|에 저장 된 시퀀스를 변환 합니다 `mypath` .|
|[스왑을](#swap)|`swap(mypath, right.mypath)`를 실행 합니다.|
|[u16string](#u16string)|에 저장 된 시퀀스를 `mypath` u t f-16으로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u16string` .|
|[u32string](#u32string)|에 저장 된 시퀀스를 `mypath` u t f-32로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u32string` .|
|[u8string](#u8string)|에 저장 된 시퀀스를 `mypath` u t f-8로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u8string` .|
|[value_type](#value_type)|형식은 호스트 운영 체제에서 선호하는 경로 요소를 설명합니다.|
|[wstring](#wstring)|에 저장 된 시퀀스를 `mypath` 시퀀스에 대해 호스트 시스템에서 선호 하는 인코딩으로 변환 하 **`wchar_t`** 고 형식의 개체에 저장 된 대로 반환 합니다 `wstring` .|

### <a name="operators"></a>연산자

|연산자|Description|
|-|-|
|[연산자 =](#op_as)|경로의 요소를 다른 경로의 복사본으로 바꿉니다.|
|[operator + =](#op_add)|다양 한 `concat` 식입니다.|
|[operator/=](#op_divide)|다양 한 `append` 식입니다.|
|[operator string_type](#op_string)|`myname`를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<filesystem>

**네임스페이스:** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a> 경로:: append

필요한 경우 지정 된 시퀀스를에 추가 하 `mypath` 고, 변환 하 고, 삽입 합니다 `preferred_separator` .

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>매개 변수

*원본*\
지정 된 시퀀스입니다.

*기본*\
지정 된 시퀀스의 시작입니다.

*최신*\
지정 된 시퀀스의 끝입니다.

## <a name="pathassign"></a><a name="assign"></a> path:: assign

`mypath`필요에 따라 변환 된 지정 된 시퀀스로 대체 합니다.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>매개 변수

*원본*\
지정 된 시퀀스입니다.

*기본*\
지정 된 시퀀스의 시작입니다.

*최신*\
지정 된 시퀀스의 끝입니다.

## <a name="pathbegin"></a><a name="begin"></a> path:: begin

`path::iterator`경로 이름에서 첫 번째 경로 요소를 지정 하는를 반환 합니다 (있는 경우).

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a> 경로:: c_str

의 첫 번째 문자에 대 한 포인터를 반환 합니다 `mypath` .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a> 경로:: clear

`mypath.clear()`를 실행 합니다.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a> path:: compare

첫 번째 함수는 `mypath.compare(pval.native())`를 반환합니다. 두 번째 함수는 `mypath.compare(str)`를 반환합니다. 세 번째 함수는를 반환 합니다 `mypath.compare(ptr)` .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>매개 변수

*pval*\
비교할 경로입니다.

*문자열*\
비교할 문자열입니다.

*ptr*\
비교할 포인터입니다.

## <a name="pathconcat"></a><a name="concat"></a> 경로:: concat

`mypath`필요에 따라 변환 되었지만 구분 기호를 삽입 하지 않는 지정 된 시퀀스를에 추가 합니다.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>매개 변수

*원본*\
지정 된 시퀀스입니다.

*기본*\
지정 된 시퀀스의 시작입니다.

*최신*\
지정 된 시퀀스의 끝입니다.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a> 경로:: const_iterator

`iterator`의 동의어입니다.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a> path:: empty

`mypath.empty()`를 반환합니다.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a> 경로:: end

형식의 시퀀스의 끝 반복기를 반환 합니다 `iterator` .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a> path:: extension

의 접미사를 반환 합니다 `filename()` .

```cpp
path extension() const;
```

### <a name="remarks"></a>설명

는 다음과 같은의 접미사를 반환 합니다 `filename() X` .

`X == path(".") || X == path("..")`또는 `X` 에 점이 없는 경우 접미사가 비어 있습니다.

그렇지 않은 경우 접미사가 맨 오른쪽 점으로 시작되고 해당 점을 포함합니다.

## <a name="pathfilename"></a><a name="filename"></a> 경로:: filename

myname의 루트 디렉터리 구성 요소(구체적으로는 `empty() path() : *--end()`)를 반환합니다. 구성 요소는 비어 있을 수 있습니다.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a> 경로:: generic_string

슬래시로 변환된 백슬래시와 함께 `this->string<Elem, Traits, Alloc>(al)`를 반환합니다(Windows).

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a> 경로:: generic_u16string

슬래시로 변환된 백슬래시와 함께 `u16string()`를 반환합니다(Windows).

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a> 경로:: generic_u32string

슬래시로 변환된 백슬래시와 함께 `u32string()`를 반환합니다(Windows).

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a> 경로:: generic_u8string

슬래시로 변환된 백슬래시와 함께 `u8string()`를 반환합니다(Windows).

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a> 경로:: generic_wstring

슬래시로 변환된 백슬래시와 함께 `wstring()`를 반환합니다(Windows).

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a> 경로:: has_extension

`!extension().empty()`를 반환합니다.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a> 경로:: has_filename

`!filename().empty()`를 반환합니다.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a> 경로:: has_parent_path

`!parent_path().empty()`를 반환합니다.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a> 경로:: has_relative_path

`!relative_path().empty()`를 반환합니다.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a> 경로:: has_root_directory

`!root_directory().empty()`를 반환합니다.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a> 경로:: has_root_name

`!root_name().empty()`를 반환합니다.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a> 경로:: has_root_path

`!root_path().empty()`를 반환합니다.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a> 경로:: has_stem

`!stem().empty()`를 반환합니다.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a> 경로:: is_absolute

Windows의 경우 함수는를 반환 `has_root_name() && has_root_directory()` 합니다. POSIX의 경우 함수는를 반환 `has_root_directory()` 합니다.

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a> 경로:: is_relative

`!is_absolute()`를 반환합니다.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a> path:: iterator

의 경로 구성 요소를 지정 하는 양방향 상수 반복기입니다 `myname` .

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>설명

이 클래스는 `path` 시퀀스에서의 구성 요소를 지정 하는 양방향 상수 반복기를 설명 합니다 `myname` .

1. 루트 이름(있는 경우)

1. 루트 디렉터리(있는 경우)

1. 파일 이름 (있는 경우)으로 끝나는 부모의 나머지 디렉터리 요소 (있는 경우) `path`

`pval`다음 유형의 개체 `path` :

1. `path::iterator X = pval.begin()``path`경로 이름에서 첫 번째 요소를 지정 합니다 (있는 경우).

1. `X == pval.end()` 가 `X` 구성 요소 시퀀스의 끝을 지나서 있는 경우는 true입니다.

1. `*X` 현재 구성 요소와 일치 하는 문자열을 반환 합니다.

1. `++X`는 시퀀스에서 다음 구성 요소(있는 경우)를 지정합니다.

1. `--X`는 시퀀스에서 이전 구성 요소(있는 경우)를 지정합니다.

1. 변경 하면 `myname` 에서 요소를 지정 하는 모든 반복기가 무효화 `myname` 됩니다.

## <a name="pathmake_preferred"></a><a name="make_preferred"></a> 경로:: make_preferred

필요에 따라 각 구분 기호를로 변환 합니다 `preferred_separator` .

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a> path:: native

`myname`를 반환합니다.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a> path:: operator =

경로의 요소를 다른 경로의 복사본으로 바꿉니다.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`path`에 복사할 [경로](../standard-library/path-class.md)입니다.

*원본*\
원본 경로입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 연산자는 `right.myname` 를로 복사 `myname` 합니다. 두 번째 멤버 연산자는 `right.myname` 로 이동 `myname` 합니다. 세 번째 멤버 연산자는와 동일 하 게 동작 합니다 `*this = path(source)` .

## <a name="pathoperator"></a><a name="op_add"></a> path:: operator + =

다양 한 `concat` 식입니다.

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
추가 된 경로입니다.

*문자열*\
추가 된 문자열입니다.

*ptr*\
추가 된 포인터입니다.

*e*\
추가 된 `value_type` 또는 `Elem` 입니다.

*원본*\
추가 된 원본입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 해당 식과 동일하게 작동합니다.

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a> path:: operator/=

다양 한 `append` 식입니다.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
추가 된 경로입니다.

*원본*\
추가 된 원본입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 해당 식과 동일하게 작동합니다.

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a> path:: operator string_type

`myname`를 반환합니다.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a> 경로::p arent_path

의 부모 경로 구성 요소를 반환 합니다 `myname` .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>설명

는의 부모 경로 구성 요소 `myname` , 특히를 `myname` 제거한 후의 접두사 `filename().native()` 와 바로 앞의 디렉터리 구분 기호를 반환 합니다. 동일 하 게 적용 하는 경우 `begin() != end()` 범위에 있는 모든 요소를 연속적으로 `[begin(), --end())` 적용 하 여 결합 합니다 `operator/=` . 구성 요소가 비어 있을 수 있습니다.

## <a name="pathpath"></a><a name="path"></a> 경로::p a

`path`여러 가지 방법으로을 생성 합니다.

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
생성 된 경로가 복사본으로 지정할 경로입니다.

*원본*\
생성 된 경로를 복사할 원본입니다.

*loc*\
지정 된 로캘입니다.

*기본*\
복사할 첫 번째 요소의 위치입니다.

*최신*\
복사할 마지막 요소의 위치입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같은 `myname` 다양 한 방법으로 구성 됩니다.

`path()`는 `myname()` 입니다.

의 경우 `path(const path& right` )입니다 `myname(right.myname)` .

`path(path&& right)`는 `myname(right.myname)` 입니다.

`template<class Source> path(const Source& source)`는 `myname(source)` 입니다.

`template<class Source> path(const Source& source, const locale& loc)`그 이유는 `myname(source)` 에서 필요한 codecvt 패싯을 가져오는 것입니다 `loc` .

`template<class InIt> path(InIt first, InIt last)`는 `myname(first, last)` 입니다.

`template<class InIt> path(InIt first, InIt last, const locale& loc)`그 이유는 `myname(first, last)` 에서 필요한 codecvt 패싯을 가져오는 것입니다 `loc` .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a> 경로::p referred_separator

상수 개체는 호스트 운영 체제에 따라 경로 구성 요소를 구분하는 기본 문자를 제공합니다.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>설명

대부분의 Windows 컨텍스트에서는 L'/'을 대신 사용하여 동일하게 허용됩니다.

## <a name="pathrelative_path"></a><a name="relative_path"></a> 경로:: relative_path

의 상대 경로 구성 요소를 반환 합니다 `myname` .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>설명

는의 상대 경로 구성 요소 `myname` , 특히를 `myname` 제거한 후의 접미사 `root_path().native()` 및 즉시 중복 디렉터리 구분 기호를 반환 합니다. 구성 요소는 비어 있을 수 있습니다.

## <a name="pathremove_filename"></a><a name="remove_filename"></a> 경로:: remove_filename

파일 이름을 제거 합니다.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a> 경로:: replace_extension

의 확장을 바꿉니다 `myname` .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>매개 변수

*newext*\
새 확장명입니다.

### <a name="remarks"></a>설명

는 먼저에서 접미사를 제거 합니다 `extension().native()` `myname` . 그런 다음 `!newext.empty() && newext[0] != dot` ( `dot` 가 인 경우 `*path(".").c_str()` ) `dot` 가에 추가 됩니다 `myname` . 그런 다음 *newext* 가에 추가 됩니다 `myname` .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a> 경로:: replace_filename

파일 이름을 바꿉니다.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>매개 변수

*pval*\
파일 이름의 경로입니다.

### <a name="remarks"></a>설명

멤버 함수에서 다음을 실행합니다.

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a> 경로:: root_directory

의 루트 디렉터리 구성 요소를 반환 합니다 `myname` .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>설명

구성 요소는 비어 있을 수 있습니다.

## <a name="pathroot_name"></a><a name="root_name"></a> 경로:: root_name

의 루트 이름 구성 요소를 반환 합니다 `myname` .

```cpp
path root_name() const;
```

### <a name="remarks"></a>설명

구성 요소는 비어 있을 수 있습니다.

## <a name="pathroot_path"></a><a name="root_path"></a> 경로:: root_path

의 루트 경로 구성 요소를 반환 합니다 `myname` .

```cpp
path root_path() const;
```

### <a name="remarks"></a>설명

특히의 루트 경로 구성 요소를 반환 합니다 `myname` `root_name()`  /  `root_directory` . 구성 요소는 비어 있을 수 있습니다.

## <a name="pathstem"></a><a name="stem"></a> path:: 스템

`stem`의 구성 요소를 반환 합니다 `myname` .

```cpp
path stem() const;
```

### <a name="remarks"></a>설명

는 `stem` 의 구성 요소를 반환 합니다 .이 구성 요소는 `myname` `filename().native()` 임의의 후행 제거를 포함 합니다 `extension().native()` . 구성 요소는 비어 있을 수 있습니다.

## <a name="pathstring"></a><a name="string"></a> path:: string

에 저장 된 시퀀스를 변환 합니다 `mypath` .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>설명

첫 번째 (템플릿) 멤버 함수는 다음과 같은 방식으로 저장 된 시퀀스를 변환 합니다 `mypath` .

1. `string<char, Traits, Alloc>()`의 경우 `string()`

1. `string<wchar_t, Traits, Alloc>()`의 경우 `wstring()`

1. `string<char16_t, Traits, Alloc>()`의 경우 `u16string()`

1. `string<char32_t, Traits, Alloc>()`의 경우 `u32string()`

두 번째 멤버 함수는에 저장 된 시퀀스를 `mypath` 시퀀스에 대해 호스트 시스템에서 선호 하는 인코딩으로 변환 하 **`char`** 고 형식의 개체에 저장 된 대로 반환 합니다 `string` .

## <a name="pathstring_type"></a><a name="string_type"></a> 경로:: string_type

이 형식은 `basic_string<value_type>`의 동의어입니다.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a> 경로:: swap

`swap(mypath, right.mypath)`를 실행 합니다.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a> 경로:: u16string

에 저장 된 시퀀스를 `mypath` u t f-16으로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u16string` .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a> 경로:: u32string

에 저장 된 시퀀스를 `mypath` u t f-32로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u32string` .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a> 경로:: u8string

에 저장 된 시퀀스를 `mypath` u t f-8로 변환 하 여 형식의 개체에 저장 된 대로 반환 합니다 `u8string` .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a> 경로:: value_type

형식은 `path` 호스트 운영 체제에서 선호 하는 요소를 설명 합니다.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a> path:: wstring

에 저장 된 시퀀스를 `mypath` 시퀀스에 대해 호스트 시스템에서 선호 하는 인코딩으로 변환 하 **`wchar_t`** 고 형식의 개체에 저장 된 대로 반환 합니다 `wstring` .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>추가 정보

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
