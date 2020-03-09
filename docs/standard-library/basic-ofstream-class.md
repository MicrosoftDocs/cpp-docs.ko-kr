---
title: basic_ofstream 클래스
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: a73803f25c4fb9e54703b8bca93e68fedb63074e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865871"
---
# <a name="basic_ofstream-class"></a>basic_ofstream 클래스

문자 특성이 클래스 [에 의해 결정되는 ](../standard-library/basic-filebuf-class.md) 형식의 요소가 있는 클래스 < basic_filebuf`Elem``Tr``Elem`, `Tr`>의 스트림 버퍼로의 요소 및 인코드된 개체 삽입을 제어하는 개체에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

*Elem*\
파일 버퍼의 기본 요소입니다.

*Tr*\
파일 버퍼 기본 요소의 특성(일반적으로 `char_traits`< `Elem`>)입니다.

## <a name="remarks"></a>설명

`basic_ofstream`의 **wchar_t** 특수화가 파일에 쓸 때, 파일이 텍스트 모드로 열려 있으면 MBCS 시퀀스를 작성 합니다. 내부 표현에서는 `wchar_t`자의 버퍼를 사용하게 됩니다.

이 개체는 `basic_filebuf`< `Elem`, `Tr`> 클래스의 개체를 저장합니다.

## <a name="example"></a>예제

다음 예제에서는 `basic_ofstream` 개체를 만들고 거기에 텍스트를 쓰는 방법을 보여 줍니다.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_ofstream](#basic_ofstream)|`basic_ofstream` 형식의 개체를 만듭니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[close](#close)|파일을 닫습니다.|
|[is_open](#is_open)|파일이 열려 있는지 확인합니다.|
|[열기](#open)|파일을 엽니다.|
|[rdbuf](#rdbuf)|저장된 스트림 버퍼 주소를 반환합니다.|
|[swap](#swap)|이 `basic_ofstream`의 내용을 제공된 `basic_ofstream`의 내용으로 교환합니다.|

### <a name="operators"></a>연산자

|연산자|Description|
|-|-|
|[operator=](#op_eq)|이 스트림 개체의 콘텐츠를 할당합니다. 복사본을 남기지 않는 `rvalue reference`와 관련된 이동 할당입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<fstream >

**네임스페이스:** std

## <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream

`basic_ofstream` 형식의 개체를 만듭니다.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>매개 변수

*_Filename*\
열어야 할 파일의 이름입니다.

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode)의 열거형 중 하나입니다.

*_Prot*\
`shflag`_fsopen, _wfsopen[의 ](../c-runtime-library/reference/fsopen-wfsopen.md) 매개 변수와 같은 기본 파일 열기 보호입니다.

*오른쪽*\
이 `basic_ofstream` 개체를 초기화하는 데 사용되는 `basic_ofstream` 개체에 대한 rvalue 참조입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 [basic_ostream](../standard-library/basic-ostream-class.md)(`sb`)를 호출 하 여 기본 클래스를 초기화 합니다. 여기서 `sb`는 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem``Tr`> 클래스의 저장 된 개체입니다. 또한 `sb``basic_filebuf`< , `Elem`>을 호출하여 `Tr`를 초기화합니다.

두 번째 및 세 번째 생성자는 `basic_ostream`( **sb**)를 호출하여 기본 클래스를 초기화합니다. 또한 `basic_filebuf`< `Elem``Tr`>를 호출한 다음 `sb`를 호출 하 여 `sb`를 초기화 합니다. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`)을 차례로 호출합니다. 후자 함수가 null 포인터를 반환 하면 생성자는 [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`)를 호출 합니다.

네 번째 생성자는 복사 함수입니다. 이 메서드는 rvalue 참조로 처리 되는 *오른쪽*의 내용을 사용 하 여 개체를 초기화 합니다.

### <a name="example"></a>예제

다음 예제에서는 `basic_ofstream` 개체를 만들고 거기에 텍스트를 쓰는 방법을 보여 줍니다.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="close"></a>  basic_ofstream::close

파일을 닫습니다.

```cpp
void close();
```

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)를 호출합니다.

### <a name="example"></a>예제

[의 사용 예제는 ](../standard-library/basic-filebuf-class.md#close)basic_filebuf::close`close`를 참조하세요.

## <a name="is_open"></a>  basic_ofstream::is_open

파일이 열려 있는지 여부를 나타냅니다.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Return Value

파일이 열린 경우 **true**, 아닌 경우 **false**입니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)를 반환 합니다.

### <a name="example"></a>예제

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="open"></a>  basic_ofstream::open

파일을 엽니다.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
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
`shflag`_fsopen, _wfsopen[의 ](../c-runtime-library/reference/fsopen-wfsopen.md) 매개 변수와 같은 기본 파일 열기 보호입니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`)을 호출 합니다. 해당 함수가 null 포인터를 반환 하는 경우 함수는 [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`)를 호출 합니다.

### <a name="example"></a>예제

`open`를 사용 하는 예제는 [basic_filebuf:: open](../standard-library/basic-filebuf-class.md#open) 을 참조 하세요.

## <a name="op_eq"></a>  basic_ofstream::operator=

이 스트림 개체의 콘텐츠를 할당합니다. 복사본을 남기지 않는 `rvalue reference`와 관련된 이동 할당입니다.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`basic_ofstream` 개체에 대한 rvalue 참조입니다.

### <a name="return-value"></a>Return Value

`*this`를 반환합니다.

### <a name="remarks"></a>설명

멤버 연산자는 rvalue 참조로 처리 되는 *오른쪽*의 내용을 사용 하 여 개체의 내용을 바꿉니다.

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

저장된 스트림 버퍼 주소를 반환합니다.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Return Value

저장된 스트림 버퍼 주소를 반환합니다.

### <a name="example"></a>예제

[의 사용 예제는 ](../standard-library/basic-filebuf-class.md#close)basic_filebuf::close`rdbuf`를 참조하세요.

## <a name="swap"></a>  basic_ofstream::swap

두 `basic_ofstream` 개체의 내용을 교환합니다.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
다른 `lvalue` 개체에 대한 `basic_ofstream` 참조입니다.

### <a name="remarks"></a>설명

멤버 함수는이 개체의 내용을 *오른쪽*의 내용으로 교환 합니다.

## <a name="see-also"></a>참고 항목

[basic_ostream 클래스](../standard-library/basic-ostream-class.md)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
