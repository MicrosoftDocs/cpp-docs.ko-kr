---
description: Time_get 클래스에 대해 자세히 알아보세요.
title: time_get 클래스
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: 079929d66ceb124fbceb1a908fbe9a868c446471
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167294"
---
# <a name="time_get-class"></a>time_get 클래스

클래스 템플릿은 형식의 시퀀스에서 시간 값으로의 변환을 제어 하는 로캘 패싯으로 사용할 수 있는 개체를 설명 합니다 `CharType` .

## <a name="syntax"></a>구문

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>매개 변수

*CharType*\
문자를 인코딩하기 위해 프로그램 내 사용하는 형식

*InputIterator*\
시간 값을 읽어올 반복기입니다.

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 **id** 에 고유한 양수 값이 저장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[time_get](#time_get)|`time_get` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.|
|[iter_type](#iter_type)|입력 반복기에 대해 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[date_order](#date_order)|패싯에서 사용하는 날짜 순서를 반환합니다.|
|[do_date_order](#do_date_order)|패싯에서 사용하는 날짜 순서를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_get](#do_get)|문자 데이터를 읽고 시간 값으로 변환합니다.|
|[do_get_date](#do_get_date)|문자열을 `x` 지정자가 `strftime`에 대해 만든 날짜로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_get_monthname](#do_get_monthname)|문자열을 월 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_get_time](#do_get_time)|문자열을 `X` 지정자가 `strftime`에 대해 만든 날짜로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_get_weekday](#do_get_weekday)|문자열을 요일 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_get_year](#do_get_year)|문자열을 연도 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[get](#get)|문자 데이터 소스를 읽고 해당 데이터를 시간 구조체에 저장된 시간으로 변환합니다.|
|[get_date](#get_date)|문자열을 `x` 지정자가 `strftime`에 대해 만든 날짜로 구문 분석합니다.|
|[get_monthname](#get_monthname)|문자열을 월 이름으로 구문 분석합니다.|
|[get_time](#get_time)|문자열을 `X` 지정자가 `strftime`에 대해 만든 날짜로 구문 분석합니다.|
|[get_weekday](#get_weekday)|문자열을 요일 이름으로 구문 분석합니다.|
|[get_year](#get_year)|문자열을 연도 이름으로 구문 분석합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="time_getchar_type"></a><a name="char_type"></a> time_get:: char_type

로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **Chartype** 의 동의어입니다.

## <a name="time_getdate_order"></a><a name="date_order"></a> time_get::d ate_order

패싯에서 사용하는 날짜 순서를 반환합니다.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>반환 값

패싯에서 사용하는 날짜 순서입니다.

### <a name="remarks"></a>설명

구성원 함수는 [do_date_order](#do_date_order)를 반환합니다.

### <a name="example"></a>예제

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a> time_get::d o_date_order

패싯에서 사용하는 날짜 순서를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>반환 값

패싯에서 사용하는 날짜 순서입니다.

### <a name="remarks"></a>설명

보호된 가상 구성원 함수는 [do_get_date](#do_get_date)를 통해 날짜 구성 요소 일치를 확인하는 순서를 설명하는 **time_base::dateorder** 형식의 값을 반환합니다. 이 구현에서 값은 1979년 12월 2일 형식의 날짜에 해당하는 **time_base::mdy** 입니다.

### <a name="example"></a>예제

`do_date_order`를 호출하는 [date_order](#date_order)에 대한 예제를 참조하세요.

## <a name="time_getdo_get"></a><a name="do_get"></a> time_get::d o_get

문자 데이터를 읽고 시간 값으로 변환합니다. 하나의 변환 지정자 및 한정자를 허용합니다.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작을 나타내는 입력 반복기입니다.

*최신*\
시퀀스의 끝을 나타내는 입력 반복기입니다.

*iosbase*\
스트림 개체입니다.

*상태일*\
오류를 나타내기 위해 적절 한 비트 마스크 요소가 설정 된 iosbase의 필드입니다.

*ptm*\
시간이 저장되는 시간 구조에 대한 포인터입니다.

*bcp.fmt*\
변환 지정자 문자입니다.

*연산을*\
선택적 한정자 문자입니다.

### <a name="return-value"></a>반환 값

변환되지 않은 첫 번째 요소를 지정하는 반복기를 반환합니다. 변환에 실패 하면에서이 설정 되 `ios_base::failbit` `state` 고는 *먼저* 반환 됩니다.

### <a name="remarks"></a>설명

가상 멤버 함수는 [,) 범위에서 하나 이상의 입력 요소를 변환 및 `first` 건너뛰어 `last` 의 하나 이상의 멤버에 저장 된 값을 확인 합니다 `*pt` . 변환에 실패 하면에서이 설정 되 `ios_base::failbit` `state` 고는 *먼저* 반환 됩니다. 그렇지 않은 경우 함수는 변환되지 않은 첫 번째 요소를 지정하는 반복기를 반환합니다.

변환 지정자는 다음과 같습니다.

`'a'` 또는 `'A'` - [time_get::get_weekday](#get_weekday)와 동일하게 동작합니다.

`'b'`, `'B'` 또는 `'h'` -- [time_get::get_monthname](#get_monthname)와 동일하게 동작합니다.

`'c'` - `"%b %d %H : %M : %S %Y"`와 동일하게 동작합니다.

`'C'` - [0, 99] 범위의 10진수 입력 필드를 `val` 값으로 변환하고 `val * 100 - 1900`을 `pt-&tm_year`에 저장합니다.

`'d'` 또는 `'e'` - [1, 31] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_mday`에 저장합니다.

`'D'` - `"%m / %d / %y"`와 동일하게 동작합니다.

`'H'` - [0, 23] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_hour`에 저장합니다.

`'I'` - [0, 11] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_hour`에 저장합니다.

`'j'` - [1, 366] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_yday`에 저장합니다.

`'m'` - [1, 12] 범위의 10진수 입력 필드를 `val` 값으로 변환하고 `val - 1`을 저장한 다음 해당 값을 `pt-&tm_mon`에 저장합니다.

`'M'` - [0, 59] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_min`에 저장합니다.

`'n'` 또는 `'t'` - `" "`와 동일하게 동작합니다.

`'p'` - "AM" 또는 "am"을 0으로 변환하고 "PM" 또는 "PM"을 12로 변환한 다음 이 값을 `pt-&tm_hour`에 추가합니다.

`'r'` - `"%I : %M : %S %p"`와 동일하게 동작합니다.

`'R'` - `"%H %M"`와 동일하게 동작합니다.

`'S'` - [0, 59] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_sec`에 저장합니다.

`'T'` 또는 `'X'` - `"%H : %M : S"`와 동일하게 동작합니다.

`'U'` - [0, 53] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_yday`에 저장합니다.

`'w'` - [0, 6] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_wday`에 저장합니다.

`'W'` - [0, 53] 범위의 10진수 입력 필드를 변환하고 해당 값을 `pt-&tm_yday`에 저장합니다.

`'x'` - `"%d / %m / %y"`와 동일하게 동작합니다.

`'y'` - [0, 99] 범위의 10진수 입력 필드를 `val` 값으로 변환하고 `val < 69  val + 100 : val`을 `pt-&tm_year`에 저장합니다.

`'Y'` - [time_get::get_year](#get_year)와 동일하게 동작합니다.

다른 변환 지정자는 `ios_base::failbit`를 `state`로 설정하고 반환됩니다. 이 구현에서는 한정자가 아무 영향도 주지 않습니다.

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a> time_get::d o_get_date

문자열을 *x* 지정자가 `strftime`에 대해 만든 날짜로 구문 분석하기 위해 호출하는 보호된 가상 구성원 함수입니다.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
날짜 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

보호된 가상 구성원 함수는 비어 있지 않은 완전한 날짜 입력 필드를 인식할 때까지 시퀀스 [ `first`, `last`)에서 처음 시작되는 순차 요소 일치를 시도합니다. 성공 하면이 필드를 **tm:: tm \_ mon**, **tm:: tm \_ day** 및 **tm:: tm \_ year** 구성 요소와 동일한 값으로 변환 하 고 결과를 각각, 및에 저장 `ptm->tm_mon` `ptm->tm_day` `ptm->tm_year` 합니다. 이 함수는 날짜 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 `iosbase::failbit` *상태* 를 설정 합니다. 그리고 유효한 날짜 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

날짜 입력 필드의 형식은 로캘에 따라 달랄집니다. 기본 로캘의경우 날짜 입력 필드의 형식은 MMM DD, YYYY입니다. 여기서 각 항목의 의미는 다음과 같습니다.

- MMM은 [get_monthname](#get_monthname)을 호출해 일치시키며, 월을 제공합니다.

- DD는 해당하는 숫자 값이 [1, 31] 범위에 있어야 하는 10진수 시퀀스로, 일을 제공합니다.

- YYYY는 [get_year](#get_year)를 호출하여 일치시키며, 년을 제공합니다.

리터럴 공백 및 쉼표는 입력 시퀀스의 해당 요소와 일치해야 합니다.

### <a name="example"></a>예제

`do_get_date`를 호출하는 [get_date](#get_date)에 대한 예제를 참조하세요.

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a> time_get::d o_get_monthname

문자열을 월 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
사용되지 않습니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정하는 출력 매개 변수입니다.

*ptm*\
월 정보를 저장할 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

보호된 가상 구성원 함수는 비어 있지 않은 완전한 월 입력 필드를 인식할 때까지 시퀀스 [ `first`, `last`)에서 처음 시작되는 순차 요소 일치를 시도합니다. 성공 하는 경우이 필드는 구성 요소 **tm:: tm \_ mon** 과 동일한 값으로 변환 하 고 결과를에 저장 `ptm->tm_mon` 합니다. 이 함수는 월 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 `ios_base::failbit` *상태* 를 설정 합니다. 그리고 유효한 월 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

월 입력 필드는 1, 1월, 2, 2월 등의 로캘별 시퀀스 집합 중 가장 긴 항목과 일치하는 시퀀스입니다. 변환된 값은 1월 이후 지난 개월 수입니다.

### <a name="example"></a>예제

`do_get_monthname`을 호출하는 [get_monthname](#get_monthname)에 대한 예제를 참조하세요.

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a> time_get::d o_get_time

문자열을 *X* 지정 자가에 대해 만든 날짜로 구문 분석 하기 위해 호출 하는 보호 된 가상 멤버 함수입니다 `strftime` .

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
사용되지 않습니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
날짜 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

보호된 가상 구성원 함수는 비어 있지 않은 완전한 시간 입력 필드를 인식할 때까지 시퀀스[ `first`, `last`)에서 처음 시작되는 순차 요소 일치를 시도합니다. 성공 하면이 필드를, 및 구성 요소와 동등한 값으로 변환 `tm::tm_hour` 하 `tm::tm_min` `tm::tm_sec` 고 결과를 각각, 및에 저장 `ptm->tm_hour` `ptm->tm_min` `ptm->tm_sec` 합니다. 이 함수는 시간 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 `ios_base::failbit` *상태* 를 설정 합니다. 그리고 유효한 시간 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

이 구현에서 시간 입력 필드의 형식은 HH:MM:SS입니다. 여기서 각 항목의 의미는 다음과 같습니다.

- HH는 해당하는 숫자 값이 [0, 24) 범위에 있어야 하는 10진수 시퀀스로, 시간을 제공합니다.

- MM은 해당하는 숫자 값이 [0, 60) 범위에 있어야 하는 10진수 시퀀스로, 분을 제공합니다.

- SS는 해당하는 숫자 값이 [0, 60) 범위에 있어야 하는 10진수 시퀀스로, 초를 제공합니다.

리터럴 콜론은 입력 시퀀스의 해당 요소와 일치해야 합니다.

### <a name="example"></a>예제

`do_get_time`을 호출하는 [get_time](#get_time)에 대한 예제를 참조하세요.

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a> time_get::d o_get_weekday

문자열을 요일 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
요일 정보를 저장할 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

가상 보호 된 멤버 함수는  `first` `last` 비어 있지 않은 완전 한 요일 입력 필드를 인식할 때까지 시퀀스 [,)에서 처음 시작 되는 순차 요소를 일치 시 키 려 고 합니다. 성공 하는 경우이 필드를 **tm:: tm \_ wday** 구성 요소와 동일한 값으로 변환 하 고 결과를에 저장 `ptm->tm_wday` 합니다. 이 함수는 요일 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 `ios_base::failbit` *상태* 를 설정 합니다. 그리고 유효한 요일 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

요일 입력 필드는 일, 일요일, 월, 월요일 등의 로캘별 시퀀스 집합 중 가장 긴 항목과 일치하는 시퀀스입니다. 변환된 값은 일요일 이후 지난 일 수입니다.

### <a name="example"></a>예제

`do_get_weekday`를 호출하는 [get_weekday](#get_weekday)에 대한 예제를 참조하세요.

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a> time_get::d o_get_year

문자열을 연도 이름으로 구문 분석하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
연도 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

가상 보호 된 멤버 함수는  `first` `last` 비어 있지 않은 완전 한 연도 입력 필드를 인식할 때까지 시퀀스 [,)에서 처음 시작 되는 순차 요소를 일치 시 키 려 고 합니다. 성공 하면이 필드를 **tm:: tm \_ year** 구성 요소와 동일한 값으로 변환 하 고 결과를에 저장 `ptm->tm_year` 합니다. 이 함수는 연도 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 `ios_base::failbit` *상태* 를 설정 합니다. 그리고 유효한 연도 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

연도 입력 필드는 해당하는 숫자 값이 [1900, 2036) 범위에 있어야 하는 10진수 시퀀스입니다. 이 값에서 1900을 뺀 값이 저장됩니다. 이 구현에서는 [69, 136) 범위의 값이 연도 범위 [1969, 2036)을 나타냅니다. [0, 69) 범위의 값도 사용 가능하지만 이 값은 특정 변환 환경에 따라 연도 범위 [1900, 1969) 또는 [2000, 2069)를 나타낼 수 있습니다.

### <a name="example"></a>예제

`do_get_year`를 호출하는 [get_year](#get_year)에 대한 예제를 참조하세요.

## <a name="time_getget"></a><a name="get"></a> time_get:: get

문자 데이터 소스를 읽고 해당 데이터를 시간 구조체에 저장된 시간으로 변환합니다. 첫 번째 함수는 하나의 변환 지정자 및 한정자를 허용하고, 두 번째 함수는 여러 개 허용합니다.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 위치를 나타내는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝 부분을 나타내는 입력 반복기입니다.

*iosbase*\
스트림입니다.

*상태일*\
적절한 비트 마스크 요소는 스트림 상태가 오류를 나타내도록 설정됩니다.

*ptm*\
시간을 저장할 시간 구조에 대한 포인터입니다.

*bcp.fmt*\
변환 지정자 문자입니다.

*연산을*\
선택적 한정자 문자입니다.

*fmt_first*\
형식 지시문의 시작 위치를 가리킵니다.

*fmt_last*\
형식 지시문의 끝을 가리킵니다.

### <a name="return-value"></a>반환 값

시간 구조체를 할당 하는 데 사용 된 데이터 뒤의 첫 번째 문자에 대 한 반복기를 반환 합니다 `*ptm` .

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 `do_get(first, last, iosbase, state, ptm, fmt, mod)`을 반환합니다.

두 번째 구성원 함수는 `[fmt_first, fmt_last)`로 구분된 형식에 의해 제어되는 `do_get`을 호출합니다. 형식을 필드 시퀀스로 취급하며, 각 필드는 `[first, last)`로 구분된 0개 이상의 입력 요소의 변환을 결정합니다. 변환되지 않은 첫 번째 요소를 지정하는 반복기를 반환합니다. 다음과 같이 세 종류의 필드가 있습니다.

(%) (%) 형식에서 set [EOQ #]의 선택적 한정자 *mod* 와 변환 지정자 *fmt* 가 차례로 오는 형식으로 *먼저* 를에서 반환 된 값으로 바꿉니다 `do_get(first, last, iosbase, state, ptm, fmt, mod)` . 변환 실패가 상태를 `ios_base::failbit` 설정  하 고를 반환 합니다.

이 형식에 있는 공백 요소는 0개 이상의 입력 공백 요소를 건너뜁니다.

이 형식에 있는 다른 모든 요소는 건너뛰는 그 다음 입력 요소와 일치해야 합니다. 일치 실패가 `ios_base::failbit` *상태* 에서 설정 되 고이 반환 됩니다.

## <a name="time_getget_date"></a><a name="get_date"></a> time_get:: get_date

문자열을 *x* 지정자가 `strftime`에 대해 만든 날짜로 구문 분석합니다.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
날짜 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_get_date](#do_get_date)( `first` , `last` , `iosbase` , `state` ,) `ptm` 를 반환 합니다.

월은 0~11 범위로 계산됩니다.

### <a name="example"></a>예제

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_monthname"></a><a name="get_monthname"></a> time_get:: get_monthname

문자열을 월 이름으로 구문 분석합니다.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
사용되지 않습니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정하는 출력 매개 변수입니다.

*ptm*\
월 정보를 저장할 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_get_monthname](#do_get_monthname)( `first` , `last` , `iosbase` , `state` ,) `ptm` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_time"></a><a name="get_time"></a> time_get:: get_time

문자열을 *X* 지정 자가에 대해 만든 날짜로 구문 분석 `strftime` 합니다.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
사용되지 않습니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
날짜 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_get_time](#do_get_time)( `first` , `last` , `iosbase` , `state` ,) `ptm` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="time_getget_weekday"></a><a name="get_weekday"></a> time_get:: get_weekday

문자열을 요일 이름으로 구문 분석합니다.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
요일 정보를 저장할 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_get_weekday](#do_get_weekday)( `first` , `last` , `iosbase` , `state` ,) `ptm` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="time_getget_year"></a><a name="get_year"></a> time_get:: get_year

문자열을 연도 이름으로 구문 분석합니다.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 시퀀스의 시작 부분 주소를 지정하는 입력 반복기입니다.

*최신*\
변환할 시퀀스의 끝부분 주소를 지정하는 입력 반복기입니다.

*iosbase*\
집합이 통화 기호가 선택 사항임을 나타낼 때 사용하는 형식 플래그입니다. 그 외의 경우 통화 기호는 필수 항목입니다.

*상태일*\
작업 성공 여부에 따라 스트림 상태에 대해 적절한 비트 마스크 요소를 설정합니다.

*ptm*\
연도 정보를 저장할 위치에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

입력 필드를 벗어난 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_get_year](#do_get_year)( `first` , `last` , `iosbase` , `state` ,) `ptm` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="time_getiter_type"></a><a name="iter_type"></a> time_get:: iter_type

입력 반복기에 대해 설명하는 형식입니다.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **InputIterator** 와 동일한 의미입니다.

## <a name="time_gettime_get"></a><a name="time_get"></a> time_get:: time_get

`time_get` 형식의 개체에 대한 생성자입니다.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>매개 변수

*refs*\
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

### <a name="remarks"></a>설명

*Refs* 매개 변수에 사용할 수 있는 값은 다음과 같습니다.

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \> 1: 이러한 값은 정의 되지 않습니다.

소멸자는 보호되므로 직접적인 예제는 확인할 수 없습니다.

생성자는 **locale::**[facet](../standard-library/locale-class.md#facet_class)()를 사용 하 여 해당 기본 개체를 초기화 `refs` 합니다.

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)\
[time_base 클래스](../standard-library/time-base-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
