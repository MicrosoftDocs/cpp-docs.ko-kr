---
title: basic_string 클래스
description: '`basic_string`표준 c + + 문자열 클래스인 클래스에 대 한 API 참조입니다.'
ms.date: 9/10/2020
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::ends_with
- xstring/std::basic_string::starts_with
- xstring/std::basic_string::swap
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], starts_with
- std::basic_string [C++], ends_with
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 9012fc8203bf8b54e87e2c21f47f2ef6ef764c2d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040315"
---
# <a name="basic_string-class"></a>basic_string 클래스

형식의 개체에 의해 제어 되는 시퀀스는 `basic_string` 표준 c + + 문자열 클래스 이며 일반적으로 문자열 이라고 하며, c + + 표준 라이브러리 전체에서 사용 되는 null로 종료 되는 C 스타일 문자열과 혼동 해서는 안 됩니다. 표준 C++ 문자열은 비교/연결 작업, 반복기, C++ 표준 라이브러리 알고리즘, 클래스 할당자 관리 메모리 복사/할당 등의 일반 형식으로 문자열을 사용할 수 있는 컨테이너입니다. 표준 C++ 문자열을 null로 종료되는 C 스타일 문자열로 변환해야 하는 경우에는 [basic_string::c_str](#c_str) 멤버를 사용합니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>매개 변수

*CharType*\
문자열에 저장되는 단일 문자의 데이터 형식입니다. C + + 표준 라이브러리는이 클래스 템플릿의 특수화를 제공 합니다. 여기 [string](../standard-library/string-typedefs.md#string) 에는 형식의 요소 **`char`** , [wstring](../standard-library/string-typedefs.md#wstring), for **`wchar_t`** , [u16string](../standard-library/string-typedefs.md#u16string) for **`char16_t`** 및 [u32string](../standard-library/string-typedefs.md#u32string) 의 요소에 대 한 형식 정의 문자열이 포함 **`char32_t`** 됩니다.

*특징이*\
Basic_string 특수화의 요소에 대 한 다양 한 중요 한 속성 `CharType` 은 클래스에서 설명 `Traits` 합니다. 기본값은 `char_traits`< `CharType`>입니다.

*할당자*\
문자열의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 기본값은 `allocator<CharType>`입니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_string](#basic_string)|비어 있거나 특정 문자로 초기화된 문자열 또는 다른 문자열 개체나 C 문자열 일부 또는 전체의 복사본인 문자열을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|문자열 개체의 `allocator` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|문자열의 요소를 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|[const_pointer](#const_pointer)|문자열의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|[const_reference](#const_reference)|**`const`** 작업을 읽고 수행 하기 위해 문자열에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|문자열의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|[difference_type](#difference_type)|동일한 문자열 내의 요소를 참조하는 두 반복기 사이의 차이를 제공하는 형식입니다.|
|[반복](#iterator)|문자열에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.|
|[npos](#npos)|검색 함수가 실패할 때 "찾을 수 없음" 또는 "모든 나머지 문자"를 나타내는-1로 초기화 된 부호 없는 정수 값입니다.|
|[놓고](#pointer)|문자열 또는 문자 배열의 문자 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|문자열에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역방향 문자열에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|문자열의 요소 수에 대한 부호 없는 정수 형식입니다.|
|[traits_type](#traits_type)|문자열에 저장된 요소의 문자 특성 형식입니다.|
|[value_type](#value_type)|문자열에 저장된 문자의 형식을 나타내는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[append](#append)|문자열 끝에 문자를 추가합니다.|
|[assign](#assign)|문자열의 내용에 새 문자 값을 할당합니다.|
|[at](#at)|문자열의 지정된 위치에 있는 요소에 대한 참조를 반환합니다.|
|[뒤로](#back)||
|[시작](#begin)|문자열의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.|
|[c_str](#c_str)|문자열의 내용을 C 스타일의 null로 종료되는 문자열로 변환합니다.|
|[수용](#capacity)|문자열의 메모리 할당을 늘리지 않고도 문자열에 저장할 수 있는 요소의 최대 수를 반환합니다.|
|[cbegin](#cbegin)|문자열의 첫 번째 요소 주소를 지정하는 const 반복기를 반환합니다.|
|[cend](#cend)|문자열에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 const 반복기를 반환합니다.|
|[해제](#clear)|문자열의 모든 요소를 지웁니다.|
|[과](#compare)|문자열을 지정된 문자열과 비교하여 두 문자열이 같은지 아니면 한 문자열이 다른 문자열보다 사전순으로 더 작은지를 확인합니다.|
|[copy](#copy)|소스 문자열의 인덱싱된 위치에서 지정한 수까지의 문자를 대상 문자 배열에 복사합니다. 더 이상 사용되지 않습니다. 대신 [basic_string::_Copy_s](#copy_s)를 사용합니다.|
|[crbegin](#crbegin)|역방향 문자열에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.|
|[crend](#crend)|역방향 문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.|
|[_Copy_s](#copy_s)|소스 문자열의 인덱싱된 위치에서 지정한 수까지의 문자를 대상 문자 배열에 복사합니다.|
|[data](#data)|문자열의 내용을 문자 배열로 변환합니다.|
|[empty](#empty)|문자열에 문자가 있는지 테스트합니다.|
|[종단](#end)|문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.|
|[ends_with](#ends_with)<sup>c + + 20</sup>|문자열이 지정 된 접미사로 끝나는지 여부를 확인 합니다.|
|[erase](#erase)|문자열에서 지정된 위치의 요소 또는 요소 범위를 제거합니다.|
|[find](#find)|문자열에서 지정된 문자 시퀀스와 일치하는 첫 번째 하위 문자열을 정방향으로 검색합니다.|
|[find_first_not_of](#find_first_not_of)|문자열에서 지정 된 문자열의 요소가 아닌 첫 번째 문자를 검색 합니다.|
|[find_first_of](#find_first_of)|문자열에서 지정된 문자열의 요소와 일치하는 첫 번째 문자를 검색합니다.|
|[find_last_not_of](#find_last_not_of)|문자열에서 지정 된 문자열의 요소가 아닌 마지막 문자를 검색 합니다.|
|[find_last_of](#find_last_of)|문자열에서 지정된 문자열의 요소인 마지막 문자를 검색합니다.|
|[앞뒤](#front)|문자열의 첫 번째 요소에 대한 참조를 반환합니다.|
|[get_allocator](#get_allocator)|문자열을 생성하는 데 사용된 `allocator` 개체의 복사본을 반환합니다.|
|[insert](#insert)|요소 하나 또는 여러 개나 요소의 범위를 문자열의 지정된 위치에 삽입합니다.|
|[length](#length)|문자열의 현재 요소 수를 반환합니다.|
|[max_size](#max_size)|문자열이 포함할 수 있는 최대 문자 수를 반환합니다.|
|[pop_back](#pop_back)|문자열의 마지막 요소를 지웁니다.|
|[push_back](#push_back)|문자열 끝에 요소를 추가합니다.|
|[rbegin](#rbegin)|역방향 문자열에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.|
|[rend](#rend)|역방향 문자열에서 마지막 요소 바로 다음을 가리키는 반복기를 반환합니다.|
|[replace](#replace)|문자열에서 지정된 위치의 요소를 다른 범위 또는 문자열이나 C 문자열에서 복사한 문자 또는 지정된 문자로 바꿉니다.|
|[두기](#reserve)|문자열의 용량을 최소한 지정된 숫자보다 크게 설정합니다.|
|[조정해](#resize)|문자열의 새 크기를 지정하고 필요에 따라 요소를 추가하거나 지웁니다.|
|[rfind](#rfind)|문자열에서 지정된 문자 시퀀스와 일치하는 첫 번째 하위 문자열을 역방향으로 검색합니다.|
|[shrink_to_fit](#shrink_to_fit)|문자열의 초과 용량을 삭제합니다.|
|[size](#size)|문자열의 현재 요소 수를 반환합니다.|
|[starts_with](#starts_with)<sup>c + + 20</sup>|문자열이 지정 된 접두사로 시작 하는지 여부를 확인 합니다.|
|[substr](#substr)|지정된 위치부터 시작하여 문자열의 하위 문자열을 최대 특정 문자 수만큼 복사합니다.|
|[스왑을](#swap)|두 문자열의 내용을 교환합니다.|

### <a name="operators"></a>연산자

|연산자|Description|
|-|-|
|[operator + =](#op_add_eq)|문자열에 문자를 추가합니다.|
|[연산자 =](#op_eq)|문자열의 내용에 새 문자 값을 할당합니다.|
|[operator&#91;&#93;](#op_at)|문자열에서 지정된 인덱스에 있는 문자에 대한 참조를 제공합니다.|

## <a name="remarks"></a>설명

함수는 [max_size](#max_size) 요소보다 긴 시퀀스를 생성하라는 요청을 받으면 [length_error](../standard-library/length-error-class.md) 형식의 개체를 throw하여 길이 오류를 보고합니다.

제어 되는 시퀀스의 요소를 지정 하는 참조, 포인터 및 반복기는 제어 되는 시퀀스를 변경 하는 함수를 호출한 후 또는 멤버 함수가 아닌 함수를 처음 호출 하 고 나면 유효 하지 않을 수 있습니다 **`const`** .

## <a name="requirements"></a>요구 사항

**헤더:**\<string>

**네임스페이스:** std

## <a name="basic_stringallocator_type"></a><a name="allocator_type"></a> basic_string:: allocator_type

문자열 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Allocator`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringappend"></a><a name="append"></a> basic_string:: append

문자열 끝에 문자를 추가합니다.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*ptr*\
추가할 C 문자열입니다.

*문자열*\
문자를 추가하려고 하는 문자열입니다.

*이동*\
추가할 문자를 제공하는 소스 문자열 부분의 인덱스입니다.

*수*\
소스 문자열에서 최대한 추가할 문자의 수입니다.

*char_value*\
추가할 문자 값입니다.

*기본*\
추가될 범위에 있는 첫 번째 요소의 주소를 지정하는 입력 반복기입니다.

*최신*\
추가할 범위에 있는 마지막 요소의 다음 요소 위치를 주소 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

### <a name="return-value"></a>반환 값

멤버 함수에 의해 전달된 문자가 추가되는 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

[연산자 + =](#op_add_eq) 또는 멤버 함수 또는 push_back을 사용 하 여 문자열에 문자를 추가할 수 있습니다 `append` [push_back](#push_back). `operator+=` 는 단일 인수 값을 추가 하는 반면, 다중 인수 `append` 멤버 함수를 사용 하면 문자열의 특정 부분을 추가 하도록 지정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="basic_stringassign"></a><a name="assign"></a> basic_string:: assign

문자열의 내용에 새 문자 값을 할당합니다.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*ptr*\
대상 문자열에 할당할 C 문자열의 문자에 대한 포인터입니다.

*수*\
소스 문자열에서 할당할 문자 수입니다.

*문자열*\
문자를 대상 문자열에 할당할 소스 문자열입니다.

*char_value*\
할당할 문자 값입니다.

*기본*\
대상 범위에 할당할 소스 문자열 범위에서 첫 번째 문자의 주소를 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

*최신*\
대상 범위에 할당할 소스 문자열 범위에서 마지막 문자 다음 문자의 주소를 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

*해제*\
새 문자의 할당을 시작할 위치입니다.

### <a name="return-value"></a>반환 값

멤버 함수에 의해 새 문자가 할당되는 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

문자열에 새 문자 값을 할당할 수 있습니다. 새 값은 문자열과 C 문자열 또는 단일 문자일 수 있습니다. 새 값을 단일 매개 변수로 설명할 수 있는 경우 [operator =](#op_eq) 를 사용할 수 있습니다. 그렇지 않으면 여러 매개 변수가 있는 멤버 함수를 사용 하 여 `assign` 대상 문자열에 할당할 문자열 부분을 지정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="basic_stringat"></a><a name="at"></a> basic_string:: at

문자열에서 지정된 인덱스에 있는 문자에 대한 참조를 제공합니다.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>매개 변수

*이동*\
참조할 요소 위치의 인덱스입니다.

### <a name="return-value"></a>반환 값

매개 변수 인덱스로 지정된 위치에 있는 문자열의 문자에 대한 참조입니다.

### <a name="remarks"></a>설명

문자열의 첫 번째 요소는 인덱스가 0이 고 다음 요소는 양의 정수로 연속적으로 인덱싱됩니다. 따라서 길이가 *n* 인 문자열에는 *n 번째 요소가 n* *-* 1로 인덱싱되는 요소가 있습니다.

멤버 [연산자&#91;&#93;](#op_at) 는 `at` 문자열의 요소에 대 한 읽기 및 쓰기 권한을 제공 하기 위해 멤버 함수 보다 빠릅니다.

멤버는 `operator[]` 매개 변수로 전달 된 인덱스가 유효한 지 여부를 확인 하지 않지만 멤버 함수는 유효 하지 않은 경우이를 `at` 사용 해야 합니다. 0 보다 작거나 문자열의 크기 보다 크거나 같은 인덱스에 해당 하는 잘못 된 인덱스는 `at` [out_of_range 클래스](../standard-library/out-of-range-class.md) 예외를 throw 합니다. `operator[]`에 잘못된 인덱스가 전달되면 정의되지 않은 동작이 발생하지만, 문자열의 길이와 같은 인덱스는 const 문자열에 대해 유효한 인덱스이며 이 인덱스가 전달되면 연산자는 null 문자를 반환합니다.

반환 된 참조는 문자열 재할당 또는 문자열이 아닌에 대 한 수정으로 인해 무효화 될 수 있습니다 **`const`** .

### <a name="example"></a>예제

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringback"></a><a name="back"></a> basic_string:: back

문자열의 마지막 요소에 대한 참조를 반환합니다.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>반환 값

비어 있지 않아야 하는 문자열의 마지막 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

## <a name="basic_stringbasic_string"></a><a name="basic_string"></a> basic_string:: basic_string

비어 있거나 특정 문자로 초기화된 문자열 또는 다른 문자열 개체나 C 스타일(null 종료) 문자열 일부 또는 전체의 복사본인 문자열을 생성합니다.

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*ptr*\
해당 문자가 생성되는 `string`을 초기화하는 데 사용되는 C 문자열입니다. 이 값은 null 포인터일 수 없습니다.

*alloc_type*\
생성되는 문자열 개체에 대한 스토리지 할당자 클래스입니다.

*수*\
초기화할 문자 수입니다.

*오른쪽*\
생성되는 문자열을 초기화할 문자열입니다.

*right_offset*\
생성되는 문자열에 대한 문자 값을 초기화하는 데 첫 번째로 사용할 문자열의 문자 인덱스입니다.

*char_value*\
생성되는 문자열에 복사할 문자 값입니다.

*기본*\
삽입할 소스 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

*최신*\
삽입할 소스 범위에 있는 마지막 요소의 다음 요소 위치를 주소 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

### <a name="return-value"></a>반환 값

생성자에 의해 생성되는 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

모든 생성자는 [basic_string::allocator_type](#allocator_type)을 저장하고 제어되는 시퀀스를 초기화합니다. 할당자 개체는 `al` 인수입니다(있는 경우). 복사 생성자의 경우 `right.` [basic_string:: get_allocator](#get_allocator) `()` 입니다. 그렇지 않으면 할당자는 `Alloc()` 입니다.

제어되는 시퀀스는 나머지 피연산자에서 지정된 피연산자 시퀀스의 복사본으로 초기화됩니다. 피연산자 시퀀스가 없는 생성자는 제어되는 빈 초기 시퀀스를 지정합니다. `InputIterator`가 템플릿 생성자의 정수 형식이 면 피연산자 시퀀스는 `first,  last` 와 동일 하 게 동작 합니다 `(size_type) first, (value_type) last` .

### <a name="example"></a>예제

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="basic_stringbegin"></a><a name="begin"></a> basic_string:: begin

문자열의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 임의 액세스 반복기입니다.

### <a name="example"></a>예제

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="basic_stringc_str"></a><a name="c_str"></a> basic_string:: c_str

문자열의 내용을 C 스타일의 null로 종료되는 문자열로 변환합니다.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>반환 값

호출하는 문자열의 C 스타일의 버전에 대한 포인터입니다.  소멸자를 포함 하 여 개체의 basic_string 클래스에서 비 const 함수를 호출한 후에는 포인터 값이 유효 하지 않습니다.

### <a name="remarks"></a>설명

Basic_string 클래스 템플릿에 속하는 문자열 형식의 개체가 \<char> null로 종료 될 필요는 없습니다. Null 문자 ' \0 '은 C 문자열에서 특수 문자로 사용되어 문자열의 끝을 표시하지만, 문자열 형식의 개체에서는 특별한 의미가 없으며 다른 문자와 마찬가지로 문자열의 일부가 될 수 있습니다. **Const char** 에서 문자열로 자동 변환 <strong>\*</strong> 되지만, 문자열 클래스는 C 스타일 문자열에서 **basic_string \<char> **형식의 개체로의 자동 변환을 제공 하지 않습니다.

반환 된 C 스타일 문자열은 수정 하지 않아야 합니다 .이 경우 문자열에 대 한 포인터가 무효화 되거나 삭제 될 수 있습니다. 문자열은 수명이 제한 되어 있고 클래스 문자열은이를 소유 하기 때문입니다.

### <a name="example"></a>예제

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringcapacity"></a><a name="capacity"></a> basic_string:: 용량

문자열의 메모리 할당을 늘리지 않고도 문자열에 저장할 수 있는 요소의 최대 수를 반환합니다.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>반환 값

문자열을 보관하기 위해 현재 메모리에 할당된 스토리지의 크기입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어된 시퀀스를 유지하기 위해 현재 할당된 스토리지를 반환하며, 최소 [크기](#size)의 값을 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringcbegin"></a><a name="cbegin"></a> basic_string:: cbegin

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

## <a name="basic_stringcend"></a><a name="cend"></a> basic_string:: cend

**`const`** 범위에서 마지막 요소 바로 다음 위치의 주소를 가리키는 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위 끝의 바로 다음을 가리키는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `end()` `cend()` 합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

에서 반환 된 값은 `cend` 역참조 되지 않아야 합니다.

## <a name="basic_stringclear"></a><a name="clear"></a> basic_string:: clear

문자열의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

멤버 함수가 호출된 문자열은 비어 있게 됩니다.

### <a name="example"></a>예제

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="basic_stringcompare"></a><a name="compare"></a> basic_string:: compare

지정된 문자열과 대/소문자를 구분한 비교를 수행하여 두 문자열이 같은지 아니면 한 문자열이 다른 문자열보다 사전순으로 더 작은지를 확인합니다.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>매개 변수

*문자열*\
피연산자 문자열과 비교할 문자열입니다.

*position_1*\
비교가 시작될 피연산자 문자열의 인덱스입니다.

*number_1*\
비교할 피연산자 문자열의 최대 문자 수입니다.

*number_2*\
비교할 매개 변수 문자열의 최대 문자 수입니다.

*이동*\
비교가 시작될 매개 변수 문자열의 인덱스입니다.

*수*\
비교할 매개 변수 문자열의 최대 문자 수입니다.

*ptr*\
피연산자 문자열과 비교할 C 문자열입니다.

### <a name="return-value"></a>반환 값

피연산자 문자열이 매개 변수 문자열보다 작은 경우 음수 값, 두 문자열이 같은 경우 0, 피연산자 문자열이 매개 변수 문자열보다 큰 경우 양수 값입니다.

### <a name="remarks"></a>설명

`compare`멤버 함수는 사용 되는에 따라 매개 변수 및 피연산자 문자열의 전체 또는 일부를 비교 합니다.

비교는 대/소문자를 구분하여 수행됩니다.

### <a name="example"></a>예제

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="basic_stringconst_iterator"></a><a name="const_iterator"></a> basic_string:: const_iterator

문자열의 요소를 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식은 문자의 값을 수정하는 데 사용할 수 없으며, 문자열을 정방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`const_iterator`를 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="basic_stringconst_pointer"></a><a name="const_pointer"></a> basic_string:: const_pointer

문자열의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

이 형식은 `allocator_type::const_pointer`의 동의어입니다.

형식의 경우 `string` 와 동일 **`char*`** 합니다.

const로 선언된 포인터는 선언할 때 초기화해야 합니다. Const 포인터는 항상 동일한 메모리 위치를 가리키며 상수 또는 비상수 데이터를 가리킬 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="basic_stringconst_reference"></a><a name="const_reference"></a> basic_string:: const_reference

**`const`** 작업을 읽고 수행 하기 위해 문자열에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>설명

`const_reference` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

이 형식은 `allocator_type::const_reference`의 동의어입니다. 문자열의 경우 `type` const와 동일 `char&` 합니다.

### <a name="example"></a>예제

`const_reference`를 선언하고 사용하는 방법에 대한 예제는 [at](#at)의 예제를 참조하세요.

## <a name="basic_stringconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> basic_string:: const_reverse_iterator

문자열의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 문자열 값을 수정할 수 없으며 문자열을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="basic_stringcopy"></a><a name="copy"></a> basic_string:: copy

소스 문자열의 인덱싱된 위치에서 지정한 수까지의 문자를 대상 문자 배열에 복사합니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다. 대신 [basic_string::_Copy_s](#copy_s)의 사용을 고려해보세요.

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*ptr*\
요소를 복사할 대상 문자 배열입니다.

*개수* 원본 문자열에서 복사할 문자 수입니다.

*이동*\
복사본을 만들 원본 문자열의 시작 위치입니다.

### <a name="return-value"></a>반환 값

실제로 복사된 문자 수입니다.

### <a name="remarks"></a>설명

Null 문자는 복사본의 끝에 추가 되지 않습니다.

### <a name="example"></a>예제

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringcrbegin"></a><a name="crbegin"></a> basic_string:: crbegin

역방향 문자열에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

문자열 끝의 바로 다음을 가리키는 임의 역방향 반복기입니다. 이 위치는 역방향 문자열의 시작을 지정합니다.

## <a name="basic_stringcrend"></a><a name="crend"></a> basic_string:: crend

역방향 문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 문자열에서 마지막 요소 다음의 위치(역방향이 해제된 문자열의 첫 번째 요소 앞의 위치) 주소를 지정하는 const 역방향 반복기입니다.

### <a name="remarks"></a>설명

## <a name="basic_string_copy_s"></a><a name="copy_s"></a> basic_string:: _Copy_s

소스 문자열의 인덱싱된 위치에서 지정한 수까지의 문자를 대상 문자 배열에 복사합니다.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*dest*\
요소를 복사할 대상 문자 배열입니다.

*dest_size*\
*대상*의 크기입니다.

*개수* 원본 문자열에서 복사할 문자 수입니다.

*이동*\
복사본을 만들 원본 문자열의 시작 위치입니다.

### <a name="return-value"></a>반환 값

실제로 복사된 문자 수입니다.

### <a name="remarks"></a>설명

Null 문자는 복사본의 끝에 추가 되지 않습니다.

### <a name="example"></a>예제

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringdata"></a><a name="data"></a> basic_string: ata:d

문자열의 내용을 null로 끝나는 문자 배열로 변환 합니다.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>반환 값

문자열의 내용을 포함 하는 null로 끝나는 배열의 첫 번째 요소에 대 한 포인터입니다. 빈 문자열의 경우 포인터는와 같은 단일 null 문자를 가리킵니다 `value_type()` .

### <a name="remarks"></a>설명

`data`요소가 올바른 범위에서 반환 하는 포인터 `[data(), data() + size()]` 입니다. 범위의 각 요소는 문자열의 현재 데이터에 해당 합니다. 즉, 범위의 모든 유효한 오프셋 *n* 에 대해,입니다 `data() + n == addressof(operator[](n))` .

의 오버 로드에서 반환 되는 문자열의 내용을 수정 하는 경우 **`const`** `data` 동작이 정의 되지 않습니다. 또한 터미널 null 문자를 다른 값으로 변경 하면 정의 되지 않은 동작이 발생 합니다. 문자열에 대 한 비 const 참조가 표준 라이브러리 함수로 전달 되는 경우 반환 된 포인터가 무효화 될 수 있습니다. Const가 아닌 멤버 함수를 호출 하 여 무효화 될 수도 있습니다. 멤버 `at` , `back` ,,, `begin` , `end` , 및에 대 `front` `rbegin` `rend` 한 호출은 `operator[]` 포인터를 무효화 하지 않습니다.

C + + 11 이전에는 `data` 반환 된 문자열이 null로 종료 되는 것을 보장 하지 않았습니다. C + + 11부터 `data` 및 `c_str` 는 모두 null로 끝나는 문자열을 반환 하 고는 사실상 동일 합니다.

비 const 오버 로드는 c + + 17의 새로운 기능입니다. 이를 사용 하려면 **/sd: c + + 17** 또는 **/std: c + + 최신** 컴파일러 옵션을 지정 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringdifference_type"></a><a name="difference_type"></a> basic_string::d ifference_type

동일한 문자열 내의 요소를 참조하는 두 반복기 사이의 차이를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>설명

부호 있는 정수 형식은 제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다.

형식의 경우 `string` 와 동일 `ptrdiff_t` 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="basic_stringempty"></a><a name="empty"></a> basic_string:: empty

문자열에 문자가 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 문자열 개체에 문자가 포함 되어 있지 않으면이 고, 그렇지 않으면입니다. **`false`** 하나 이상의 문자가 있는 경우입니다.

### <a name="remarks"></a>설명

멤버 함수는 [size](#size) == 0과 등가입니다.

### <a name="example"></a>예제

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="basic_stringend"></a><a name="end"></a> basic_string:: end

문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 임의 액세스 반복기를 반환합니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 문자열의 끝에 도달 했는지 여부를 테스트 하는 데 주로 사용 됩니다. 에서 반환 된 값은 `end` 역참조 되지 않아야 합니다.

`end`의 반환 값이 `const_iterator`에 할당된 경우 문자열 개체를 수정할 수 없습니다. 의 반환 값 `end` 이에 할당 된 경우 `iterator` 문자열 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="basic_stringends_with"></a><a name="ends_with"></a> basic_string:: ends_with

문자열이 지정 된 접미사로 끝나는지 여부를 확인 합니다.

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

`true` 문자열이 지정 된 접미사로 끝나는 경우 `false` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

`ends_with()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

문자열이 지정 된 접두사로 시작 하는지 확인 하려면 [starts_with](#starts_with) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.ends_with('g') << '\n';
    std::cout << str.ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << str.ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_stringerase"></a><a name="erase"></a> basic_string:: erase

문자열에서 지정된 위치의 요소 또는 요소 범위를 제거합니다.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>매개 변수

*기본*\
지울 범위에서 첫 번째 요소 위치의 주소를 지정하는 반복기입니다.

*최신*\
지울 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 반복기입니다.

*iter*\
지울 문자열에서 요소 위치의 주소를 지정하는 반복기입니다.

*이동*\
제거할 문자열에서 첫 번째 문자의 인덱스입니다.

*수*\
*오프셋*으로 시작 하는 문자열의 범위가 많은 경우 제거 되는 요소 수입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우, 멤버 함수에 의해 제거된 마지막 문자 이후 첫 번째 문자의 주소를 지정하는 반복기입니다. 세 번째 멤버 함수의 경우, 요소가 지워진 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

세 번째 멤버 함수는 ** \* this**를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="basic_stringfind"></a><a name="find"></a> basic_string:: find

문자열에서 지정된 문자 시퀀스와 일치하는 첫 번째 하위 문자열을 정방향으로 검색합니다.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'perfect' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="basic_stringfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string:: find_first_not_of

문자열에서 지정 된 문자열의 요소가 아닌 첫 번째 문자를 검색 합니다.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="basic_stringfind_first_of"></a><a name="find_first_of"></a> basic_string:: find_first_of

문자열에서 지정된 문자열의 요소와 일치하는 첫 번째 문자를 검색합니다.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="basic_stringfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string:: find_last_not_of

문자열에서 지정 된 문자열의 요소가 아닌 마지막 문자를 검색 합니다.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 마칠 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공하면 검색되는 부분 문자열의 첫 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="basic_stringfind_last_of"></a><a name="find_last_of"></a> basic_string:: find_last_of

문자열에서 지정된 문자열의 요소와 일치하는 마지막 문자를 검색합니다.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 마칠 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공 시 검색되는 부분 문자열의 마지막 문자 인덱스이고, 그렇지 않으면 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="basic_stringfront"></a><a name="front"></a> basic_string:: front

문자열의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>반환 값

비어 있지 않아야 하는 문자열의 첫 번째 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

## <a name="basic_stringget_allocator"></a><a name="get_allocator"></a> basic_string:: get_allocator

문자열을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

문자열에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

멤버 함수는 저장된 할당자 개체를 반환합니다.

문자열 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringinsert"></a><a name="insert"></a> basic_string:: insert

요소 하나 또는 여러 개나 요소의 범위를 문자열의 지정된 위치에 삽입합니다.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*놓을*\
새 문자 삽입 지점 뒤 위치의 인덱스입니다.

*ptr*\
문자열에 전체 또는 부분적으로 삽입할 C 문자열입니다.

*수*\
삽입할 문자 수입니다.

*문자열*\
대상 문자열에 전체 또는 부분적으로 삽입할 문자열입니다.

*이동*\
추가할 문자를 제공하는 소스 문자열 부분의 인덱스입니다.

*char_value*\
삽입할 요소의 문자 값입니다.

*iter*\
뒤에 문자를 삽입할 위치를 주소 지정하는 반복기입니다.

*기본*\
삽입할 소스 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

*최신*\
삽입할 소스 범위에 있는 마지막 요소의 다음 요소 위치를 주소 지정하는 입력 반복기, const_pointer 또는 const_iterator입니다.

### <a name="return-value"></a>반환 값

멤버 함수에 의해 새 문자가 할당되는 문자열 개체에 대한 참조 또는 개별 문자 삽입의 경우 특정 멤버 함수에 따라 삽입된 문자의 위치를 주소 지정하는 반복기나 없음입니다.

### <a name="example"></a>예제

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="basic_stringiterator"></a><a name="iterator"></a> basic_string:: iterator

문자열의 요소를 액세스 하 고 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

형식은 `iterator` 문자 값을 수정 하는 데 사용할 수 있으며 정방향 방향으로 문자열을 반복 하는 데 사용 됩니다.

### <a name="example"></a>예제

`iterator`를 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="basic_stringlength"></a><a name="length"></a> basic_string:: length

문자열의 현재 요소 수를 반환합니다.

```cpp
size_type length() const;
```

### <a name="remarks"></a>설명

멤버 함수는 [size](#size)와 동일합니다.

### <a name="example"></a>예제

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringmax_size"></a><a name="max_size"></a> basic_string:: max_size

문자열이 포함할 수 있는 최대 문자 수를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

문자열이 포함할 수 있는 최대 문자 수입니다.

### <a name="remarks"></a>설명

연산의 결과 최대 크기보다 긴 길이의 문자열이 생성되면 [length_error 클래스](../standard-library/length-error-class.md) 형식의 예외가 throw됩니다.

### <a name="example"></a>예제

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringnpos"></a><a name="npos"></a> basic_string:: npos

검색 함수가 실패할 때 "찾을 수 없음" 또는 "모든 나머지 문자"를 나타내는-1로 초기화 된 부호 없는 정수 값입니다.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>설명

값에 대해 반환 값을 확인 해야 하는 경우 `npos` 반환 값이 또는가 아닌 [size_type](#size_type) 형식이 아닌 경우에는 작동 하지 않을 수 **`int`** 있습니다 **`unsigned`** .

### <a name="example"></a>예제

`npos`를 선언하고 사용하는 방법에 대한 예제는 [find](#find)의 예제를 참조하세요.

## <a name="basic_stringoperator"></a><a name="op_add_eq"></a> basic_string:: operator + =

문자열에 문자를 추가합니다.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*char_value*\
추가할 문자입니다.

*ptr*\
추가할 C 문자열의 문자입니다.

*오른쪽*\
추가할 문자열의 문자입니다.

### <a name="return-value"></a>반환 값

멤버 함수에 의해 전달된 문자가 추가되는 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`operator+=` 또는 멤버 함수 [append](#append)나 [push_back](#push_back)을 사용하여 문자열에 문자를 추가할 수 있습니다. `operator+=`을 사용하면 단일 인수 값을 추가할 수 있는 반면 다중 인수 append 멤버 함수를 사용하면 문자열의 특정 부분을 추가하도록 지정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="basic_stringoperator"></a><a name="op_eq"></a> basic_string:: operator =

문자열의 내용에 새 문자 값을 할당합니다.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>매개 변수

*char_value*\
할당할 문자 값입니다.

*ptr*\
대상 문자열에 할당할 C 문자열의 문자에 대한 포인터입니다.

*오른쪽*\
문자를 대상 문자열에 할당할 소스 문자열입니다.

### <a name="return-value"></a>반환 값

멤버 함수에 의해 새 문자가 할당되는 문자열 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

문자열에 새 문자 값을 할당할 수 있습니다. 새 값은 문자열과 C 문자열 또는 단일 문자일 수 있습니다. 새 값을 단일 매개 변수로 설명할 수 있는 경우 `operator=`을 사용할 수 있습니다. 아닌 경우 여러 매개 변수가 있는 멤버 함수 [assign](#assign)을 사용하여 문자열의 어느 부분을 대상 문자열에 할당할지를 지정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="basic_stringoperator"></a><a name="op_at"></a> basic_string:: operator []

문자열에서 지정된 인덱스에 있는 문자에 대한 참조를 제공합니다.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>매개 변수

*이동*\
참조할 요소 위치의 인덱스입니다.

### <a name="return-value"></a>반환 값

매개 변수 인덱스로 지정된 위치에 있는 문자열의 문자에 대한 참조입니다.

### <a name="remarks"></a>설명

문자열의 첫 번째 요소는 인덱스가 0이고 다음 요소부터 연속적으로 양의 정수로 인덱스가 지정되므로 길이가 *n*인 문자열에서 *n*번째 요소의 인덱스 번호는 *n* - 1입니다.

`operator[]`는 문자열의 요소에 대해 읽기 및 쓰기 권한을 제공하므로 [at](#at) 멤버 함수보다 빠릅니다.

`operator[]` 는 매개 변수로 전달 된 인덱스가 유효한 지 여부를 확인 하지 않지만 멤버 함수는 `at` 유효성 검사에 사용 되어야 합니다. 멤버 함수로 전달 된 잘못 된 인덱스 (0 보다 작거나 문자열의 크기 보다 크거나 같은 인덱스)는 `at` [out_of_range 클래스](../standard-library/out-of-range-class.md) 예외를 throw 합니다. `operator[]`에 잘못된 인덱스가 전달되면 정의되지 않은 동작이 발생하지만, 문자열의 길이와 같은 인덱스는 const 문자열에 대해 유효한 인덱스이며 이 인덱스가 전달되면 연산자는 null 문자를 반환합니다.

반환 된 참조는 문자열 재할당 또는 문자열이 아닌에 대 한 수정으로 인해 무효화 될 수 있습니다 **`const`** .

[ \_ 반복기 \_ 디버그 \_ 수준](../standard-library/iterator-debug-level.md) 을 1 또는 2로 설정 하 여 컴파일할 때 문자열 범위 밖의 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다. 자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringpointer"></a><a name="pointer"></a> basic_string::p ointer

문자열 또는 문자 배열의 문자 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>설명

이 형식은 `allocator_type::pointer`의 동의어입니다.

형식의 경우 `string` 와 동일 **`char`** <strong>\*</strong> 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="basic_stringpop_back"></a><a name="pop_back"></a> basic_string::p op_back

문자열의 마지막 요소를 지웁니다.

```cpp
void pop_back();
```

### <a name="remarks"></a>설명

이 멤버 함수는 실제로 `erase(size() - 1)`를 호출하여 비어 있지 않아야 하는 시퀀스의 마지막 요소를 지웁니다.

## <a name="basic_stringpush_back"></a><a name="push_back"></a> basic_string::p ush_back

문자열 끝에 요소를 추가합니다.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>매개 변수

*char_value*\
문자열의 끝에 추가할 문자입니다.

### <a name="remarks"></a>설명

멤버 함수는 실제로 [insert](#insert)( [end](#end), *char_value* )를 호출 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="basic_stringrbegin"></a><a name="rbegin"></a> basic_string:: rbegin

역방향 문자열에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향이 해제된 해당 문자열에서 무엇이 마지막 요소가 될지를 확인하면서, 임의 액세스 반복기를 역순 문자열의 첫 번째 요소로 반환합니다.

### <a name="remarks"></a>설명

[begin](#begin)이 문자열과 사용되는 것처럼 `rbegin`은 역방향 문자열과 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당된 경우 문자열 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당된 경우 문자열 개체를 수정할 수 있습니다.

`rbegin`은 문자열에서 역순으로 수행되는 반복을 초기화하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="basic_stringreference"></a><a name="reference"></a> basic_string:: reference

문자열에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>설명

형식을 `reference` 사용 하 여 요소의 값을 수정할 수 있습니다.

이 형식은 `allocator_type::reference`의 동의어입니다.

형식의 경우 `string` 와 동일 `chr&` 합니다.

### <a name="example"></a>예제

`reference`를 선언하고 사용하는 방법에 대한 예제는 [at](#at)의 예제를 참조하세요.

## <a name="basic_stringrend"></a><a name="rend"></a> basic_string:: rend

역순 문자열에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 문자열에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

[end](#end)가 문자열과 사용되는 것처럼 `rend`은 역방향 문자열과 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당된 경우 문자열 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당된 경우 문자열 개체를 수정할 수 있습니다.

역방향 반복기가 문자열 끝에 도달했는지 여부를 테스트하려면 `rend`를 사용할 수 있습니다.

에서 반환 된 값은 `rend` 역참조 되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="basic_stringreplace"></a><a name="replace"></a> basic_string:: replace

문자열에서 지정된 위치의 요소를 다른 범위 또는 문자열이나 C 문자열에서 복사한 문자 또는 지정된 문자로 바꿉니다.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*문자열*\
피연산자 문자열의 문자 소스가 될 문자열입니다.

*position_1*\
교체가 시작될 피연산자 문자열의 인덱스입니다.

*number_1*\
피연산자 문자열에서 교체할 최대 문자 수입니다.

*position_2*\
복사가 시작될 매개 변수 문자열의 인덱스입니다.

*number_2*\
매개 변수 C 문자열에서 사용될 최대 문자 수입니다.

*ptr*\
피연산자 문자열의 문자 소스가 될 C 문자열입니다.

*char_value*\
피연산자 문자열에 복사될 문자입니다.

*first0*\
피연산자 문자열에서 제거될 첫 번째 문자의 주소를 지정하는 반복기입니다.

*last0*\
피연산자 문자열에서 제거될 마지막 문자의 주소를 지정하는 반복기입니다.

*기본*\
매개 변수 문자열에서 복사될 첫 번째 문자의 주소를 지정하는 반복기, const_pointer 또는 const_iterator입니다.

*최신*\
매개 변수 문자열에서 복사될 마지막 문자의 주소를 지정하는 반복기, const_pointer 또는 const_iterator입니다.

*수*\
*Char_value* 피연산자 문자열로 복사 되는 횟수입니다.

### <a name="return-value"></a>반환 값

대체된 피연산자 문자열입니다.

### <a name="example"></a>예제

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="basic_stringreserve"></a><a name="reserve"></a> basic_string:: reserve

문자열의 용량을 최소한 지정된 숫자보다 크게 설정합니다.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>매개 변수

*수*\
메모리가 예약되는 문자 수입니다.

### <a name="remarks"></a>설명

다시 할당은 시간이 오래 걸리는 프로세스이고 문자열의 문자를 참조하는 모든 참조, 포인터 및 반복기를 무효화하기 때문에 용량을 충분히 확보하는 것이 중요합니다.

문자열 형식의 개체에 대한 용량의 개념은 벡터 형식의 개체에 대한 개념과 같습니다. Vector와 달리 멤버 함수를 `reserve` 호출 하 여 개체의 용량을 축소할 수 있습니다. 요청은 강제성이 없으며, 발생할 수도 발생하지 않을 수도 있습니다. 매개 변수의 기본값이 0 이므로의 호출은 `reserve` 현재 문자열에 있는 문자 수에 맞게 문자열의 용량을 줄이기 위한 비 바인딩 요청입니다. 용량은 절대 현재 문자 수 아래로 줄지 않습니다.

`reserve`를 호출하는 것이 문자열의 용량을 줄이기 위한 유일한 방법입니다. 그러나 위에서 언급한 대로 이 요청은 강제성이 없으며, 발생할 수도 발생하지 않을 수도 있습니다.

### <a name="example"></a>예제

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="basic_stringresize"></a><a name="resize"></a> basic_string:: 크기 조정

문자열의 새 크기를 지정하고 필요에 따라 요소를 추가하거나 지웁니다.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>매개 변수

*수*\
문자열의 새 크기입니다.

*char_value*\
추가 요소가 필요한 경우 추가된 문자를 초기화할 값입니다.

### <a name="remarks"></a>설명

결과 크기가 최대 문자 수를 초과하면 양식에서 `length_error`를 throw합니다.

### <a name="example"></a>예제

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="basic_stringreverse_iterator"></a><a name="reverse_iterator"></a> basic_string:: reverse_iterator

문자열에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 문자열 값을 수정하는 데 사용할 수 있으며 문자열을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="basic_stringrfind"></a><a name="rfind"></a> basic_string:: rfind

문자열에서 지정된 문자 시퀀스와 일치하는 첫 번째 하위 문자열을 역방향으로 검색합니다.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>매개 변수

*char_value*\
멤버 함수가 검색할 문자 값입니다.

*이동*\
검색을 시작할 위치의 인덱스입니다.

*ptr*\
멤버 함수가 검색할 C 문자열입니다.

*수*\
멤버 함수가 검색할 C 문자열의 첫 문자부터 계산된 문자 수입니다.

*문자열*\
멤버 함수가 검색할 문자열입니다.

### <a name="return-value"></a>반환 값

성공할 경우 부분 문자열에서 첫 번째 문자의 마지막 발생(역방향으로 검색 시)의 인덱스입니다. 실패할 경우 `npos`입니다.

### <a name="example"></a>예제

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="basic_stringshrink_to_fit"></a><a name="shrink_to_fit"></a> basic_string:: shrink_to_fit

문자열의 초과 용량을 삭제합니다.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>설명

이 멤버 함수는 컨테이너에서 불필요한 스토리지를 모두 제거합니다.

## <a name="basic_stringsize"></a><a name="size"></a> basic_string:: size

문자열의 현재 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

문자열의 길이입니다.

### <a name="example"></a>예제

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringsize_type"></a><a name="size_type"></a> basic_string:: size_type

문자열에서 요소 수와 인덱스를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>설명

와 동일 `allocator_type::size_type` 합니다.

형식의 경우 `string` 와 동일 `size_t` 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="basic_stringstarts_with"></a><a name="starts_with"></a> basic_string:: starts_with

문자열이 지정 된 접두사로 시작 하는지 여부를 확인 합니다.

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

문자열이 지정 된 접미사로 끝나는지 여부를 확인 하려면 [ends_with](#ends_with) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'     
    std::cout << str.starts_with('b') << '\n';
    std::cout << str.starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << str.starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_stringsubstr"></a><a name="substr"></a> basic_string:: substr

지정된 위치부터 시작하여 문자열의 하위 문자열을 최대 특정 문자 수만큼 복사합니다.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>매개 변수

*이동*\
문자열의 복사본이 만들어지는 위치에 요소를 배치하는 인덱스이며 기본값은 0입니다.

*수*\
문자가 있는 경우 복사될 문자의 수입니다.

### <a name="return-value"></a>반환 값

첫 번째 인수에 의해 지정된 위치에서 시작하는 문자열 피연산자 요소의 복사본인 부분 문자열 개체입니다.

### <a name="example"></a>예제

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="basic_stringswap"></a><a name="swap"></a> basic_string:: swap

두 문자열의 내용을 교환합니다.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>매개 변수

*문자열*\
대상 문자열의 요소와 교환할 요소가 있는 소스 문자열입니다.

### <a name="remarks"></a>설명

교환되는 문자열에 동일한 할당자 개체가 있으면 `swap` 멤버 함수는:

- 일정한 시간에 발생합니다.

- 예외를 throw하지 않습니다.

- 두 개 문자열에서 요소를 지정하는 어떤 참조, 포인터 또는 반복기도 무효화하지 않습니다.

그렇지 않으면 두 개의 제어되는 시퀀스에 있는 요소 수에 비례하여 많은 요소 할당 및 생성자 호출을 수행합니다.

### <a name="example"></a>예제

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="basic_stringtraits_type"></a><a name="traits_type"></a> basic_string:: traits_type

문자열에 저장된 요소의 문자 특성 형식입니다.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>설명

Type은 두 번째 템플릿 매개 변수의 동의어입니다 `Traits` .

형식의 경우 `string` **char_traits \<char> **와 동일 합니다.

### <a name="example"></a>예제

`traits_type`을 선언하고 사용하는 방법에 대한 예제는 [copy](../standard-library/char-traits-struct.md#copy)의 예제를 참조하세요.

## <a name="basic_stringvalue_type"></a><a name="value_type"></a> basic_string:: value_type

문자열에 저장된 문자의 형식을 나타내는 형식입니다.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>설명

`traits_type::char_type`와 동일 하며 **`char`** 형식의 개체에 대해와 동일 `string` 합니다.

### <a name="example"></a>예제

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>참고 항목

[\<string>](../standard-library/string.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
