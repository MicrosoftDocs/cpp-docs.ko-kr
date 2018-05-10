---
title: basic_fstream 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00484c170ba3e42ceb9925861def9e7a4617e324
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="basicfstream-class"></a>basic_fstream 클래스

문자 특성이 `Tr` 클래스에 의해 결정되는 `Elem` 형식의 요소가 있는 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 클래스의 스트림 버퍼를 사용하여 요소 및 인코드된 개체의 삽입 및 추출을 제어하는 개체를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

`Elem` 파일 버퍼의 기본 요소입니다.

`Tr` 파일 버퍼 기본 요소의 특성 (일반적으로 `char_traits` <  `Elem`>).

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

|생성자|설명|
|-|-|
|[basic_fstream](#basic_fstream)|`basic_fstream` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[close](#close)|파일을 닫습니다.|
|[is_open](#is_open)|파일이 열려 있는지 확인합니다.|
|[open](#open)|파일을 엽니다.|
|[rdbuf](#rdbuf)|형식 포인터의 저장된 스트림 버퍼 주소를 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>에 반환합니다.|
|[swap](#swap)|이 개체의 콘텐츠를 다른 `basic_fstream` 개체의 콘텐츠로 교환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<fstream>

**네임스페이스:** std

## <a name="basic_fstream"></a>  basic_fstream::basic_fstream

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

`_Filename` 열려는 파일의 이름입니다.

`_Mode` 열거 중 하나 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode)합니다.

`_Prot` 기본 파일을 보호 하려면 해당를 여는 `shflag` 매개 변수에서 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)합니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**)를 호출하여 기본 클래스를 초기화합니다. 여기서 **sb**는 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**> 클래스의 저장된 개체입니다. 또한 `basic_filebuf`\< **Elem**, **Tr**>을 호출하여 **sb**를 초기화합니다.

두 번째 및 세 번째 생성자는 `basic_iostream`( **sb**)를 호출하여 기본 클래스를 초기화합니다. 또한 `basic_filebuf`\< **Elem**, **Tr**> 및 **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`)를 차례로 호출하여 **sb**를 초기화합니다. 후자 함수가 null 포인터를 반환하면 생성자는 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)를 호출합니다.

네 번째 생성자는 rvalue 참조로 처리되는 `right`의 내용으로 개체를 초기화합니다.

### <a name="example"></a>예제

`basic_fstream`을 사용하는 예는 [streampos](../standard-library/ios-typedefs.md#streampos)를 참조하세요.

## <a name="close"></a>  basic_fstream::close

파일을 닫습니다.

```cpp
void close();
```

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf)**->** [close](../standard-library/basic-filebuf-class.md#close)를 호출합니다.

### <a name="example"></a>예제

**close**를 사용하는 방법의 예는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="is_open"></a>  basic_fstream::is_open

파일이 열려 있는지 확인합니다.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>반환 값

파일이 열린 경우 **true**, 아닌 경우 **false**입니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open)을 반환합니다.

### <a name="example"></a>예제

`is_open`을 사용하는 방법의 예는 [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)을 참조하세요.

## <a name="open"></a>  basic_fstream::open

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

`_Filename` 열려는 파일의 이름입니다.

`_Mode` 열거 중 하나 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode)합니다.

`_Prot` 기본 파일을 보호 하려면 해당를 여는 `shflag` 매개 변수에서 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)합니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`)를 호출합니다. 해당 함수가 null 포인터를 반환하면 함수는 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)를 호출합니다.

### <a name="example"></a>예제

**open**을 사용하는 방법의 예는 [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open)을 참조하세요.

## <a name="op_eq"></a>  basic_fstream::operator=

지정된 스트림 개체의 내용을 이 개체에 할당합니다. 복사본을 남기지 않는 rvalue와 관련된 이동 할당입니다.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>매개 변수

`right` 에 대 한 lvalue 참조는 `basic_fstream` 개체입니다.

### <a name="return-value"></a>반환 값

`*this`를 반환합니다.

### <a name="remarks"></a>설명

멤버 연산자는 rvalue 참조로 처리되는 `right`의 내용을 사용하여 개체의 내용을 바꿉니다.

## <a name="rdbuf"></a>  basic_fstream::rdbuf

형식 포인터의 저장된 스트림 버퍼 주소를 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>에 반환합니다.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>반환 값

저장된 스트림 버퍼의 주소입니다.

### <a name="example"></a>예제

`rdbuf`를 사용하는 방법의 예는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="swap"></a>  basic_fstream::swap

두 `basic_fstream` 개체의 내용을 교환합니다.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>매개 변수

`right` `lvalue` 에 대 한 참조는 `basic_fstream` 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 이 개체의 내용과 `right`의 내용을 교환합니다.

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
