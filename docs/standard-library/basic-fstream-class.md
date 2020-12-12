---
description: Basic_fstream 클래스에 대해 자세히 알아보세요.
title: basic_fstream 클래스
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: df8ad83696422737b5b368b39bf21c82506e8b65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321575"
---
# <a name="basic_fstream-class"></a>basic_fstream 클래스

[](../standard-library/basic-filebuf-class.md) <  `Elem` `Tr` `Elem` 문자 특성이 클래스에 의해 결정 되는 형식의 요소가 있는 클래스 basic_filebuf,>의 스트림 버퍼를 사용 하 여 요소 및 인코드된 개체의 삽입 및 추출을 제어 하는 개체에 대해 설명 합니다 `Tr` .

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

*E*\
파일 버퍼의 기본 요소입니다.

*비교한*\
파일 버퍼 기본 요소의 특성(일반적으로 `char_traits`< `Elem`>)입니다.

## <a name="remarks"></a>설명

이 개체는 `basic_filebuf`< `Elem`, `Tr`> 클래스의 개체를 저장합니다.

> [!NOTE]
> fstream 개체의 get 포인터 및 put 포인터는 서로 독립적이지 **않습니다**. get 포인터가 이동하면 put 포인터도 이동합니다.

## <a name="example"></a>예제

다음 예제에서는 읽고 쓸 수 있는 `basic_fstream` 개체를 만드는 방법을 보여 줍니다.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_fstream](#basic_fstream)|`basic_fstream` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[close](#close)|파일을 닫습니다.|
|[is_open](#is_open)|파일이 열려 있는지 확인합니다.|
|[열기](#open)|파일을 엽니다.|
|[rdbuf](#rdbuf)|> [basic_filebuf](../standard-library/basic-filebuf-class.md)에 대 한 형식 포인터의 저장 된 스트림 버퍼 주소를 반환 <  `Elem` `Tr` 합니다.|
|[스왑을](#swap)|이 개체의 콘텐츠를 다른 `basic_fstream` 개체의 콘텐츠로 교환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<fstream>

**네임스페이스:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a> basic_fstream:: basic_fstream

`basic_fstream` 형식의 개체를 생성합니다.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>매개 변수

*_Filename*\
열어야 할 파일의 이름입니다.

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode)의 열거형 중 하나입니다.

*_Prot*\
_Fsopen의 *shflag* 매개 변수에 해당 하는 기본 파일 열기 보호는 [_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>설명

첫 번째 생성자는 [basic_iostream](../standard-library/basic-iostream-class.md)()를 호출 하 여 기본 클래스를 초기화 합니다 `sb` `sb` . 여기서은 [basic_filebuf](../standard-library/basic-filebuf-class.md)클래스의 저장 된 개체입니다 \< **Elem**, **Tr**> . 또한 `sb` 를 호출 하 여를 초기화 `basic_filebuf` \< **Elem**, **Tr**> 합니다.

두 번째 및 세 번째 생성자는 `basic_iostream`( **sb**)를 호출하여 기본 클래스를 초기화합니다. 또한 `sb` `basic_filebuf` \< **Elem**, **Tr**> 를 호출한 다음 **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*,)을 호출 하 여를 초기화 `_Mode` 합니다. 후자 함수가 null 포인터를 반환 하면 생성자는 [setstate](../standard-library/basic-ios-class.md#setstate)()를 호출 `failbit` 합니다.

네 번째 생성자는 rvalue 참조로 처리되는 `right`의 내용으로 개체를 초기화합니다.

### <a name="example"></a>예제

`basic_fstream`을 사용하는 예는 [streampos](../standard-library/ios-typedefs.md#streampos)를 참조하세요.

## <a name="basic_fstreamclose"></a><a name="close"></a> basic_fstream:: close

파일을 닫습니다.

```cpp
void close();
```

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)를 호출 합니다.

### <a name="example"></a>예제

`close`를 사용하는 방법의 예는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="basic_fstreamis_open"></a><a name="is_open"></a> basic_fstream:: is_open

파일이 열려 있는지 확인합니다.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>반환 값

**`true`** 파일이 열려 있으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)반환 합니다.

### <a name="example"></a>예제

`is_open`을 사용하는 방법의 예는 [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)을 참조하세요.

## <a name="basic_fstreamopen"></a><a name="open"></a> basic_fstream:: open

파일을 엽니다.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>매개 변수

*_Filename*\
열어야 할 파일의 이름입니다.

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode)의 열거형 중 하나입니다.

*_Prot*\
_Fsopen의 *shflag* 매개 변수에 해당 하는 기본 파일 열기 보호는 [_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*,)을 호출 합니다 `_Mode` . 해당 함수가 null 포인터를 반환 하는 경우 함수는 [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit` )를 호출 합니다.

### <a name="example"></a>예제

을 사용 하는 방법에 대 한 예제는 [basic_filebuf:: open](../standard-library/basic-filebuf-class.md#open) 을 참조 하세요 `open` .

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a> basic_fstream:: operator =

지정된 스트림 개체의 내용을 이 개체에 할당합니다. 복사본을 남기지 않는 rvalue와 관련된 이동 할당입니다.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`basic_fstream` 개체에 대한 lvalue 참조입니다.

### <a name="return-value"></a>반환 값

**`*this`** 을 반환 합니다.

### <a name="remarks"></a>설명

멤버 연산자는 rvalue 참조로 처리 되는 *오른쪽* 의 내용을 사용 하 여 개체의 내용을 바꿉니다.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a> basic_fstream:: rdbuf

[Basic_filebuf](../standard-library/basic-filebuf-class.md)에 대 한 형식 포인터의 저장 된 스트림 버퍼 주소를 반환 \< **Elem**, **Tr**> 합니다.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>반환 값

저장된 스트림 버퍼의 주소입니다.

### <a name="example"></a>예제

`rdbuf`를 사용하는 방법의 예는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="basic_fstreamswap"></a><a name="swap"></a> basic_fstream:: swap

두 `basic_fstream` 개체의 내용을 교환합니다.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`basic_fstream` 개체에 대한 `lvalue` 참조입니다.

### <a name="remarks"></a>설명

멤버 함수는이 개체의 내용과 *오른쪽* 의 내용을 교환 합니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
