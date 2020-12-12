---
description: Basic_istream 클래스에 대해 자세히 알아보세요.
title: basic_istream 클래스
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 103777c5a4a590fbbfac95e690329b621497d087
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325695"
---
# <a name="basic_istream-class"></a>basic_istream 클래스

이 템플릿 클래스는 문자 특성이 *Tr*([traits_type](../standard-library/basic-ios-class.md#traits_type)이라고도 함) 클래스에 의해 결정되는 `Char_T`([char_type](../standard-library/basic-ios-class.md#char_type)이라고도 함) 형식의 요소가 있는 스트림 버퍼에서 요소 및 인코드된 개체의 추출을 제어하는 개체를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>설명

[operator>>](#op_gt_gt)를 오버로드하는 대부분의 멤버 함수는 형식이 지정된 입력 함수입니다. 다음 패턴을 따릅니다.

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

다른 많은 멤버 함수는 형식이 지정되지 않은 입력 함수입니다. 다음 패턴을 따릅니다.

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

두 함수 그룹 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` 은 요소를 추출 하는 동안 파일의 끝이 나올 경우를 호출 합니다.

클래스 저장소의 개체 `basic_istream<Char_T, Tr>` :

- 클래스의 가상 공용 기준 개체 [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` 입니다.

- 서식이 지정 되지 않은 마지막 입력 작업 (이전 코드에서 호출)에 대 한 추출 수 `count` 입니다.

## <a name="example"></a>예제

입력 스트림에 대한 자세한 내용은 [basic_ifstream 클래스](../standard-library/basic-ifstream-class.md)에 대한 예제를 참조하세요.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_istream](#basic_istream)|`basic_istream` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[gcount](#gcount)|서식이 지정되지 않은 마지막 입력 동안 읽은 문자 수를 반환합니다.|
|[get](#get)|입력 스트림에서 하나 이상의 문자를 읽습니다.|
|[getline](#getline)|입력 스트림에서 한 줄을 읽습니다.|
|[무시](#ignore)|현재 읽기 위치에서 많은 요소를 건너뜁니다.|
|[빠르게](#peek)|읽을 다음 문자를 반환합니다.|
|[putback](#putback)|지정된 문자를 스트림에 넣습니다.|
|[읽음](#read)|스트림에서 지정된 개수의 문자를 읽고 배열에 저장합니다.|
|[readsome](#readsome)|버퍼에서 읽기만 합니다.|
|[seekg](#seekg)|스트림에서 읽기 위치를 이동합니다.|
|[감시](#sentry)|중첩된 클래스는 선언에서 형식이 지정된 입력 함수 및 형식이 지정되지 않은 입력 함수를 구성하는 개체를 설명합니다.|
|[스왑을](#swap)|이 `basic_istream` 개체를 제공된 `basic_istream` 개체 매개 변수로 교환합니다.|
|[동기화](#sync)|스트림의 연결 된 입력 장치를 스트림 버퍼와 동기화 합니다.|
|[tellg](#tellg)|스트림에서 현재 읽기 위치를 보고합니다.|
|[unget](#unget)|가장 최근에 읽은 문자를 다시 스트림에 넣습니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자>>](#op_gt_gt)|입력 스트림에 대해 함수를 호출하거나 입력 스트림에서 형식이 지정된 데이터를 읽습니다.|
|[연산자 =](#op_eq)|이 개체에 연산자의 오른쪽에 있는 `basic_istream`을 할당합니다. `rvalue`복사본을 남기지 않는 참조와 관련 된 이동 할당입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<istream>

**네임스페이스:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a> basic_istream:: basic_istream

`basic_istream` 형식의 개체를 생성합니다.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>매개 변수

*strbuf*\
[basic_streambuf](../standard-library/basic-streambuf-class.md) 형식의 개체입니다.

*_Isstd*\
**`true`** 표준 스트림 인 경우 그렇지 않으면 **`false`** 입니다.

*오른쪽*\
복사할 `basic_istream` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는를 호출 하 여 기본 클래스를 초기화 합니다 [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` . 또한 추출 개수에 0을 저장합니다. 이 추출 횟수에 대 한 자세한 내용은 [Basic_istream 클래스](../standard-library/basic-istream-class.md) 개요의 설명 섹션을 참조 하세요.

두 번째 생성자는 `move(right)`를 호출하여 기본 개체를 초기화합니다. 또한 `right.gcount()` 추출 개수에를 저장 하 고 * right * *의 추출 개수에 0을 저장 합니다.

### <a name="example"></a>예제

입력 스트림에 대한 자세한 내용은 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream)에 대한 예제를 참조하세요.

## <a name="basic_istreamgcount"></a><a name="gcount"></a> basic_istream:: gcount

서식이 지정되지 않은 마지막 입력 동안 읽은 문자 수를 반환합니다.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>반환 값

추출 개수입니다.

### <a name="remarks"></a>설명

형식이 지정되지 않은 문자를 읽으려면 [basic_istream::get](#get)을 사용하세요.

### <a name="example"></a>예제

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a> basic_istream:: get

입력 스트림에서 하나 이상의 문자를 읽습니다.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>매개 변수

*수*\
*strbuf* 에서 읽을 문자 수입니다.

*문자가*\
*개수* 이전에 발생 한 경우 읽기를 종료 해야 하는 문자입니다.

*문자열*\
쓸 수 있는 문자열입니다.

*Ch*\
가져올 문자입니다.

*strbuf*\
쓸 수 있는 버퍼입니다.

### <a name="return-value"></a>반환 값

매개 변수 없는 형식의 get은 읽은 요소를 정수로서 또는 파일 끝으로서 반환합니다. 나머지 폼은 스트림 (*)을 반환 합니다 **`this`** .

### <a name="remarks"></a>설명

서식이 지정 되지 않은 첫 번째 입력 함수는를 반환 하는 것 처럼 가능한 경우 요소를 추출 `rdbuf->sbumpc` 합니다. 그렇지 않으면를 반환 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 합니다. 함수가 요소를 추출 하지 않으면를 호출 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 합니다.

두 번째 함수도 같은 방법으로 [int_type](../standard-library/basic-ios-class.md#int_type) 요소 `meta`를 추출합니다. `meta`가와 비교 하면 `traits_type::eof` 함수는를 호출 `setstate(failbit)` 합니다. 그렇지 않으면 `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` *Ch* 에 저장 됩니다. 함수는 __* this__ 를 반환 합니다.

세 번째 함수는를 반환 합니다 `get(str, count, widen('\n'))` .

네 번째 함수는 최대 `count - 1` 개 요소를 추출 하 여 *str* 에서 시작 하는 배열에 저장 합니다. 함수는 항상 추출하여 저장한 요소 뒤에 `char_type`을 저장합니다. 테스트 순서에서 추출은 다음에서 중지됩니다.

- 파일의 끝.

- 함수는 *구분 기호와* 동일한 요소를 추출 합니다. 이 경우 요소는 제어 되는 시퀀스로 다시 배치 됩니다.

- 함수는 요소를 추출 `count - 1` 합니다.

함수가 요소를 추출하지 않는 경우 `setstate(failbit)`. 어떤 경우 든 __* this__ 를 반환 합니다.

다섯째 함수는를 반환 합니다 `get(strbuf, widen('\n'))` .

여섯 번째 함수는 요소를 추출하고 *strbuf* 에 삽입합니다. 추출 하지 않는 *구분 기호* 와 동일 하 게 비교 되는 요소 또는 파일 끝에서 추출이 중지 됩니다. 또한 삽입이 실패하거나 예외를 throw하면(catch했지만 다시 throw되지 않음) 문제의 요소를 추출하지 않고 중단합니다. 함수가 요소를 추출하지 않는 경우 `setstate(failbit)`. 어떤 경우 든 함수는 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a> basic_istream:: getline

입력 스트림에서 한 줄을 가져옵니다.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>매개 변수

*수*\
*strbuf* 에서 읽을 문자 수입니다.

*문자가*\
*개수* 이전에 발생 한 경우 읽기를 종료 해야 하는 문자입니다.

*문자열*\
쓸 수 있는 문자열입니다.

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

이러한 형식이 지정 되지 않은 입력 함수 중 첫 번째는를 반환 합니다 `getline(str, count, widen('\n'))` .

두 번째 함수는 최대 `count - 1` 개 요소를 추출 하 여 *str* 에서 시작 하는 배열에 저장 합니다. 함수는 항상 추출하여 저장한 요소 뒤에 문자열 종결 문자를 저장합니다. 테스트 순서에서 추출은 다음에서 중지됩니다.

- 파일의 끝.

- 함수는 *구분 기호와* 동일한 요소를 추출 합니다. 이 경우 요소는 다시 배치 되지 않으며 제어 되는 시퀀스에 추가 되지 않습니다.

- 함수는 요소를 추출 `count - 1` 합니다.

함수가 요소 또는 요소를 추출 하지 않으면 `count - 1` 를 호출 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 합니다. 어떤 경우 든 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a> basic_istream:: 무시

현재 읽기 위치에서 많은 요소를 건너뜁니다.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>매개 변수

*수*\
현재 읽기 위치에서 건너뛸 요소의 수입니다.

*문자가*\
개수 이전에 발생 한 경우에서를 반환 하 `ignore` 고 *구분 기호* 이후의 모든 요소를 읽을 수 있도록 하는 요소입니다.

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

형식이 지정 되지 않은 입력 함수는 요소 *수를 계산* 하 고 삭제 합니다. 그러나 *count* 가와 같으면 `numeric_limits<int>::max` 임의로 크게 사용 됩니다. 추출은 파일의 끝 이나 `Ch` `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` 구분 기호 (추출 된 *구분 기호* )와 같은 요소에 대 한 초기에 중지 됩니다. 함수는 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a> basic \_ istream:: operator>>

입력 스트림에 대해 함수를 호출하거나 입력 스트림에서 형식이 지정된 데이터를 읽습니다.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>매개 변수

*Pfn*\
함수 포인터입니다.

*strbuf*\
`stream_buf` 형식의 개체입니다.

*짧은*\
스트림에서 읽은 값입니다.

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

\<istream> 헤더도 몇몇 전역 추출 연산자를 정의합니다. 자세한 내용은 [operator>>  ( \<istream> )](../standard-library/istream-operators.md#op_gt_gt)를 참조 하세요.

첫 번째 멤버 함수는 폼의 식이 `istr >> ws` 를 호출 하 [`ws`](../standard-library/istream-functions.md#ws) `(istr)` 고 __* this__ 를 반환 하는지 확인 합니다. 두 번째와 세 번째 함수는와 같은 다른 조작자가 [`hex`](../standard-library/ios-functions.md#hex) 비슷하게 동작 하도록 합니다. 나머지 함수는 형식이 지정 된 입력 함수입니다.

다음 함수는

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

*strbuf* 가 null 포인터가 아닌 경우 요소를 추출 하 고 *strbuf* 에 삽입 합니다. 추출은 파일의 끝에서 중지됩니다. 또한 삽입이 실패하거나 예외를 throw하면(catch했지만 다시 throw되지 않음) 문제의 요소를 추출하지 않고 중단합니다. 함수가 요소를 추출 하지 않으면를 호출 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 합니다. 어떤 경우 든 함수는 __* this__ 를 반환 합니다.

다음 함수는

```cpp
basic_istream& operator>>(bool& val);
```

을 호출 하 여 필드를 추출 하 고 부울 값으로 변환 [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)` 합니다. 여기서 `InIt` 는로 정의 됩니다 [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` . 함수는 __* this__ 를 반환 합니다.

각 함수는 다음과 같습니다.

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

필드를 추출 하 고를 호출 하 여 숫자 값으로 변환 `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` 합니다. 여기서 `InIt` 는로 정의 되 `istreambuf_iterator<Char_T, Tr>` 고 *val* 은 필요에 따라, 또는 형식입니다 **`long`** **`unsigned long`** **`void`** <strong>\*</strong> .

변환 된 값을 *val* 형식으로 표현할 수 없는 경우 함수는를 호출 합니다 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . 어떤 경우 든 함수는 __* this__ 를 반환 합니다.

각 함수는 다음과 같습니다.

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

필드를 추출 하 고를 호출 하 여 숫자 값으로 변환 `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` 합니다. 여기서 `InIt` 는로 정의 되 `istreambuf_iterator<Char_T, Tr>` 고 *val* 은 형식 또는 필요에 따라를 정의 **`double`** **`long double`** 합니다.

변환 된 값을 *val* 형식으로 표현할 수 없는 경우 함수는를 호출 합니다 `setstate(failbit)` . 어떤 경우 든 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a> basic_istream:: operator =

이 개체에 연산자의 오른쪽에 있는 `basic_istream`을 할당합니다. `rvalue`복사본을 남기지 않는 참조와 관련 된 이동 할당입니다.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`basic_ifstream` 개체에 대한 `rvalue` 참조입니다.

### <a name="return-value"></a>반환 값

__* This__ 를 반환 합니다.

### <a name="remarks"></a>설명

멤버 연산자는를 호출 합니다 `swap(right)` .

## <a name="basic_istreampeek"></a><a name="peek"></a> basic_istream::p e

읽을 다음 문자를 반환합니다.

```cpp
int_type peek();
```

### <a name="return-value"></a>반환 값

읽을 다음 문자입니다.

### <a name="remarks"></a>설명

형식이 지정 되지 않은 입력 함수는를 반환 하는 것 처럼 가능한 경우 요소를 추출 `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc) 합니다. 그렇지 않으면를 반환 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a> basic_istream::p utback

지정된 문자를 스트림에 넣습니다.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>매개 변수

*Ch*\
스트림에 다시 배치할 문자입니다.

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

형식이 지정 되지 않은 [입력 함수](../standard-library/basic-istream-class.md) 는를 호출 하는 것 처럼 가능한 경우 *Ch* 를 다시 배치 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc) 합니다. `rdbuf`가 null 포인터 이거나에 대 한 호출이 반환 되는 `sputbackc` 경우 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 함수는를 호출 합니다 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . 어떤 경우 든 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a> basic_istream:: read

스트림에서 지정된 개수의 문자를 읽고 배열에 저장합니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

*문자열*\
문자를 읽을 배열입니다.

*수*\
읽을 문자 수입니다.

### <a name="return-value"></a>반환 값

스트림 ( **`*this`** )입니다.

### <a name="remarks"></a>설명

형식이 지정 되지 않은 입력 함수는 요소 *수를 계산* 하 여 *str* 에서 시작 하는 배열에 저장 합니다. 추출은 파일의 끝에서 일찍 중지 되며,이 경우 함수는를 호출 합니다 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . 어떤 경우 든 __* this__ 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a> basic_istream:: readsome

지정한 개수의 문자 값을 읽습니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

*문자열*\
`readsome`이 읽은 문자를 저장하는 배열입니다.

*수*\
읽을 문자 수입니다.

### <a name="return-value"></a>반환 값

실제로 읽은 문자 수 [`gcount`](#gcount) 입니다.

### <a name="remarks"></a>설명

이 형식이 지정 되지 않은 입력 함수는 입력 스트림에서 요소 *수를 계산* 하 여 배열 *str* 에 저장 합니다.

이 함수는 입력을 기다리지 않고, 읽을 수 있는 데이터는 무엇이든 읽습니다.

### <a name="example"></a>예제

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a> basic_istream:: seekg

스트림에서 읽기 위치를 이동합니다.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>매개 변수

*pos*\
읽기 포인터를 이동할 절대 위치입니다.

*해제*\
읽기 포인터를 기준으로 이동 하는 오프셋 *입니다.*

*방식은*\
[ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 열거형 중 하나입니다.

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 절대 검색을 수행하고 두 번째 멤버 함수는 상대 검색을 수행합니다.

> [!NOTE]
> 표준 C++는 텍스트 파일에서 상대 검색을 지원하지 않으므로 두 번째 멤버 함수를 텍스트 파일과 함께 사용하지 마세요.

[`fail`](../standard-library/basic-ios-class.md#fail)가 false 이면 첫 번째 멤버 함수는 `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)` 일부 `pos_type` 임시 개체에 대해를 `newpos` 호출 합니다. `fail`가 false 인 경우 두 번째 함수는를 호출 합니다 `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` . 두 경우 모두 `(off_type)newpos == (off_type)(-1)` (위치 지정 작업이 실패 하는 경우) 함수는를 호출 합니다 `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . 두 함수는 모두 __* this__ 를 반환 합니다.

[`fail`](../standard-library/basic-ios-class.md#fail)이 true 이면 멤버 함수는 아무 작업도 수행 하지 않습니다.

### <a name="example"></a>예제

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a> basic_istream:: sentry

중첩된 클래스는 선언에서 형식이 지정된 입력 함수 및 형식이 지정되지 않은 입력 함수를 구성하는 개체를 설명합니다.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>설명

`_Istr.` [`good`](../standard-library/basic-ios-class.md#good) 이 true 이면 생성자는 다음과 같습니다.

- `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) `_Istr.tie` 이 null 포인터가 아닌 경우를 호출 합니다.

- [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` 가 0이 아닌 경우를 효과적으로 호출 `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) 합니다.

이러한 준비가 완료 된 후 `_Istr.good` 가 false 이면 생성자는를 호출 `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 합니다. 어떤 경우 든 생성자는에서 반환 된 값을 저장 `_Istr.good` `status` 합니다. 를 나중에 호출 하면 `operator bool` 이 저장 된 값이 전달 됩니다.

## <a name="basic_istreamswap"></a><a name="swap"></a> basic_istream:: swap

두 `basic_istream` 개체의 내용을 교환합니다.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`basic_istream` 개체에 대한 lvalue 참조입니다.

### <a name="remarks"></a>설명

멤버 함수는를 호출 합니다 [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` . 또한 추출 개수를 *오른쪽* 의 추출 개수로 교환 합니다.

## <a name="basic_istreamsync"></a><a name="sync"></a> basic_istream:: sync

스트림의 연결 된 입력 장치를 스트림 버퍼와 동기화 합니다.

```cpp
int sync();
```

### <a name="return-value"></a>반환 값

[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)가 null 포인터인 경우 함수는-1을 반환 합니다. 그렇지 않으면를 호출 `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync) 합니다. 해당 호출에서-1을 반환 하는 경우 함수는 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 를 호출 하 고-1을 반환 합니다. 아닌 경우 함수는 0을 반환합니다.

## <a name="basic_istreamtellg"></a><a name="tellg"></a> basic_istream:: tellg

스트림에서 현재 읽기 위치를 보고합니다.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>반환 값

스트림 내의 현재 위치입니다.

### <a name="remarks"></a>설명

[`fail`](../standard-library/basic-ios-class.md#fail)가 false 이면 멤버 함수는를 반환 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` 합니다. 그렇지 않으면 `pos_type(-1)`을 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a> basic_istream:: unget

가장 최근에 읽은 문자를 다시 스트림에 넣습니다.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>반환 값

스트림입니다 (__* this__).

### <a name="remarks"></a>설명

형식이 지정 되지 않은 [입력 함수](../standard-library/basic-istream-class.md) 는를 호출 하는 것 처럼 가능한 경우 스트림의 이전 요소를 다시 배치 `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc) 합니다. [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)가 null 포인터 이거나에 대 한 호출이 반환 되는 `sungetc` 경우 `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof) 함수는를 호출 합니다 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . 어떤 경우 든 __* this__ 를 반환 합니다.

가 실패할 수 있는 방법에 대 한 자세한 내용은 `unget` 을 참조 하십시오 [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc) .

### <a name="example"></a>예제

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
