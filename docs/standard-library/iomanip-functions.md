---
description: '자세한 정보: &lt; io마나트 ip &gt; 함수'
title: '&lt;iomanip&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: d9ddcea6b524c0413bc1c68c2b75ec910b529d22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323930"
---
# <a name="ltiomanipgt-functions"></a>&lt;iomanip&gt; 함수

[get_money](#iomanip_get_money)\
[get_time](#iomanip_get_time)\
[put_money](#iomanip_put_money)\
[put_time](#iomanip_put_time)\
[작은따옴표로](#quoted)\
[resetiosflags](#resetiosflags)\
[setbase](#setbase)\
[setfill](#setfill)\
[setiosflags](#setiosflags)\
[setprecision](#setprecision)\
[setw](#setw)

## <a name="get_money"></a><a name="iomanip_get_money"></a> get_money

원하는 형식을 사용하여 스트림에서 통화 값을 추출하고 매개 변수에서 값을 반환합니다.

```cpp
template <class Money>
T7 get_money(Money& amount, bool use_intl);
```

### <a name="parameters"></a>매개 변수

*많이*\
추출된 통화 값입니다.

*use_intl*\
인 경우 **`true`** 국가별 형식을 사용 합니다. 기본값은 **`false`** 입니다.

### <a name="remarks"></a>설명

조작자는 스트림에서 추출 될 때 `str` `formatted input function` `get` `money_get` `str` *use_intl* 를 사용 하 여 국가별 형식을 나타내는에 연결 된 로캘 패싯에 대해 멤버 함수를 호출 하는 개체를 반환 합니다. 성공 하면 호출이 *추출 된 통화 값으로 저장* 됩니다. 그런 다음 조작자는 `str`을 반환합니다.

`Money` 는 형식 **`long double`** 이거나 `basic_string` 와 동일한 요소 및 특성 매개 변수를 사용 하는 인스턴스화 여야 합니다 `str` .

## <a name="get_time"></a><a name="iomanip_get_time"></a> get_time

원하는 형식을 사용하여 스트림에서 시간 값을 추출합니다. 매개 변수의 값을 시간 구조로 반환합니다.

```cpp
template <class Elem>
T10 put_time(struct tm *time_ptr, const Elem *time_format);
```

### <a name="parameters"></a>매개 변수

*time_ptr*\
시간 구조 형식의 시간입니다.

*time_format*\
시간 구조를 가져오는 데 사용할 원하는 형식입니다.

### <a name="remarks"></a>설명

조작자는 `str` 스트림에서 추출될 경우 `formatted input function`처럼 동작하는 개체를 반환합니다. 이 입력 함수는 `str`과 연결된 로캘 패싯 `time_get`에 대해 멤버 함수 `get`을 호출하며, `tptr`을 사용하여 시간 구조를 나타내고 `fmt`를 사용하여 null로 끝나는 형식 문자열의 시작을 나타냅니다. 성공하면 추출된 시간 필드와 연결된 값을 시간 구조에 저장합니다. 그런 다음 조작자는 `str`을 반환합니다.

## <a name="put_money"></a><a name="iomanip_put_money"></a> put_money

원하는 형식을 사용하여 스트림에 금액을 삽입합니다.

```cpp
template <class Money>
T8 put_money(const Money& amount, bool use_intl);
```

### <a name="parameters"></a>매개 변수

*많이*\
스트림에 삽입할 금액입니다.

*use_intl*\
**`true`** 조작자가 국가별 형식을 사용 해야 하는 경우로 설정 하 고, 그렇지 않으면로 설정 **`false`** 합니다.

### <a name="return-value"></a>반환 값

`str`를 반환합니다.

### <a name="remarks"></a>설명

조작자는 `str` 스트림에 삽입될 경우 서식 있는 출력 함수처럼 동작하는 개체를 반환합니다. 이 출력 함수는 `str`과 연결된 로캘 패싯 `money_put`에 대해 멤버 함수 `put`을 호출합니다. 성공 하면 `amount` *use_intl* 를 사용 하 여 국제 형식 및를 채우기 요소로 사용 하 여 적절 하 게 형식이 지정 된 호출을 삽입 합니다 `str.fill()` . 그런 다음 조작자는 `str`을 반환합니다.

`Money` 는 형식 **`long double`** 이거나 `basic_string` 와 동일한 요소 및 특성 매개 변수를 사용 하는 인스턴스화 여야 합니다 `str` .

## <a name="put_time"></a><a name="iomanip_put_time"></a> put_time

지정된 형식을 사용하여 시간 구조에서 스트림으로 시간 값을 씁니다.

```cpp
template <class Elem>
T10 put_time(struct tm* time_ptr, const Elem* time_format);
```

### <a name="parameters"></a>매개 변수

*time_ptr*\
스트림에 쓸 시간 값으로, 시간 구조에 제공됩니다.

*time_format*\
시간 값을 쓸 원하는 형식입니다.

### <a name="remarks"></a>설명

조작자는 `str` 스트림에 삽입될 경우 `formatted output function`처럼 동작하는 개체를 반환합니다. 출력 함수는 `str`과 연결된 로캘 패킷 `time_put`에 대해 멤버 함수 `put`을 호출합니다. Output 함수는 *time_ptr* 을 사용 하 여 시간 구조를 나타내고 *time_format* null로 끝나는 형식 문자열의 시작을 표시 합니다. 성공하면 형식 문자열에서 리터럴 텍스트를 삽입하고 시간 구조에서 변환된 값을 삽입합니다. 그런 다음 조작자는 `str`을 반환합니다.

## <a name="quoted"></a><a name="quoted"></a> 작은따옴표로

**(C++14의 새로운 기능)** >> 및 << 연산자를 사용하여 스트림에 대한 문자열의 편리한 왕복을 가능하게 하는 iostream 조작자입니다.

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>매개 변수

*문자열*\
Std:: string, char \* , string 리터럴 또는 원시 문자열 리터럴 또는 이러한 형식의 전체 버전 (예: std:: wstring, wchar_t \* )

*문자가*\
문자열의 시작과 끝에 대한 구분 기호로 사용할 사용자 지정 문자 또는 와이드 문자입니다.

*이스케이프*\
문자열 내의 이스케이프 시퀀스에 대한 이스케이프 문자로 사용할 사용자 지정 문자 또는 와이드 문자입니다.

### <a name="remarks"></a>설명

[삽입 연산자 사용 및 형식 제어](../standard-library/using-insertion-operators-and-controlling-format.md)를 참조하세요.

### <a name="example"></a>예제

이 예제에서는 좁은 문자열을 사용하여 기본 구분 기호 및 이스케이프 문자와 함께 `quoted`를 사용하는 방법을 보여 줍니다. 와이드 문자열도 동일하게 지원됩니다.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_quoted_v_nonquoted()
{
    // Results are identical regardless of input string type:
    // string inserted { R"(This is a "sentence".)" }; // raw string literal
    // string inserted { "This is a \"sentence\"." };  // regular string literal
    const char* inserted = "This is a \"sentence\".";  // const char*
    stringstream ss, ss_quoted;
    string extracted, extracted_quoted;

    ss << inserted;
    ss_quoted << quoted(inserted);

    cout << "ss.str() is storing       : " << ss.str() << endl;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;

    // Round-trip the strings
    ss >> extracted;
    ss_quoted >> quoted(extracted_quoted);

    cout << "After round trip: " << endl;
    cout << "Non-quoted      : " << extracted << endl;
    cout << "Quoted          : " << extracted_quoted << endl;
}

int main(int argc, char* argv[])
{
    show_quoted_v_nonquoted();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}

/* Output:
ss.str() is storing       : This is a "sentence".
ss_quoted.str() is storing: "This is a \"sentence\"."

After round trip:
Non-quoted      : This
Quoted          : This is a "sentence".

Press Enter to exit
*/
```

### <a name="example"></a>예제

다음 예제에서는 사용자 지정 구분 기호 및/또는 이스케이프 문자를 제공하는 방법을 보여 줍니다.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_custom_delimiter()
{
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    stringstream ss, ss_quoted;
    string extracted;

    ss_quoted << quoted(inserted, '*');
    ss << inserted;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;

    // Use the same quoted arguments as on insertion.
    ss_quoted >> quoted(extracted, '*');

    cout << "After round trip: " << endl;
    cout << "Quoted          : " << extracted << endl;

    extracted = {};
    ss >> extracted;
    cout << "Non-quoted      : " << extracted << endl << endl;
}

void show_custom_escape()
{
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };
    stringstream ss, ss_quoted, ss_quoted_custom;
    string extracted;

    // Use '"' as delimiter and '~' as escape character.
    ss_quoted_custom << quoted(inserted, '"', '~');
    ss_quoted << quoted(inserted);
    ss << inserted;
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;
    cout << "ss.str()              : " << ss.str() << endl << endl;

    // No spaces in this string, so non-quoted behaves same as quoted
    // after round-tripping.
}

int main(int argc, char* argv[])
{
    cout << "Custom delimiter:" << endl;
    show_custom_delimiter();
    cout << "Custom escape character:" << endl;
    show_custom_escape();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}
/* Output:
Custom delimiter:
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".

After round trip:
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".
Non-quoted      : "This"

Custom escape character:
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"
ss.str()              : \\root\trunk\branch\nest\egg\yolk

Press Enter to exit
*/
```

## <a name="resetiosflags"></a><a name="resetiosflags"></a> resetiosflags

지정된 플래그를 지웁니다.

```cpp
T1 resetiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>매개 변수

*마스크할*\
선택을 취소할 플래그입니다.

### <a name="return-value"></a>반환 값

조작자는 스트림에서 추출 하거나 스트림에 삽입 하는 경우 `str` `str.` [setf](../standard-library/ios-base-class.md#setf) `(ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags)를 호출 하 고를 반환 하는 개체를 반환 `, mask)` `str` 합니다.

### <a name="example"></a>예제

`resetiosflags` 사용 예제는 [setw](../standard-library/iomanip-functions.md#setw)를 참조하세요.

## <a name="setbase"></a><a name="setbase"></a> setbase

정수의 밑을 설정합니다.

```cpp
T3 setbase(int base);
```

### <a name="parameters"></a>매개 변수

*하단*\
숫자 밑입니다.

### <a name="return-value"></a>반환 값

조작자는 스트림에서 추출 하거나 스트림에 삽입 하는 경우 `str` `str.setf(mask,` [ios_base:: basefield](../standard-library/ios-base-class.md#fmtflags)를 호출 하 고를 반환 하는 개체를 반환 `)` `str` 합니다. 여기서 `mask` 는 다음과 같이 결정 됩니다.

- *Base* 가 8 이면 `mask` `ios_base::` [10 월](../standard-library/ios-functions.md#oct)입니다.

- *Base* 가 10 인 경우 mask는 `ios_base::` [12 월](../standard-library/ios-functions.md#dec)입니다.

- *Base* 가 16 인 경우 `mask` 는 16 `ios_base::` [진수](../standard-library/ios-functions.md#hex)입니다.

- *Base* 가 다른 값 이면 mask는 `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags)입니다 `(0)` .

### <a name="example"></a>예제

`setbase` 사용 예제는 [setw](../standard-library/iomanip-functions.md#setw)를 참조하세요.

## <a name="setfill"></a><a name="setfill"></a> setfill

오른쪽 맞춤된 디스플레이에서 공백을 채우는데 사용할 문자를 설정합니다.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>매개 변수

*Ch*\
오른쪽 맞춤된 디스플레이에서 공백을 채우는데 사용할 문자입니다.

### <a name="return-value"></a>반환 값

템플릿 조작자는 스트림에 추출 하거나 스트림에 삽입 하는 경우 `str` `str.` [fill](../standard-library/basic-ios-class.md#fill) `(Ch)` 을 호출 하 고를 반환 하는 개체를 반환 합니다 `str` . 형식은 `Elem` 스트림의 요소 형식과 동일 해야 합니다 `str` .

### <a name="example"></a>예제

`setfill` 사용 예제는 [setw](../standard-library/iomanip-functions.md#setw)를 참조하세요.

## <a name="setiosflags"></a><a name="setiosflags"></a> setiosflags

지정된 플래그를 설정합니다.

```cpp
T2 setiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>매개 변수

*마스크할*\
설정할 플래그입니다.

### <a name="return-value"></a>반환 값

조작자는 스트림에서 추출 하거나 스트림에 삽입 하는 경우 `str` `str.` [setf](../standard-library/ios-base-class.md#setf) `(mask)` 를 호출 하 고를 반환 하는 개체를 반환 합니다 `str` .

### <a name="example"></a>예제

`setiosflags` 사용 예제는 [setw](../standard-library/iomanip-functions.md#setw)를 참조하세요.

## <a name="setprecision"></a><a name="setprecision"></a> setprecision

부동 소수점 값의 전체 자릿수를 설정합니다.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>매개 변수

*Prec*\
부동 소수점 값의 전체 자릿수입니다.

### <a name="return-value"></a>반환 값

조작자는 스트림에서 추출 하거나 스트림에 삽입 하 `str` `str.` 고 [전체 자릿수](../standard-library/ios-base-class.md#precision)를 호출한 다음을 반환 하는 개체를 반환 `(Prec)` `str` 합니다.

### <a name="example"></a>예제

`setprecision` 사용 예제는 [setw](../standard-library/iomanip-functions.md#setw)를 참조하세요.

## <a name="setw"></a><a name="setw"></a> setw

스트림에서 다음 요소에 대한 표시 필드의 너비를 지정합니다.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>매개 변수

*전반적인*\
표시 필드의 너비입니다.

### <a name="return-value"></a>반환 값

조작자는 스트림에서 추출 하거나 스트림에 삽입 하는 경우 너비를 호출 하 고를 반환 하는 개체를 반환 `str` `str.` [](../standard-library/ios-base-class.md#width) `(Wide)` `str` 합니다.

### <a name="remarks"></a>설명

setw는 스트림에서 다음 요소에 대한 너비만 설정하며 너비를 지정하려는 각 요소 앞에 삽입되어야 합니다.

### <a name="example"></a>예제

```cpp
// iomanip_setw.cpp
// compile with: /EHsc
// Defines the entry point for the console application.
//
// Sample use of the following manipulators:
//   resetiosflags
//   setiosflags
//   setbase
//   setfill
//   setprecision
//   setw

#include <iostream>
#include <iomanip>

using namespace std;

const double   d1 = 1.23456789;
const double   d2 = 12.3456789;
const double   d3 = 123.456789;
const double   d4 = 1234.56789;
const double   d5 = 12345.6789;
const long      l1 = 16;
const long      l2 = 256;
const long      l3 = 1024;
const long      l4 = 4096;
const long      l5 = 65536;
int         base = 10;

void DisplayDefault( )
{
   cout << endl << "default display" << endl;
   cout << "d1 = " << d1 << endl;
   cout << "d2 = " << d2 << endl;
   cout << "d3 = " << d3 << endl;
   cout << "d4 = " << d4 << endl;
   cout << "d5 = " << d5 << endl;
}

void DisplayWidth( int n )
{
   cout << endl << "fixed width display set to " << n << ".\n";
   cout << "d1 = " << setw(n) << d1 << endl;
   cout << "d2 = " << setw(n) << d2 << endl;
   cout << "d3 = " << setw(n) << d3 << endl;
   cout << "d4 = " << setw(n) << d4 << endl;
   cout << "d5 = " << setw(n) << d5 << endl;
}

void DisplayLongs( )
{
   cout << setbase(10);
   cout << endl << "setbase(" << base << ")" << endl;
   cout << setbase(base);
   cout << "l1 = " << l1 << endl;
   cout << "l2 = " << l2 << endl;
   cout << "l3 = " << l3 << endl;
   cout << "l4 = " << l4 << endl;
   cout << "l5 = " << l5 << endl;
}

int main( int argc, char* argv[] )
{
   DisplayDefault( );

   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);
   DisplayDefault( );

   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);
   DisplayDefault( );

   cout << setiosflags(ios_base::scientific);
   cout << endl << "setiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << resetiosflags(ios_base::scientific);
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << endl << "setfill('" << 'S' << "')" << setfill('S');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);
   DisplayWidth(10);
   DisplayDefault( );

   base = 16;
   DisplayLongs( );

   base = 8;
   DisplayLongs( );

   base = 10;
   DisplayLongs( );

   return   0;
}
```

```Output

default display
d1 = 1.23457
d2 = 12.3457
d3 = 123.457
d4 = 1234.57
d5 = 12345.7

setprecision(3)
default display
d1 = 1.23
d2 = 12.3
d3 = 123
d4 = 1.23e+003
d5 = 1.23e+004

setprecision(12)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setiosflags(4096)
default display
d1 = 1.234567890000e+000
d2 = 1.234567890000e+001
d3 = 1.234567890000e+002
d4 = 1.234567890000e+003
d5 = 1.234567890000e+004

resetiosflags(4096)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill('S')
fixed width display set to 15.
d1 = SSSSS1.23456789
d2 = SSSSS12.3456789
d3 = SSSSS123.456789
d4 = SSSSS1234.56789
d5 = SSSSS12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill(' ')
fixed width display set to 15.
d1 =      1.23456789
d2 =      12.3456789
d3 =      123.456789
d4 =      1234.56789
d5 =      12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setprecision(8)
fixed width display set to 10.
d1 =  1.2345679
d2 =  12.345679
d3 =  123.45679
d4 =  1234.5679
d5 =  12345.679

default display
d1 = 1.2345679
d2 = 12.345679
d3 = 123.45679
d4 = 1234.5679
d5 = 12345.679

setbase(16)
l1 = 10
l2 = 100
l3 = 400
l4 = 1000
l5 = 10000

setbase(8)
l1 = 20
l2 = 400
l3 = 2000
l4 = 10000
l5 = 200000

setbase(10)
l1 = 16
l2 = 256
l3 = 1024
l4 = 4096
l5 = 65536
```

## <a name="see-also"></a>참고 항목

[\<iomanip>](../standard-library/iomanip.md)
