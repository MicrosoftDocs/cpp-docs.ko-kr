---
description: Time_put 클래스에 대해 자세히 알아보세요.
title: time_put 클래스
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 135bd8c619907b789f448e41e742fcc256d9b6eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167268"
---
# <a name="time_put-class"></a>time_put 클래스

클래스 템플릿에서는 시간 값을 형식의 시퀀스로 변환 하는 것을 제어 하는 로캘 패싯으로 사용할 수 있는 개체에 대해 설명 합니다 `CharType` .

## <a name="syntax"></a>구문

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>매개 변수

*CharType*\
문자를 인코딩하기 위해 프로그램 내 사용하는 형식

*OutputIterator*\
시간 put 함수가 출력을 쓰는 반복기의 형식입니다.

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 **id** 에 고유한 양수 값이 저장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[time_put](#time_put)|`time_put` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.|
|[iter_type](#iter_type)|출력 반복기에 대해 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[do_put](#do_put)|시간과 날짜 정보를 `CharType`의 시퀀스로 출력하는 가상 함수입니다.|
|[보관](#put)|시간과 날짜 정보를 `CharType`의 시퀀스로 출력합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="time_putchar_type"></a><a name="char_type"></a> time_put:: char_type

로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `CharType`의 동의어입니다.

## <a name="time_putdo_put"></a><a name="do_put"></a> time_put::d o_put

시간과 날짜 정보를 `CharType`의 시퀀스로 출력하는 가상 함수입니다.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>매개 변수

*그런*\
시간과 날짜를 나타내는 문자 시퀀스를 삽입할 출력 반복기입니다.

*_Iosbase*\
사용되지 않습니다.

*_Pt*\
출력되는 날짜 및 시간 정보입니다.

*_Fmt*\
출력의 형식입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

*_Mod*\
형식의 한정자입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

### <a name="return-value"></a>반환 값

삽입된 마지막 요소 뒤의 첫 번째 위치에 대한 반복기입니다.

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수는 `next` 형식의 개체에 저장 된 시간 값부터 시작 하 여 순차 요소를 생성 합니다 \* `_Pt` `tm` . 함수는 생성된 출력을 지나 요소를 삽입할 다음 위치를 지정하는 반복기를 반환합니다.

출력은에서 사용 하는 것과 동일한 규칙을 사용 하 여 `strftime` 일련의 요소를 배열에 생성 하는 *_Pt* 의 마지막 인수를 사용 하 여 생성 됩니다 **`char`** . 이러한 각 **`char`** 요소는 간단한 일대일 매핑으로 형식의 동등한 요소에 매핑되는 것으로 간주 됩니다 `CharType` . *_Mod* 0 인 경우 유효 형식은 "% f" 이며, 여기서 F는 *_Fmt* 로 바뀝니다. 그렇지 않으면 유효 형식은 "% MF" 이며, 여기서 M은 *_Mod* 로 바뀝니다.

### <a name="example"></a>예제

`do_put`을 호출하는 [put](#put)에 대한 예제를 참조하세요.

## <a name="time_putiter_type"></a><a name="iter_type"></a> time_put:: iter_type

출력 반복기에 대해 설명하는 형식입니다.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `OutputIterator`의 동의어입니다.

## <a name="time_putput"></a><a name="put"></a> time_put::p

시간과 날짜 정보를 `CharType`의 시퀀스로 출력합니다.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*그런*\
시간과 날짜를 나타내는 문자 시퀀스를 삽입할 출력 반복기입니다.

*_Iosbase*\
사용되지 않습니다.

*_Fill*\
`CharType`간격에 사용 되는 형식의 문자입니다.

*_Pt*\
출력되는 날짜 및 시간 정보입니다.

*_Fmt*\
출력의 형식입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

*_Mod*\
형식의 한정자입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

*기본*\
출력에 대한 서식 문자열의 시작 부분입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

*최신*\
출력에 대한 서식 문자열의 끝부분입니다. 유효한 값은 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)를 참조하세요.

### <a name="return-value"></a>반환 값

삽입된 마지막 요소 뒤의 첫 번째 위치에 대한 반복기입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [do_put](#do_put)( `next` , `_Iosbase` , `_Fill` , `_Pt` , `_Fmt` , `_Mod` )를 반환 합니다. 두 번째 멤버 함수는 \* `next` 백분율 (%)이 아닌 간격 [,)의 모든 요소에 복사 합니다 `first` `last` . [,) 간격의 백분율 뒤에 문자 *C* 가 오는 `first` 경우 `last` 함수는 `next`  =  `do_put` ( `next` ,, `_Iosbase` `_Fill` , `_Pt` , *C*, 0)을 계산 하 고 이전 *C* 를 건너뜁니다. 그러나 *C* 가 set EOQ #의 한정자 문자 다음에 `C2` 간격 [,)의 문자가 있으면 `first` `last` 함수는 대신 `next`  =  `do_put` ( `next` , `_Iosbase` ,,,, `_Fill` `_Pt` `C2` *C*)를 계산 하 고 이전을 건너뜁니다 `C2` .

### <a name="example"></a>예제

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_puttime_put"></a><a name="time_put"></a> time_put:: time_put

`time_put` 형식의 개체에 대한 생성자입니다.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>매개 변수

*_Refs*\
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

### <a name="remarks"></a>설명

*_Refs* 매개 변수에 사용할 수 있는 값과 해당 의미는 다음과 같습니다.

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \> 1: 이러한 값은 정의 되지 않습니다.

생성자는 [locale:: facet](../standard-library/locale-class.md#facet_class)(*_Refs*)를 사용 하 여 해당 기본 개체를 초기화 합니다.

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)\
[time_base 클래스](../standard-library/time-base-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
