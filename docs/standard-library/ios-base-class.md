---
title: ios_base 클래스
description: Microsoft Visual C++ 표준 라이브러리 클래스에 대 한 API 참조 `ios_base`
ms.date: 10/23/2020
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: b425df2cf8d0c98c3558b377c29d013adf82d014
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907560"
---
# <a name="ios_base-class"></a>ios_base 클래스

이 클래스는 템플릿 매개 변수에 따라 달라지지 않는 입력 및 출력 스트림에 공통된 스토리지 및 멤버 함수를 설명합니다. (클래스 템플릿에서는 [`basic_ios`](../standard-library/basic-ios-class.md) 일반적 이며 템플릿 매개 변수에 따라 달라 지는 것을 설명 합니다.)

Ios_base 클래스의 개체는 다음 항목으로 구성되는 형식 지정 정보를 저장합니다.

- 형식의 개체에 있는 형식 플래그 [`fmtflags`](#fmtflags) 입니다.

- 형식의 개체에 있는 예외 마스크 [`iostate`](#iostate) 입니다.

- `int` 형식의 개체에 있는 필드 너비.

- `int` 형식의 개체에 있는 표시 자릿수.

- 형식의 개체에 있는 로캘 개체 `locale` 입니다.

- 형식의 요소와 포인터가 있는 두 개의 확장 가능한 배열 `long` `void`

클래스 ios_base의 개체는 스트림 상태 정보, 형식의 개체 [`iostate`](#iostate) 및 콜백 스택도 저장 합니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|Description|
|-|-|
|[`ios_base`](#ios_base)|`ios_base` 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|이름|Description|
|-|-|
|[`event_callback`](#event_callback)|에 전달 된 함수에 대해 설명 [`register_call`](#register_callback) 합니다.|
|[`fmtflags`](#fmtflags)|출력의 모양을 지정하는 상수입니다.|
|[`iostate`](#iostate)|스트림의 상태를 설명하는 상수를 정의합니다.|
|[`openmode`](#openmode)|스트림과 상호 작용하는 방법을 설명합니다.|
|[`seekdir`](#seekdir)|오프셋 작업에 대한 시작 지점을 지정합니다.|

### <a name="enums"></a>열거형

|이름|Description|
|-|-|
|[`event`](#event)|이벤트 유형을 지정합니다.|

### <a name="constants"></a>상수

|이름|Description|
|-|-|
|[`adjustfield`](#fmtflags)|로 정의 된 비트 마스크 `internal` \| `left` \| `right` 입니다.|
|[`app`](#openmode)|각 삽입 전에 스트림의 끝에 검색을 지정합니다.|
|[`ate`](#openmode)|해당 제어 개체를 처음 만들 때 스트림의 끝에 검색을 지정합니다.|
|[`badbit`](#iostate)|스트림 버퍼의 무결성 손실을 기록합니다.|
|[`basefield`](#fmtflags)|로 정의 된 비트 마스크 `dec` \| `hex` \| `oct` 입니다.|
|[`beg`](#seekdir)|시퀀스의 시작을 기준으로 한 검색을 지정합니다.|
|[`binary`](#openmode)|파일을 텍스트 스트림이 아니라 이진 스트림으로 읽도록 지정합니다.|
|[`boolalpha`](#fmtflags)|숫자 값이 아닌 이름(예: `true` 및 `false`)으로서 `bool` 형식의 개체를 삽입 또는 추출하도록 지정합니다.|
|[`cur`](#seekdir)|시퀀스 내에서 현재 위치를 기준으로 하는 검색을 지정합니다.|
|[`dec`](#fmtflags)|10진수 형식의 정수 값을 삽입 또는 추출하도록 지정합니다.|
|[`end`](#seekdir)|시퀀스의 끝을 기준으로 한 검색을 지정합니다.|
|[`eofbit`](#iostate)|스트림에서 추출할 때 파일 끝을 기록합니다.|
|[`failbit`](#iostate)|스트림에서 유효한 필드를 추출하지 못하는 경우를 기록합니다.|
|[`fixed`](#fmtflags)|고정 소수점 형식(지수 필드 없음)의 부동 소수점 값을 삽입하도록 지정합니다.|
|[`floatfield`](#fmtflags)|로 정의된 비트 마스크`fixed` \| `scientific`|
|[`goodbit`](#iostate)|모든 상태 비트를 지웁니다.|
|[`hex`](#fmtflags)|16진수 형식의 정수 값을 삽입 또는 추출하도록 지정합니다.|
|[`in`](#openmode)|스트림에서 추출하도록 지정합니다.|
|[`internal`](#fmtflags)|생성된 숫자 필드의 내부에 있는 점에서 채우기 문자를 삽입하여 필드 너비를 채웁니다.|
|[`left`](#fmtflags)|왼쪽 맞춤을 지정합니다.|
|[`oct`](#fmtflags)|8진수 형식의 정수 값을 삽입 또는 추출하도록 지정합니다.|
|[`out`](#openmode)|스트림에 삽입하도록 지정합니다.|
|[`right`](#fmtflags)|오른쪽 맞춤을 지정합니다.|
|[`scientific`](#fmtflags)|공학용 형식(지수 필드 사용)의 부동 소수점 값을 삽입하도록 지정합니다.|
|[`showbase`](#fmtflags)|생성된 정수 필드의 기수를 표시하는 접두사를 삽입하도록 지정합니다.|
|[`showpoint`](#fmtflags)|생성된 부동 소수점 필드에서 소수점을 무조건 삽입하도록 지정합니다.|
|[`showpos`](#fmtflags)|생성된 음수가 아닌 숫자 필드에 더하기 기호를 삽입하도록 지정합니다.|
|[`skipws`](#fmtflags)|특정 추출 전에 선행 공백은 건너뛰도록 지정합니다.|
|[`trunc`](#openmode)|해당 제어 개체가 만들어지면 기존 파일의 콘텐츠를 삭제하도록 지정합니다.|
|[`unitbuf`](#fmtflags)|각 삽입 후 출력이 플러시되도록 합니다.|
|[`uppercase`](#fmtflags)|특정 삽입의 소문자에 해당하는 대문자를 삽입하도록 지정합니다.|

### <a name="functions"></a>Functions

|이름|Description|
|-|-|
|[`failure`](#failure)|멤버 클래스는 클래스 템플릿 [basic_ios](../standard-library/basic-ios-class.md)에서 멤버 함수 [clear](../standard-library/basic-ios-class.md#clear) 에 의해 throw 되는 모든 예외에 대 한 기본 클래스로 사용 됩니다.|
|[`flags`](#flags)|현재 플래그 설정을 설정하거나 반환합니다.|
|[`getloc`](#getloc)|저장된 로캘 개체를 반환합니다.|
|[`imbue`](#imbue)|로캘을 변경합니다.|
|[`Init`](#init)|`iostream`생성 될 때 표준 개체를 만듭니다.|
|[`iword`](#iword)|`iword`로 저장할 수 있는 값을 할당합니다.|
|[`precision`](#precision)|부동 소수점 숫자에 표시할 자릿수를 지정합니다.|
|[`pword`](#pword)|`pword`로 저장할 수 있는 값을 할당합니다.|
|[`register_callback`](#register_callback)|콜백 함수를 지정합니다.|
|[`setf`](#setf)|지정된 플래그를 설정합니다.|
|[`sync_with_stdio`](#sync_with_stdio)|`iostream`및 C 런타임 라이브러리 작업이 소스 코드에 표시 되는 순서 대로 발생 하는지 확인 합니다.|
|[`unsetf`](#unsetf)|지정된 플래그가 해제되도록 합니다.|
|[`width`](#width)|출력 스트림의 길이를 설정합니다.|
|[`xalloc`](#xalloc)|변수가 스트림에 포함된다고 지정합니다.|

### <a name="operators"></a>연산자

|이름|Description|
|-|-|
|[`operator=`](#op_eq)|`ios_base` 개체에 사용할 대입 연산자입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<ios>

**네임스페이스:** std

## <a name="event"></a><a name="event"></a> `event`

이벤트 유형을 지정합니다.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>설명

형식은에 등록 된 함수에 대 한 인수로 사용 되는 콜백 이벤트를 저장할 수 있는 개체를 설명 하는 열거형 형식입니다 [`register_callback`](#register_callback) . 고유 이벤트 값은 다음과 같습니다.

- `copyfmt_event`-호출의 끝 부분에서 발생 하는 콜백을 식별 하기 위해 [`copyfmt`](../standard-library/basic-ios-class.md#copyfmt) [예외 마스크](../standard-library/ios-base-class.md) 를 복사 하기 직전입니다.

- `erase_event`,에 대 한 호출이 시작 될 때 [`copyfmt`](../standard-library/basic-ios-class.md#copyfmt) 또는에 대 한 소멸자 호출이 시작 될 때 발생 하는 콜백을 식별 `*this` 합니다.

- `imbue_event`는 [`imbue`](#imbue) 함수를 반환 하기 바로 전에 호출의 끝에서 발생 하는 콜백을 식별 합니다.

### <a name="example"></a>예제

[`register_callback`](#register_callback)예는를 참조 하십시오.

## <a name="event_callback"></a><a name="event_callback"></a> `event_callback`

에 전달 된 함수에 대해 설명 [`register_call`](#register_callback) 합니다.

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>매개 변수

*`_E`*\
[`event`](#event)입니다.

*`_Base`*\
이벤트가 호출된 스트림입니다.

*`_I`*\
사용자 정의 숫자입니다.

### <a name="remarks"></a>설명

형식은에 등록할 수 있는 함수에 대 한 포인터를 설명 합니다 [`register_callback`](#register_callback) . 이러한 형식의 함수는 예외를 throw하면 안 됩니다.

### <a name="example"></a>예제

을 [`register_call`](#register_callback) 사용 하는 예제는를 참조 하세요 `event_callback` .

## <a name="failure"></a><a name="failure"></a> `failure`

`failure` 클래스는 예외로 throw된 모든 개체의 형식에 대한 기본 클래스를 `iostreams` 라이브러리의 함수별로 정의하여 스트림 버퍼 작업 중 검색된 오류를 보고합니다.

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>설명

`what()`에서 반환된 값은 `_Message`의 복사본이며, `_Code`에 기반한 테스트로 확대될 수 있습니다. `_Code`를 지정하지 않은 경우 `make_error_code(io_errc::stream)`가 기본값입니다.

### <a name="example"></a>예제

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a><a name="flags"></a> `flags`

현재 플래그 설정을 설정하거나 반환합니다.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>매개 변수

*`fmtfl`*\
새 `fmtflags` 설정입니다.

### <a name="return-value"></a>반환 값

이전 또는 현재 `fmtflags` 설정입니다.

### <a name="remarks"></a>설명

[`ios_base::fmtflags`](#fmtflags)플래그 목록은를 참조 하십시오.

첫 번째 멤버 함수는 저장된 형식 플래그를 반환합니다. 두 번째 멤버 함수는 *`fmtfl`* 형식 플래그에를 저장 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="example"></a>예제

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a><a name="fmtflags"></a> `fmtflags`

출력의 모양을 지정하는 상수입니다.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>설명

에서 조작자를 지원 [`ios`](../standard-library/ios.md) 합니다.

형식은 서식 플래그를 저장할 수 있는 개체를 설명하는 비트 마스크 형식입니다. 고유 플래그 값(요소)은 다음과 같습니다.

- `dec` - 10진수 형식의 정수 값을 삽입 또는 추출합니다.

- `hex` - 16진수 형식의 정수 값을 삽입 또는 추출합니다.

- `oct` - 18진수 형식의 정수 값을 삽입 또는 추출합니다.

- `showbase` - 생성된 정수 필드의 기수를 표시하는 접두사를 삽입합니다.

- `internal` - 생성된 숫자 필드의 내부에 있는 점에서 채우기 문자를 삽입하여 필요에 따라 필드 너비를 채웁니다. 필드 너비 설정에 대 한 자세한 내용은을 참조 하십시오 [`setw`](../standard-library/iomanip-functions.md#setw) .

- `left` - 생성된 필드(왼쪽 맞춤)의 끝 부분에서 채우기 문자를 삽입하여 필요에 따라 필드 너비를 채웁니다.

- `right` - 생성된 필드(오른쪽 맞춤)의 시작 부분에서 채우기 문자를 삽입하여 필요에 따라 필드 너비를 채웁니다.

- `boolalpha` - 숫자 값이 아닌 이름(예: `true` 및 `false`)으로서 `bool` 형식의 개체를 삽입 또는 추출합니다.

- `fixed` - 고정 소수점 형식(지수 필드 없음)의 부동 소수점 값을 삽입합니다.

- `scientific` - 공학용 형식(지수 필드 사용)의 부동 소수점 값을 삽입합니다.

- `showpoint` - 생성된 부동 소수점 필드에서 소수점을 무조건 삽입합니다.

- `showpos` - 생성된 음수가 아닌 숫자 필드에 더하기 기호를 삽입합니다.

- `skipws` - 특정 추출 전에 선행 공백을 건너뜁니다.

- `unitbuf` - 각 삽입 후 출력을 플러시합니다.

- `uppercase` - 특정 삽입의 소문자에 해당하는 대문자를 삽입합니다.

또한 다음 몇 개의 값이 유용합니다.

- `adjustfield` - 로 정의된 비트 마스크`internal` \| `left` \| `right`

- `basefield` - 로 정의됩니다.`dec` \| `hex` \| `oct`

- `floatfield` - 로 정의됩니다.`fixed` \| `scientific`

이러한 형식 플래그를 수정 하는 함수의 예는를 참조 하십시오 [`<iomanip>`](../standard-library/iomanip.md) .

## <a name="getloc"></a><a name="getloc"></a> `getloc`

저장된 로캘 개체를 반환합니다.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>반환 값

저장된 로캘 개체입니다.

### <a name="example"></a>예제

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a><a name="imbue"></a> `imbue`

로캘을 변경합니다.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>매개 변수

*`_Loc`*\
새 로캘 설정입니다.

### <a name="return-value"></a>반환 값

이전 로캘입니다.

### <a name="remarks"></a>설명

멤버 함수는 *`_Loc`* 로캘 개체에를 저장 한 다음 콜백 이벤트 및를 보고 합니다 `imbue_event` . 이전에 저장된 값을 반환합니다.

### <a name="example"></a>예제

[`basic_ios::imbue`](../standard-library/basic-ios-class.md#imbue)샘플은를 참조 하세요.

## <a name="init"></a><a name="init"></a> `Init`

`iostream`생성 될 때 표준 개체를 만듭니다.

```cpp
class Init { };
```

### <a name="remarks"></a>설명

중첩 된 클래스는 `iostream` 임의 정적 개체에 대 한 생성자를 실행 하기 전에도 생성으로 표준 개체가 올바르게 생성 되도록 하는 개체를 설명 합니다.

## <a name="ios_base"></a><a name="ios_base"></a> `ios_base`

ios_base 개체를 생성합니다.

```cpp
ios_base();
```

### <a name="remarks"></a>설명

(보호된) 생성자는 아무 작업도 수행하지 않습니다. Init를 나중에 호출 하는 경우 `basic_ios::` [init](../standard-library/basic-ios-class.md#init) 개체를 초기화 해야 안전 하 게 제거할 수 있습니다. 따라서 클래스 ios_base에 대 한 안전 사용은 클래스 템플릿 [basic_ios](../standard-library/basic-ios-class.md)의 기본 클래스로만 사용 됩니다.

## <a name="iostate"></a><a name="iostate"></a> `iostate`

스트림의 상태를 설명하는 상수의 형식입니다.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>설명

이 형식은 스트림 상태 정보를 저장할 수 있는 개체에 대해 설명하는 비트 마스크 형식입니다. 고유 플래그 값(요소)은 다음과 같습니다.

- `badbit` - 스트림 버퍼의 무결성 손실을 기록합니다.
- `eofbit` - 스트림에서 추출할 때 파일 끝을 기록합니다.
- `failbit` - 스트림에서 유효한 필드를 추출하지 못하는 경우를 기록합니다.

또한 `goodbit` 앞에서 언급 한 비트가 설정 되지 않은 ( `goodbit` 0으로 보장 됨)에도 유용한 값이 있습니다.

## <a name="iword"></a><a name="iword"></a> `iword`

`iword`로 저장할 수 있는 값을 할당합니다.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>매개 변수

*`idx`*\
`iword`로 저장할 값의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 형식의 요소를 사용 하 여 확장 가능한 배열의 요소 *idx* 에 대 한 참조를 반환 합니다 `long` . 모든 요소는 효과적으로 존재하며 처음에는 0 값을 저장합니다. 반환 된 참조는 개체 `iword` 에 대 한 다음 호출 후에는에 대 한 호출을 통해 개체가 변경 된 후 `basic_ios::` [`copyfmt`](../standard-library/basic-ios-class.md#copyfmt) 또는 개체가 제거 된 후에는 유효 하지 않습니다.

*`idx`* 이 음수 이거나 요소에 대해 고유한 저장소를 사용할 수 없는 경우 함수는 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 고유 하지 않을 수 있는 참조를 호출 하 고 반환 합니다.

형식의 모든 개체에서 사용할 고유 인덱스를 가져오려면를 `ios_base` 호출 [`xalloc`](#xalloc) 합니다.

### <a name="example"></a>예제

을 [`xalloc`](#xalloc) 사용 하는 방법에 대 한 샘플은를 참조 하세요 `iword` .

## <a name="openmode"></a><a name="openmode"></a> `openmode`

스트림과 상호 작용하는 방법을 설명합니다.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type openmode;
   static const openmode  in;
   static const openmode  out;
   static const openmode  ate;
   static const openmode  app;
   static const openmode  trunc;
   static const openmode  binary;
   // ...
};
```

### <a name="remarks"></a>설명

여러 개체의 열기 모드 `iostream` 입니다. 플래그 값은 다음과 같습니다.

| 상수 | 효과  |
|---------|---------|
| `app` | 각 쓰기 전에 스트림의 끝을 검색 합니다. |
| `ate`  | 열린 직후 스트림의 끝을 검색 합니다. |
| `binary`| 이진 모드에서 엽니다. 이진 모드에 대 한 설명은를 참조 하십시오 [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) .|
| `in` |   읽기용으로 열기 |
| `out` | 쓰기용으로 열기 |
| `trunc` | 열린 후 파일의 내용을 삭제 합니다. |

### <a name="example"></a>예제

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

ios_base 개체에 대한 대입 연산자입니다.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>매개 변수

*`right`*\
`ios_base` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

할당 중인 개체입니다.

### <a name="remarks"></a>설명

연산자는 저장된 서식 정보를 복사하여 확장 가능한 배열의 새 복사본을 만듭니다. 그런 다음 `*this`를 반환합니다. 콜백 스택은 복사되지 않습니다.

이 연산자는 `ios_base`에서 파생된 클래스에서만 사용됩니다.

## <a name="precision"></a><a name="precision"></a> `precision`

부동 소수점 숫자에 표시할 자릿수를 지정합니다.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>매개 변수

*`_Prec`*\
표시할 유효 자릿수 또는 고정 표기법에서 소수점 뒤의 자릿수입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 저장된 [표시 자릿수](../standard-library/ios-base-class.md)를 반환합니다. 두 번째 멤버 함수는 *_Prec* 를 표시 전체 자릿수에 저장 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="remarks"></a>설명

부동 소수점 숫자는 [fixed](../standard-library/ios-functions.md#fixed)를 사용하여 고정 표기법으로 표시됩니다.

### <a name="example"></a>예제

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a><a name="pword"></a> `pword`

`pword`로 저장할 수 있는 값을 할당합니다.

```cpp
void *& pword(int index);
```

### <a name="parameters"></a>매개 변수

*`index`*\
`pword`로 저장할 값의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 포인터 형식의 요소를 사용 하 여 확장 가능한 배열의 요소 *인덱스* 에 대 한 참조를 반환 합니다 `void` . 모든 요소는 효과적으로 존재하며 처음에는 null 포인터를 저장합니다. 반환 된 참조는 개체 `pword` 에 대 한 다음 호출 후에는에 대 한 호출을 통해 개체가 변경 된 후 `basic_ios::` [`copyfmt`](../standard-library/basic-ios-class.md#copyfmt) 또는 개체가 제거 된 후에는 유효 하지 않습니다.

*Index* 가 음수 이거나 요소에 대해 고유한 저장소를 사용할 수 없는 경우 함수는 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 고유 하지 않을 수 있는 참조를 호출 하 고 반환 합니다.

형식의 모든 개체에서 사용할 고유 인덱스를 가져오려면를 `ios_base` 호출 [`xalloc`](#xalloc) 합니다.

### <a name="example"></a>예제

`pword` 사용 예제는 [`xalloc`](#xalloc)를 참조하세요.

## <a name="register_callback"></a><a name="register_callback"></a> `register_callback`

콜백 함수를 지정합니다.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>매개 변수

*`pfn`*\
콜백 함수에 대한 포인터입니다.

*`idx`*\
사용자 정의 숫자입니다.

### <a name="remarks"></a>설명

멤버 함수는 쌍을 `{pfn, idx}` 저장 된 콜백 스택 [콜백 스택으로](../standard-library/ios-base-class.md)푸시합니다. 콜백 이벤트 **ev** 를 보고 하면 함수는 레지스트리의 역순으로 식에 의해 호출 됩니다 `(*pfn)(ev, *this, idx)` .

### <a name="example"></a>예제

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a><a name="seekdir"></a> `seekdir`

오프셋 작업에 대한 시작 지점을 지정합니다.

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>설명

형식은 여러 클래스의 멤버 함수에 대 한 인수로 사용 되는 검색 모드를 저장할 수 있는 개체를 설명 하는 열거형 형식입니다 `iostream` . 고유 플래그 값은 다음과 같습니다.

- `beg`-시퀀스의 시작 (배열, 스트림 또는 파일)을 기준으로 검색 (현재 읽기 또는 쓰기 위치 변경) 합니다.

- `cur`-시퀀스 내에서 현재 위치를 기준으로 검색 합니다.

- `end`-시퀀스의 끝을 기준으로 검색 합니다.

### <a name="example"></a>예제

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a><a name="setf"></a> `setf`

지정된 플래그를 설정합니다.

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>매개 변수

*`_Mask`*\
설정할 플래그입니다.

*`_Unset`*\
해제할 플래그입니다.

### <a name="return-value"></a>반환 값

이전 형식 플래그입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [`flags(_Mask | _Flags)`](#flags) (선택한 비트 설정)를 효과적으로 호출한 다음 이전 형식 플래그를 반환 합니다. 두 번째 멤버 함수는를 효과적으로 호출한 `flags(_Mask & fmtfl, flags & ~_Mask)` 다음, 마스크에서 선택한 비트를 바꾸고, 이전 형식 플래그를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a><a name="sync_with_stdio"></a> `sync_with_stdio`

`iostream`및 C 런타임 라이브러리 작업이 소스 코드에 표시 되는 순서 대로 발생 하는지 확인 합니다.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>매개 변수

*`_Sync`*\
모든 스트림이와 동기화 되어 있는지 여부를 나타냅니다 `stdio` .

### <a name="return-value"></a>반환 값

이 함수에 대 한 이전 설정입니다.

### <a name="remarks"></a>설명

정적 멤버 함수는 `stdio` 동기화 플래그를 초기에 저장 `true` 합니다. `true`인 경우이 플래그는 동일한 파일에 대 [`iostreams`](../standard-library/iostreams-conventions.md) 한 작업이 함수 및 c + + 표준 라이브러리에 정의 된 함수 간에 적절 하 게 동기화 되도록 합니다. 그렇지 않으면 동기화가 보장 될 수도 있고 그렇지 않을 수도 있지만 성능이 향상 될 수도 있습니다. 함수는 *_Sync* 를 `stdio` 동기화 플래그에 저장 하 고 이전에 저장 된 값을 반환 합니다. 표준 스트림에 대 한 작업을 수행 하기 전에만이를 안전 하 게 호출할 수 있습니다.

## <a name="unsetf"></a><a name="unsetf"></a> `unsetf`

지정 된 플래그를 해제 합니다.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>매개 변수

*`_Mask`*\
해제 하려는 플래그입니다.

### <a name="remarks"></a>설명

멤버 함수는를 효과적으로 호출 합니다 [`flags(~_Mask & flags)`](#flags) (선택한 비트 지우기).

### <a name="example"></a>예제

[`ios_base::setf`](#setf)사용에 대 한 샘플은를 참조 하세요 `unsetf` .

## <a name="width"></a><a name="width"></a> `width`

출력 스트림의 길이를 설정합니다.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>매개 변수

*`_Wide`*\
출력 스트림의 원하는 크기입니다.

### <a name="return-value"></a>반환 값

현재 너비 설정입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장 된 필드 너비를 반환 합니다. 두 번째 멤버 함수는 *`_Wide`* 필드 너비에를 저장 하 고 이전에 저장 된 값을 반환 합니다.

### <a name="example"></a>예제

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a><a name="xalloc"></a> `xalloc`

변수가 스트림의 일부가 되도록 지정 합니다.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>반환 값

정적 멤버 함수는 각 호출에서 증가 하는 저장 된 정적 값을 반환 합니다.

### <a name="remarks"></a>설명

멤버 함수 또는를 호출할 때 반환 값을 고유 인덱스 인수로 사용할 수 있습니다 [`iword`](#iword) [`pword`](#pword) .

### <a name="example"></a>예제

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
