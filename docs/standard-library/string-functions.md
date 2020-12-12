---
description: '자세한 정보: &lt; 문자열 &gt; 함수'
title: '&lt;string&gt; functions'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 859cb6db2e02ad5e915b5d8f3ed31aaf7e443580
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183739"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; functions

[getline](#getline)\
[stod](#stod)\
[stof](#stof)\
[stoi](#stoi)\
[stol](#stol)\
[stold](#stold)\
[stoll](#stoll)\
[stoul](#stoul)\
[stoull](#stoull)\
[스왑을](#swap)\
[to_string](#to_string)\
[to_wstring](#to_wstring)

## <a name="getline"></a><a name="getline"></a> getline

입력 스트림에서 문자열을 한 줄씩 추출합니다.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>매개 변수

*in_stream*\
문자열을 추출할 입력 스트림입니다.

*문자열*\
입력 스트림에서 문자를 읽어들일 문자열입니다.

*문자가*\
줄 구분 기호입니다.

### <a name="return-value"></a>반환 값

입력 스트림 *in_stream* 입니다.

### <a name="remarks"></a>설명

표시 된 함수 시그니처 쌍은 `(1)` *구분 기호가* 발견 될 때까지 *in_stream* 에서 문자를 추출 하 여 *str* 에 저장 합니다.

로 표시 된 함수 시그니처 쌍은 `(2)` 줄 바꿈 문자를 기본 줄 구분 기호로 사용 하 고로 동작 `getline(in_stream, str, in_stream. widen('\n'))` 합니다.

각 쌍의 두 번째 함수는 [value 참조](../cpp/lvalues-and-rvalues-visual-cpp.md)를 지원하기 위한 첫 번째 함수와 유사한 버전입니다.

다음 중 하나가 발생하면 추출이 중지됩니다.

- 파일의 끝에 있습니다 .이 경우 *in_stream* 의 내부 상태 플래그가로 설정 됩니다 `ios_base::eofbit` .

- 함수는 *구분 기호와* 동일한 요소를 추출 합니다. 요소가 다시 배치 되거나 제어 되는 시퀀스에 추가 되지 않습니다.

- 함수는 `str.` [max_size](../standard-library/basic-string-class.md#max_size) 요소를 추출 합니다. *In_stream* 의 내부 상태 플래그는로 설정 됩니다 `ios_base::failbit` .

- 이전에 나열 된 것 이외의 다른 오류 *in_stream* 의 내부 상태 플래그는로 설정 됩니다 `ios_base::badbit` .

내부 상태 플래그에 대한 자세한 내용은 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)를 참조하세요.

함수가 요소를 추출 하지 않으면 *in_stream* 의 내부 상태 플래그가로 설정 됩니다 `ios_base::failbit` . 어떤 경우 든 `getline` *in_stream* 는를 반환 합니다.

예외가 throw 되 면 *in_stream* 및 *str* 는 유효한 상태로 유지 됩니다.

### <a name="example"></a>예제

다음 코드에서는 `getline()`을 두 가지 모드에서 보여 줍니다. 첫 번째 모드에서는 기본 구분 기호(줄 바꿈 문자)를 사용하고 두 번째 모드에서는 공백을 구분 기호로 사용합니다. 파일의 끝 문자(키보드에서 CTRL+Z를 누름)를 사용하여 while 루프 종료를 제어합니다. 이 값은의 내부 상태 플래그를로 설정 합니다 .이 플래그는 `cin` `eofbit` 두 번째 while 루프가 제대로 작동 하기 전에 [basic_ios:: clear ()](../standard-library/basic-ios-class.md#clear) 를 사용 하 여 지워야 합니다.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a> stod

문자 시퀀스를로 변환 **`double`** 합니다.

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

### <a name="return-value"></a>반환 값

**`double`** 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`double`** `strtod( str.c_str(), _Eptr)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stof"></a><a name="stof"></a> stof

문자 시퀀스를 float로 변환합니다.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

### <a name="return-value"></a>반환 값

**`float`** 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`float`** `strtof( str.c_str(), _Eptr)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stoi"></a><a name="stoi"></a> stoi

문자 시퀀스를 정수로 변환합니다.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>반환 값

정수 값입니다.

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

*하단*\
사용할 기수입니다.

### <a name="remarks"></a>설명

함수는 `stoi` *str* 의 문자 시퀀스를 형식의 값으로 변환 하 **`int`** 고 값을 반환 합니다. 예를 들어 문자 시퀀스 "10" 전달 시 `stoi`에서 반환하는 값은 정수 10입니다.

`stoi` 는 `strtol` 방식으로 호출 될 때 단일 바이트 문자에 대 한 함수와 비슷하게 동작 합니다. `strtol( str.c_str(), _Eptr, idx)` 여기서 `_Eptr` 은 함수 내부의 개체 이거나, `wcstol` 와이드 문자의 경우 비슷한 방식으로 호출 되는 경우입니다 `wcstol(Str.c_str(), _Eptr, idx)` . 자세한 내용은 [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)을 참조하세요.

인 `str.c_str() == *_Eptr` 경우 `stoi` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출을 설정 `errno` 하거나 반환 된 값을 형식의 개체로 나타낼 수 없는 경우 **`int`** 형식의 개체를 throw `out_of_range` 합니다. 그렇지 않고, *idx* 가 null 포인터가 아닌 경우 함수는에을 저장 `*_Eptr - str.c_str()` `*idx` 합니다.

## <a name="stol"></a><a name="stol"></a> stol

문자 시퀀스를로 변환 **`long`** 합니다.

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

*하단*\
사용할 기수입니다.

### <a name="return-value"></a>반환 값

long 정수 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`long`** `strtol( str.c_str(), _Eptr, idx)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stold"></a><a name="stold"></a> stold

문자 시퀀스를로 변환 **`long double`** 합니다.

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

### <a name="return-value"></a>반환 값

**`long double`** 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`long double`** `strtold( str.c_str(), _Eptr)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stoll"></a><a name="stoll"></a> stoll

문자 시퀀스를로 변환 **`long long`** 합니다.

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

*하단*\
사용할 기수입니다.

### <a name="return-value"></a>반환 값

**`long long`** 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`long long`** `strtoll( str.c_str(), _Eptr, idx)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stoul"></a><a name="stoul"></a> stoul

문자 시퀀스를 부호 없는 long으로 변환합니다.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

*하단*\
사용할 기수입니다.

### <a name="return-value"></a>반환 값

부호 없는 long 정수 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`unsigned long`** `strtoul( str.c_str(), _Eptr, idx)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="stoull"></a><a name="stoull"></a> stoull

문자 시퀀스를로 변환 **`unsigned long long`** 합니다.

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 문자 시퀀스입니다.

*idx*\
변환되지 않은 첫 번째 문자의 인덱스 값입니다.

*하단*\
사용할 기수입니다.

### <a name="return-value"></a>반환 값

**`unsigned long long`** 값입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 *str* 의 요소 시퀀스를 형식의 값으로 변환 합니다 **`unsigned long long`** `strtoull( str.c_str(), _Eptr, idx)` . 여기서 `_Eptr` 은 함수 내부의 개체입니다. 인 경우 `str.c_str() == *_Eptr` 형식의 개체를 throw `invalid_argument` 합니다. 이러한 호출에서 `errno`를 설정하는 경우에는 `out_of_range` 형식의 개체가 throw됩니다. 그렇지 않고 *idx* 가 null 포인터가 아닌 경우 함수는에을 `*_Eptr -  str.c_str()` 저장 `*idx` 하 고 값을 반환 합니다.

## <a name="swap"></a><a name="swap"></a> 스왑을

두 문자열의 문자 배열을 교환합니다.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
다른 문자열의 요소와 교환할 요소를 포함 하는 하나의 문자열입니다.

*오른쪽*\
요소가 첫 번째 문자열과 교환되는 다른 문자열입니다.

### <a name="remarks"></a>설명

템플릿 함수는 특수 멤버 함수를 *왼쪽* 으로 실행 합니다. 문자열에 대해 [바꾸기](../standard-library/basic-string-class.md#swap)(*오른쪽*)-일관 된 복잡성을 보장 합니다.

### <a name="example"></a>예제

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
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

## <a name="to_string"></a><a name="to_string"></a> to_string

값을 `string`로 변환합니다.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>매개 변수

*기본값*\
변환할 값입니다.

### <a name="return-value"></a>반환 값

값을 나타내는 `string`입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 함수 내부의 배열 개체에 저장 된 요소의 시퀀스로 *값* 을 변환 합니다. `Buf` `sprintf(Buf, Fmt, value)` 여기서 `Fmt` 은입니다.

- `"%d"`*값* 이 형식인 경우 **`int`**

- `"%u"`*값* 이 형식인 경우 **`unsigned int`**

- `"%ld"`*값* 이 형식인 경우 **`long`**

- `"%lu"`*값* 이 형식인 경우 **`unsigned long`**

- `"%lld"`*값* 이 형식인 경우 **`long long`**

- `"%llu"`*값* 이 형식인 경우 **`unsigned long long`**

- `"%f"`*값* 이 또는 형식인 경우 **`float`****`double`**

- `"%Lf"`*값* 이 형식인 경우 **`long double`**

함수에서 `string(Buf)`을 반환합니다.

## <a name="to_wstring"></a><a name="to_wstring"></a> to_wstring

값을 와이드 문자열로 변환합니다.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>매개 변수

*기본값*\
변환할 값입니다.

### <a name="return-value"></a>반환 값

값을 나타내는 와이드 문자열입니다.

### <a name="remarks"></a>설명

함수는를 호출 하는 것 처럼 함수 내부의 배열 개체에 저장 된 요소의 시퀀스로 *값* 을 변환 합니다. `Buf` `swprintf(Buf, Len, Fmt, value)` 여기서 `Fmt` 은입니다.

- `L"%d"`*값* 이 형식인 경우 **`int`**

- `L"%u"`*값* 이 형식인 경우 **`unsigned int`**

- `L"%ld"`*값* 이 형식인 경우 **`long`**

- `L"%lu"`*값* 이 형식인 경우 **`unsigned long`**

- `L"%lld"`*값* 이 형식인 경우 **`long long`**

- `L"%llu"`*값* 이 형식인 경우 **`unsigned long long`**

- `L"%f"`*값* 이 또는 형식인 경우 **`float`****`double`**

- `L"%Lf"`*값* 이 형식인 경우 **`long double`**

함수에서 `wstring(Buf)`을 반환합니다.

## <a name="see-also"></a>참고 항목

[\<string>](../standard-library/string.md)
