---
description: Basic_ios 클래스에 대해 자세히 알아보세요.
title: basic_ios 클래스
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: 54b70092860002b85b2a603ad5d4dc5a611007ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321549"
---
# <a name="basic_ios-class"></a>basic_ios 클래스

클래스 템플릿은 템플릿 매개 변수에 따라 달라 지는 입력 스트림 (클래스 템플릿 [basic_istream](../standard-library/basic-istream-class.md)의 경우) 및 출력 스트림 (클래스 템플릿 [basic_ostream](../standard-library/basic-ostream-class.md))에 공통 된 저장소 및 멤버 함수를 설명 합니다. (클래스 [ios_base](../standard-library/ios-base-class.md) 는 일반적 이며 템플릿 매개 변수에 종속 되지 않는 것을 설명 합니다.) 클래스 **basic_ios \<class Elem, class Traits>** 의 개체는 `Elem` 문자 특성이 클래스에 의해 결정 되는 형식의 요소가 포함 된 스트림을 제어 하는 데 도움이 됩니다 `Traits` .

## <a name="syntax"></a>구문

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>매개 변수

*E*\
문자 형식입니다.

*특징이*\
문자 형식에 대 한 정보를 제공 하는 형식으로, 기본적으로로 설정 `char_traits < Elem >` 됩니다.

## <a name="remarks"></a>설명

**Basic_ios \<class Elem, class Traits>** 저장소 클래스의 개체:

- Basic_istream 형식의 개체에 대 한 동률 포인터 [](../standard-library/basic-istream-class.md) **\<Elem, Traits>** 입니다.

- Basic_streambuf 형식의 개체에 대 한 스트림 버퍼 포인터 [](../standard-library/basic-streambuf-class.md) **\<Elem, Traits >** 입니다.

- [서식 정보](../standard-library/ios-base-class.md)

- [ios_base](../standard-library/ios-base-class.md) 형식의 기준 개체에 있는 [스트림 상태 정보](../standard-library/ios-base-class.md)

- `char_type` 형식의 개체에 있는 채우기 문자

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_ios](#basic_ios)|`basic_ios` 클래스를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|템플릿 매개 변수 `Elem`의 동의어.|
|[int_type](#int_type)|`Traits::int_type`의 동의어입니다.|
|[off_type](#off_type)|`Traits::off_type`의 동의어입니다.|
|[pos_type](#pos_type)|`Traits::pos_type`의 동의어입니다.|
|[traits_type](#traits_type)|템플릿 매개 변수 `Traits`의 동의어.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[올바르지](#bad)|스트림 버퍼의 무결성 손실을 나타냅니다.|
|[clear](#clear)|오류 플래그를 모두 지웁니다.|
|[copyfmt](#copyfmt)|스트림 간에 플래그를 복사합니다.|
|[객체](#eof)|스트림의 끝에 도달했는지 여부를 나타냅니다.|
|[exceptions](#exceptions)|스트림에서 발생하는 예외를 나타냅니다.|
|[통과](#fail)|스트림에서 유효한 필드 추출 실패를 나타냅니다.|
|[칠할](#fill)|텍스트가 스트림만큼 넓지 않을 경우 사용할 문자를 지정하거나 반환합니다.|
|[good](#good)|스트림 상태가 양호함을 나타냅니다.|
|[imbue](#imbue)|로캘을 변경합니다.|
|[init](#init)|`basic_ios` 생성자에 의해 호출됩니다.|
|[move](#move)|스트림 버퍼에 대한 포인터를 제외하고 매개 변수의 모든 값을 현재 개체로 이동합니다.|
|[narrow](#narrow)|지정된 `char_type`에 해당하는 char를 찾습니다.|
|[rdbuf](#rdbuf)|스트림을 지정된 버퍼로 라우트합니다.|
|[rdstate](#rdstate)|플래그에 대한 비트 상태를 읽습니다.|
|[set_rdbuf](#set_rdbuf)|이 스트림 개체에 대한 읽기 버퍼로 사용할 스트림 버퍼를 할당합니다.|
|[setstate](#setstate)|추가 플래그를 설정합니다.|
|[스왑을](#swap)|이 `basic_ios` 개체의 값을 다른 `basic_ios` 개체의 값으로 교환합니다. 스트림 버퍼에 대한 포인터는 교환되지 않습니다.|
|[tie](#tie)|한 스트림이 다른 스트림보다 먼저 처리되도록 합니다.|
|[widen](#widen)|지정된 char에 해당하는 `char_type`을 찾습니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[explicit operator bool](#op_bool)|개체를로 사용할 수 있습니다 `basic_ios` **`bool`** . 일반적이고 의도하지 않은 부작용을 방지하기 위해 자동 형식 변환이 사용되지 않습니다.|
|[operator void *](#op_void_star)|스트림 상태가 여전히 양호한지 여부를 나타냅니다.|
|[연산자!](#op_not)|스트림 상태가 불량이 아닌지 여부를 나타냅니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<ios>

**네임스페이스:** std

## <a name="basic_iosbad"></a><a name="bad"></a> basic_ios:: 잘못 됨

스트림 버퍼의 무결성 손실을 나타냅니다.

```cpp
bool bad() const;
```

### <a name="return-value"></a>반환 값

**`true`**`rdstate & badbit`가 0이 아니면이 고, 그렇지 않으면 **`false`** 입니다.

`badbit`에 대한 자세한 내용은 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)를 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a> basic_ios:: basic_ios

basic_ios 클래스를 생성합니다.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>매개 변수

*sb*\
입력 또는 출력 요소를 저장할 표준 버퍼입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 [init](#init)(_ *Sb*)를 호출하여 멤버 개체를 초기화합니다. 보호된 두 번째 생성자는 멤버 개체를 초기화하지 않은 채 유지합니다. 를 나중에 호출 하는 경우 `init` 개체를 안전 하 게 제거할 수 있으려면 먼저 개체를 초기화 해야 합니다.

## <a name="basic_ioschar_type"></a><a name="char_type"></a> basic_ios:: char_type

템플릿 매개 변수 `Elem`의 동의어.

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a> basic_ios:: clear

오류 플래그를 모두 지웁니다.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>매개 변수

*상태일*\
필드 모든 플래그를 지운 후에 설정할 플래그입니다. 기본값은 `goodbit`입니다.

*reraise*\
필드 예외를 다시 발생시킬지 여부를 지정 합니다. 는로 기본 설정 **`false`** 됩니다 (예외를 다시 발생 시 키 지 않음).

### <a name="remarks"></a>설명

플래그는 `goodbit` ,, `failbit` `eofbit` 및 `badbit` 입니다. [good](#good), [bad](#bad), [eof](#eof) 및 [fail](#fail)을 사용하여 이러한 플래그를 테스트합니다.

멤버 함수는 저장된 스트림 상태 정보를 다음 코드로 바꿉니다.

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

`state` **&** [예외가](#exceptions) 0이 아니면 클래스 [오류](../standard-library/ios-base-class.md#failure)개체를 throw 합니다.

### <a name="example"></a>예제

을 사용 하는 예제는 [rdstate](#rdstate) 및 [getline](../standard-library/string-functions.md#getline) 을 참조 하세요 `clear` .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a> basic_ios:: copyfmt

스트림 간에 플래그를 복사합니다.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
플래그를 복사하려는 스트림입니다.

### <a name="return-value"></a>반환 값

**`this`** 플래그를 복사해 넣을 스트림에 대 한 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 콜백 이벤트 **지우기 \_ 이벤트** 를 보고 합니다. 그런 다음 *오른쪽* 에서 채우기 문자, 타이 포인터 및 서식 지정 **\* 정보로 복사 합니다.** 예외 마스크를 변경 하기 전에 콜백 이벤트를 보고 합니다 `copyfmt_event` . 복사가 완료되고 **state &**[exceptions](#exceptions)가 0이 아니면, 함수는 실제로 [rdstate](#rdstate) 인수와 함께 [clear](#clear)를 호출합니다. **\* 이** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a> basic_ios:: eof

스트림의 끝에 도달했는지 여부를 나타냅니다.

```cpp
bool eof() const;
```

### <a name="return-value"></a>반환 값

**`true`** 스트림의 끝에 도달 하면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

**`true`** [Rdstate](#rdstate) 가 0이 아닌 경우 멤버 함수는를 반환 합니다 `& eofbit` . `eofbit`에 대한 자세한 내용은 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)를 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a> basic_ios:: 예외

스트림에서 발생하는 예외를 나타냅니다.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>매개 변수

*Newexcept*\
예외를 throw하려는 플래그입니다.

### <a name="return-value"></a>반환 값

현재 스트림에 대한 예외를 throw하도록 지정된 플래그입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장된 예외 마스크를 반환합니다. 두 번째 멤버 함수는 예외 마스크에 *_Except* 를 저장하고 전에 저장된 값을 반환합니다. 새 예외 마스크를 저장하면 [clear](#clear)( [rdstate](#rdstate) )와 같은 예외가 throw될 수 있습니다.

### <a name="example"></a>예제

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a> basic_ios:: fail

스트림에서 유효한 필드 추출 실패를 나타냅니다.

```cpp
bool fail() const;
```

### <a name="return-value"></a>반환 값

**`true`**[rdstate](#rdstate) 가 0이 아니면이 고 `& (badbit|failbit)` , 그렇지 않으면 **`false`** 입니다.

`failbit`에 대한 자세한 내용은 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)를 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a> basic_ios:: fill

텍스트가 스트림만큼 넓지 않을 경우 사용할 문자를 지정하거나 반환합니다.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>매개 변수

*문자가*\
채우기 문자로 사용할 문자입니다.

### <a name="return-value"></a>반환 값

현재 채우기 문자입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장된 채우기 문자를 반환합니다. 두 번째 멤버 함수는 *문자를 채우기 문자에 저장* 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a> basic_ios:: 양호

스트림 상태가 양호함을 나타냅니다.

```cpp
bool good() const;
```

### <a name="return-value"></a>반환 값

**`true`**[rdstate](#rdstate) `== goodbit` (상태 플래그를 설정 하지 않음) 이면이 고, 그렇지 않으면 **`false`** 입니다.

`goodbit`에 대한 자세한 내용은 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)를 참조하세요.

### <a name="example"></a>예제

`good`을 사용하는 예는 [basic_ios::bad](#bad)를 참조하세요.

## <a name="basic_iosimbue"></a><a name="imbue"></a> basic_ios:: imbue

로캘을 변경합니다.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>매개 변수

*Loc*\
로캘 문자열입니다.

### <a name="return-value"></a>반환 값

이전 로캘입니다.

### <a name="remarks"></a>설명

[rdbuf](#rdbuf)가 null 포인터가 아닌 경우 멤버 함수는

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)를 호출합니다.

어느 경우든 [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a> basic_ios:: init

basic_ios 생성자에 의해 호출됩니다.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>매개 변수

*_Sb*\
입력 또는 출력 요소를 저장할 표준 버퍼입니다.

*_Isstd*\
표준 스트림인지 여부를 지정합니다.

### <a name="remarks"></a>설명

멤버 함수는 모든 멤버 개체에 값을 저장하므로:

- [rdbuf](#rdbuf)는 *_Sb* 를 반환합니다.

- [tie](#tie)는 null 포인터를 반환합니다.

- *_Sb* 0이 아니면 [rdstate](#rdstate) 는 [goodbit](../standard-library/ios-base-class.md#iostate) 을 반환 합니다. 그렇지 않으면 [badbit](../standard-library/ios-base-class.md#iostate)를 반환 합니다.

- [예외](#exceptions) 는 `goodbit` 를 반환 합니다.

- [flags](../standard-library/ios-base-class.md#flags)는 [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags)를 반환합니다.

- [width](../standard-library/ios-base-class.md#width)는 0을 반환합니다.

- [precision](../standard-library/ios-base-class.md#precision)은 6을 반환합니다.

- [fill](#fill)은 공백 문자를 반환합니다.

- [getloc](../standard-library/ios-base-class.md#getloc)는 `locale::classic`을 반환합니다.

- [iword](../standard-library/ios-base-class.md#iword)는 0을 반환하고, [pword](../standard-library/ios-base-class.md#pword)는 모든 인수 값에 대해 null 포인터를 반환합니다.

## <a name="basic_iosint_type"></a><a name="int_type"></a> basic_ios:: int_type

`traits_type::int_type`의 동의어입니다.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a> basic_ios:: move

스트림 버퍼에 대한 포인터를 제외하고 매개 변수의 모든 값을 현재 개체로 이동합니다.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
값을 이동할 `ios_base` 개체입니다.

### <a name="remarks"></a>설명

Protected 멤버 함수 *는 오른쪽에* 있는 저장 된를 제외 하 고에 저장 된 모든 값을 오른쪽으로 이동 하 여 **`*this`** `stream buffer pointer` 의 null 포인터로 설정 합니다  **`*this`** . 저장 된 `tie pointer` 가 *오른쪽* 의 null 포인터로 설정 된 경우

## <a name="basic_iosnarrow"></a><a name="narrow"></a> basic_ios:: 좁게

지정된 `char_type`에 해당하는 char를 찾습니다.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>매개 변수

*문자가*\
**`char`** 변환할입니다.

*기본*\
**`char`** 해당 항목이 없는 경우 반환 하려는입니다.

### <a name="return-value"></a>반환 값

지정 된에 해당 하는 **`char`** `char_type` 입니다.

### <a name="remarks"></a>설명

멤버 함수는 [use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype\<E> > ( [getloc](../standard-library/ios-base-class.md#getloc)())를 반환 합니다. `narrow` ( `Char`, `Default`).

### <a name="example"></a>예제

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a> basic_ios:: off_type

`traits_type::off_type`의 동의어입니다.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a> basic_ios:: operator void *

스트림 상태가 여전히 양호한지 여부를 나타냅니다.

```cpp
operator void *() const;
```

### <a name="return-value"></a>반환 값

연산자는 [fail](#fail)인 경우에만 null 포인터를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a> basic_ios:: operator!

스트림 상태가 불량이 아닌지 여부를 나타냅니다.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>반환 값

[fail](#fail)을 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a> basic_ios:: operator bool

개체를로 사용할 수 있습니다 `basic_ios` **`bool`** . 일반적이고 의도하지 않은 부작용을 방지하기 위해 자동 형식 변환이 사용되지 않습니다.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>설명

연산자는 인 경우에만로 변환할 수 있는 값을 반환 합니다 **`false`** `fail()` . 반환 형식은로만 변환할 수 있고 **`bool`** , `void *` 또는 기타 알려진 스칼라 형식으로 변환할 수 없습니다.

## <a name="basic_iospos_type"></a><a name="pos_type"></a> basic_ios::p os_type

`traits_type::pos_type`의 동의어입니다.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a> basic_ios:: rdbuf

스트림을 지정된 버퍼로 라우트합니다.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>매개 변수

*_Sb*\
스트림입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장된 스트림 버퍼 포인터를 반환합니다.

두 번째 멤버 함수는 저장 된 스트림 버퍼 포인터에 *_Sb* 를 저장 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a> basic_ios:: rdstate

플래그에 대한 비트 상태를 읽습니다.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>반환 값

저장된 스트림 상태 정보입니다.

### <a name="example"></a>예제

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a> basic_ios:: setstate

추가 플래그를 설정합니다.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>매개 변수

*_State*\
설정할 추가 플래그입니다.

### <a name="remarks"></a>설명

멤버 함수는 실제로 [clear](#clear)(_ *State* &#124; [rdstate](#rdstate))를 호출합니다.

### <a name="example"></a>예제

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a> basic_ios:: set_rdbuf

이 스트림 개체에 대한 읽기 버퍼로 사용할 스트림 버퍼를 할당합니다.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>매개 변수

*strbuf*\
읽기 버퍼가 될 스트림 버퍼입니다.

### <a name="remarks"></a>설명

Protected 멤버 함수는에 *strbuf* 를 저장 합니다 `stream buffer pointer` . 을 호출 하지 않습니다 `clear` .

## <a name="basic_iostie"></a><a name="tie"></a> basic_ios:: 동률

한 스트림이 다른 스트림보다 먼저 처리되도록 합니다.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>매개 변수

*문자열*\
스트림입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 저장된 연결(tie) 포인터를 반환합니다. 두 번째 멤버 함수는 동률 포인터에 *str* 를 저장 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="remarks"></a>설명

`tie`는 한 스트림의 작업이 완료된 후 다른 스트림의 작업이 발생하도록 두 스트림을 동기화합니다.

### <a name="example"></a>예제

이 예에서 cin을 cout과 연결하면 숫자 자체가 cin에서 추출되기 전에 "Enter a number:" 문자열이 콘솔로 이동합니다. 이렇게 하면 숫자를 읽을 때 "Enter a number:" 문자열이 아직 버퍼에 남아 있으므로, 실제로 응답해야 할 메시지가 사용자에게 표시되도록 할 수 있습니다. 기본적으로 cin과 cout은 연결됩니다.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a> basic_ios:: traits_type

템플릿 매개 변수 `Traits`의 동의어.

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a> basic_ios:: 넓히기

지정 된에 해당 하는을 찾습니다 `char_type` **`char`** .

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>매개 변수

*문자가*\
변환할 문자입니다.

### <a name="return-value"></a>반환 값

지정 된에 해당 하는을 찾습니다 `char_type` **`char`** .

### <a name="remarks"></a>설명

멤버 함수는 [use_facet](../standard-library/basic-filebuf-class.md#open) <  **ctype** \< **E**> > ( [getloc](../standard-library/ios-base-class.md#getloc))를 반환 합니다. `widen`( `Char`).

### <a name="example"></a>예제

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a> basic_ios:: swap

이 `basic_ios` 개체의 값을 다른 `basic_ios` 개체의 값으로 교환합니다. 그러나 스트림 버퍼에 대한 포인터는 교환되지 않습니다.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
값을 교환하는 데 사용되는 `basic_ios` 개체입니다.

### <a name="remarks"></a>설명

Protected 멤버 함수는 저장 된를 제외 하 고 *오른쪽* 에 저장 된 모든 값을 교환 **`*this`** `stream buffer pointer` 합니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
