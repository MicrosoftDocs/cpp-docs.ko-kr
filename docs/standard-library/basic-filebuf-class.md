---
description: Basic_filebuf 클래스에 대해 자세히 알아보세요.
title: basic_filebuf 클래스
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: fedda394d2b10d07cda0580197f6763453455c4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335783"
---
# <a name="basic_filebuf-class"></a>basic_filebuf 클래스

외부 파일에 저장 된 요소의 시퀀스에서 문자 특성이 *Tr* 클래스에 의해 결정 되는 *Char_T* 형식 요소의 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>매개 변수

*Char_T*\
파일 버퍼의 기본 요소입니다.

*비교한*\
파일 버퍼의 기본 요소에 대 한 특성입니다 (일반적으로 `char_traits<Char_T>` ).

## <a name="remarks"></a>설명

클래스 템플릿은 외부 파일에 저장 된 요소의 시퀀스를 대상으로 하는 문자 특성이 *Tr* 클래스에 의해 결정 되는 *Char_T* 형식 요소의 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다.

> [!NOTE]
> 형식의 개체는 `basic_filebuf` __\*__ `char_type` *Char_T* 형식 매개 변수에 의해 지정 된와 관계 없이 char 형식의 내부 버퍼를 사용 하 여 만들어집니다. 즉, 유니코드 문자열 ( **`wchar_t`** 문자 포함)은 **`char`** 내부 버퍼에 기록 되기 전에 ANSI 문자열 (문자 포함)로 변환 됩니다. 유니코드 문자열을 버퍼에 저장 하려면 형식의 새 버퍼를 만들고 **`wchar_t`** 메서드를 사용 하 여 설정 [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` 합니다. 이 동작을 보여 주는 예제를 보려면 아래를 참조하세요.

클래스의 개체는 `basic_filebuf<Char_T, Tr>` `FILE` 열려 있는 파일과 연결 된 스트림을 제어 하는 개체를 지정 하는 파일 포인터를 저장 합니다. 또한 보호된 멤버 함수 [overflow](#overflow) 및 [underflow](#underflow)에서 사용하도록 두 가지 파일 변환 패싯에 대한 포인터를 저장합니다. 자세한 내용은 [`basic_filebuf::open`](#open)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `basic_filebuf<wchar_t>` 형식의 개체가 `pubsetbuf()` 메서드를 호출하여 유니코드 문자열을 내부 버퍼에 강제로 저장하도록 하는 방법을 보여 줍니다.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_filebuf](#basic_filebuf)|`basic_filebuf` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|형식 이름을 `Char_T` 템플릿 매개 변수와 연결합니다.|
|[int_type](#int_type)|`Tr` 범위에 있는 동일한 이름의 형식에 해당하는 `basic_filebuf`의 범위 내에 이 형식을 만듭니다.|
|[off_type](#off_type)|`Tr` 범위에 있는 동일한 이름의 형식에 해당하는 `basic_filebuf`의 범위 내에 이 형식을 만듭니다.|
|[pos_type](#pos_type)|`Tr` 범위에 있는 동일한 이름의 형식에 해당하는 `basic_filebuf`의 범위 내에 이 형식을 만듭니다.|
|[traits_type](#traits_type)|형식 이름을 `Tr` 템플릿 매개 변수와 연결합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[close](#close)|파일을 닫습니다.|
|[is_open](#is_open)|파일이 열려 있는지 여부를 나타냅니다.|
|[열기](#open)|파일을 엽니다.|
|[오버플로](#overflow)|가득 찬 버퍼에 새 문자를 삽입할 때 호출할 수 있는 보호된 가상 함수입니다.|
|[pbackfail](#pbackfail)|보호된 가상 멤버 함수는 요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 합니다.|
|[seekoff](#seekoff)|보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다.|
|[seekpos](#seekpos)|보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다.|
|[setbuf](#setbuf)|보호된 가상 멤버 함수는 파생된 각 스트림 버퍼와 관련된 작업을 수행합니다.|
|[스왑을](#swap)|이 `basic_filebuf`의 콘텐츠를 제공된 `basic_filebuf` 매개 변수의 콘텐츠로 교환합니다.|
|[동기화](#sync)|보호된 가상 함수는 제어된 스트림을 연결된 외부 스트림과 동기화하려고 합니다.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.|
|[언더플로가](#underflow)|입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<fstream>

**네임스페이스:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a> basic_filebuf:: basic_filebuf

`basic_filebuf` 형식의 개체를 생성합니다.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>설명

첫 번째 생성자는 입력 버퍼와 출력 버퍼를 제어하는 모든 포인터에 null 포인터를 저장합니다. 또한 파일 포인터에 null 포인터를 저장합니다.

두 번째 생성자는 rvalue 참조로 처리 되는 *오른쪽* 의 내용을 사용 하 여 개체를 초기화 합니다.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a> basic_filebuf:: char_type

형식 이름을 `Char_T` 템플릿 매개 변수와 연결합니다.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a> basic_filebuf:: close

파일을 닫습니다.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>반환 값

파일 포인터가 null 포인터인 경우 멤버 함수는 null 포인터를 반환합니다.

### <a name="remarks"></a>설명

`close`은 `fclose(fp)`를 호출합니다. 해당 함수가 0이 아닌 값을 반환하는 경우 이 함수는 null 포인터를 반환합니다. 그렇지 않으면 **`this`** 파일이 성공적으로 닫 혔 음을 나타내기 위해를 반환 합니다.

와이드 스트림의 경우 스트림을 연 이후 또는에 대 한 마지막 호출 이후에 삽입이 발생 한 경우 `streampos` 함수는를 호출 합니다 [`overflow`](#overflow) . 또한 필요에 따라 호출 하는 파일 변환 패싯을 사용 하 여 초기 변환 상태를 복원 하는 데 필요한 모든 시퀀스를 삽입 합니다 `fac` `fac.unshift` . 형식의 생성 된 각 요소 `byte` **`char`** 는 `fp` 폼의 후속 호출로 인해 파일 포인터로 지정 된 연결 된 스트림에 기록 됩니다 `fputc(byte, fp)` . 또는 쓰기에 대 한 호출이 `fac.unshift` 실패 하면 함수는 성공 하지 않습니다.

### <a name="example"></a>예제

다음 샘플에서는 현재 디렉터리의 두 파일을 가정 합니다. *basic_filebuf_close.txt* (내용: "테스트") 및 *iotest.txt* (내용: "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a> basic_filebuf:: int_type

범위 내에서이 형식을 범위 `basic_filebuf` 에 있는 동일한 이름의 형식과 동일 하 게 만듭니다 `Tr` .

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a> basic_filebuf:: is_open

파일이 열려 있는지 여부를 나타냅니다.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>반환 값

**`true`** 파일 포인터가 null이 아닌 경우입니다.

### <a name="example"></a>예제

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a> basic_filebuf:: off_type

범위 내에서이 형식을 범위 `basic_filebuf` 에 있는 동일한 이름의 형식과 동일 하 게 만듭니다 `Tr` .

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a> basic_filebuf:: open

파일을 엽니다.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>매개 변수

*이름도*\
열어야 할 파일의 이름입니다.

*모드가*\
의 열거형 중 하나입니다 [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode) .

*보호*\
_Fsopen의 *shflag* 매개 변수에 해당 하는 기본 파일 열기 보호는 [_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>반환 값

버퍼가 이미 열려 있는 경우 또는 파일 포인터가 null 포인터인 경우 함수는 null 포인터를 반환 합니다. 그렇지 않으면를 반환 **`this`** 합니다.

### <a name="remarks"></a>설명

이 함수는를 `FILE *` `basic_filebuf` 호출한 것 처럼를 사용 하 여를 반환 합니다 [`fopen/wfopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)` . `strmode`다음에서 결정 `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)` :

- `ios_base::in` 가 됩니다 `"r"` (읽기용으로 기존 파일 열기).
- [ios_base:: out](../standard-library/ios-base-class.md#fmtflags) 또는가 `ios_base::out | ios_base::trunc` 됩니다 `"w"` (기존 파일 자르기 또는 쓰기용으로 만들기).
- `ios_base::out | app``"a"`는 (모든 쓰기를 추가 하기 위해 기존 파일 열기)가 됩니다.
- `ios_base::in | ios_base::out``"r+"`는 (읽기 및 쓰기용으로 기존 파일 열기)가 됩니다.
- `ios_base::in | ios_base::out | ios_base::trunc` 가 됩니다 `"w+"` (기존 파일 자르기 또는 읽기 및 쓰기를 위해 만들기).
- `ios_base::in | ios_base::out | ios_base::app` 는 `"a+"` (읽고 모든 쓰기를 추가 하기 위해 기존 파일 열기)가 됩니다.

`mode & ios_base::binary`가 0이 아닌 경우 함수는에 추가 하 여 `b` `strmode` 텍스트 스트림 대신 이진 스트림을 엽니다.
`mode & ios_base::ate`가 0이 아니고 파일이 성공적으로 열리면 스트림의 현재 위치가 파일의 끝에 배치 됩니다. 실패 하면 파일이 닫힙니다.

위의 작업이 성공적으로 완료 되 면 `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)` [언더플로](#underflow) 및 [오버플로](#overflow)를 사용 하기 위해 파일 변환 패싯이 결정 됩니다.

파일을 열 수 없으면 null이 반환 됩니다.

### <a name="example"></a>예제

을 [`basic_filebuf::close`](#close) 사용 하는 예제는를 참조 하세요 `open` .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a> basic_filebuf:: operator =

이 스트림 버퍼 개체의 콘텐츠를 할당합니다. 복사본을 남기지 않는 rvalue와 관련 된 이동 할당입니다.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
[basic_filebuf](../standard-library/basic-filebuf-class.md) 개체에 대한 rvalue 참조입니다.

### <a name="return-value"></a>반환 값

__* This__ 를 반환 합니다.

### <a name="remarks"></a>설명

멤버 연산자는 rvalue 참조로 처리 되는 *오른쪽* 의 내용을 사용 하 여 개체의 내용을 바꿉니다. 자세한 내용은 [Rvalue 참조 선언 자:  &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조 하세요.

## <a name="basic_filebufoverflow"></a><a name="overflow"></a> basic_filebuf:: 오버플로

가득 찬 버퍼에 새 문자를 삽입할 때 호출됩니다.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>매개 변수

*_Meta*\
버퍼 또는에 삽입할 문자 `traits_type::eof` 입니다.

### <a name="return-value"></a>반환 값

함수가 성공할 수 없는 경우를 반환 `traits_type::eof` 합니다. 그렇지 않으면를 반환 `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)` 합니다.

### <a name="remarks"></a>설명

인 경우 `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 보호 된 가상 멤버 함수는 요소를 `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` 출력 버퍼에 삽입 하려고 합니다. 수행할 수 있는 방법은 다양합니다.

- 쓰기 위치를 사용할 수 있는 경우 요소를 쓰기 위칭에 저장하고 출력 버퍼에 대해 다음 포인터를 증분할 수 있습니다.

- 출력 버퍼에 대해 새 스토리지 또는 추가 스토리지를 할당하여 쓰기 위치를 사용 가능하게 만들 수 있습니다.

- 이 메서드 `ch` 는 필요에 따라 호출 하는 파일 변환 패싯을 사용 하 여 출력 버퍼에서 보류 중인 모든 출력을 변환 하 고 그 다음으로 변환할 수 있습니다 `fac` `fac.out` . Char 형식의 생성 된 각 요소 `ch` 는  `fp` 폼의 후속 호출로 인해 파일 포인터로 지정 된 연결 된 스트림에 기록 됩니다 `fputc(ch, fp)` . 변환 또는 쓰기가 실패하면 함수가 성공하지 못합니다.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a> basic_filebuf::p backfail

요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 합니다.

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>매개 변수

*_Meta*\
버퍼에 삽입할 문자 또는 `traits_type::eof`입니다.

### <a name="return-value"></a>반환 값

함수가 성공할 수 없는 경우를 반환 `traits_type::eof` 합니다. 그렇지 않으면를 반환 `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)` 합니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 요소를 입력 버퍼에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정합니다. 인 경우 `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 다시 푸시할 요소는 실제로 현재 요소 이전 스트림에 이미 있는 요소입니다. 그렇지 않으면 해당 요소는로 바뀝니다 `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` . 함수는 여러 가지 방법으로 요소를 다시 넣을 수 있습니다.

- 위치를 `putback` 사용할 수 있고 해당 위치에 저장 된 요소가와 비교 하는 경우 `ch` 입력 버퍼에 대 한 다음 포인터를 감소 시킬 수 있습니다.

- 함수에서 위치를 사용할 수 있는 경우 `putback` 이 작업을 수행할 수 있습니다. 이렇게 하려면 다음 포인터를 해당 위치를 가리키도록 설정 하 고 `ch` 해당 위치에 저장 합니다.

- 함수가 요소를 입력 스트림에 다시 푸시할 수 있는 경우 `ungetc` 형식의 요소에 대해를 호출 하는 등의 작업을 수행할 수 있습니다 **`char`** .

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a> basic_filebuf::p os_type

범위 내에서이 형식을 범위 `basic_filebuf` 에 있는 동일한 이름의 형식과 동일 하 게 만듭니다 `Tr` .

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a> basic_filebuf:: seekoff

제어된 스트림의 현재 위치를 변경하려고 합니다.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

*_Off*\
*_Way* 를 기준으로 검색할 위치입니다.

*_Way*\
오프셋 작업의 시작 지점입니다. 가능한 값은 [seekdir](../standard-library/ios-base-class.md#seekdir)을 참조하세요.

*_Which*\
포인터 위치에 대한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

새 위치 또는 잘못된 스트림 위치를 반환합니다.

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수는 제어 되는 스트림의 현재 위치를 변경 하려고 합니다. 클래스의 개체의 경우 [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>` 스트림 위치는 `fpos_t` 와이드 스트림의 구문을 분석 하는 데 필요한 모든 상태 정보 및 오프셋을 저장 하는 형식의 개체로 나타낼 수 있습니다. 오프셋 0은 스트림의 첫 번째 요소를 참조 합니다. 형식의 개체는 [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) 최소한 개체를 저장 `fpos_t` 합니다.

읽기 및 쓰기용으로 열린 파일의 경우 입력 스트림과 출력 스트림이 나란히 배치됩니다. 삽입 및 추출 사이를 전환 하려면 또는를 호출 해야 [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) 합니다 [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) . 및에 대 `pubseekoff` 한 호출에 `seekoff` 는 [텍스트 스트림](../c-runtime-library/text-and-binary-streams.md), [이진 스트림](../c-runtime-library/text-and-binary-streams.md)및 [와이드 스트림에](../c-runtime-library/byte-and-wide-streams.md)대 한 다양 한 제한이 있습니다.

파일 포인터가 `fp` null 포인터인 경우 함수가 실패 합니다. 그렇지 않으면를 호출 하 여 스트림 위치를 변경 하려고 `fseek(fp, _Off, _Way)` 합니다. 해당 함수가 성공 하 고 결과 위치를 `fposn` 호출 하 여 확인할 수 있는 경우 `fgetpos(fp, &fposn)` 함수가 성공 합니다. 함수가 성공 하면를 포함 하는 형식의 값을 반환 `pos_type` `fposn` 합니다. 실패하면 잘못된 스트림 위치를 반환합니다.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a> basic_filebuf:: seekpos

제어된 스트림의 현재 위치를 변경하려고 합니다.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

*_Sp*\
찾을 위치입니다.

*_Which*\
포인터 위치에 대한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

파일 포인터가 `fp` null 포인터인 경우 함수가 실패 합니다. 그렇지 않으면를 호출 하 여 스트림 위치를 변경 하려고 `fsetpos(fp, &fposn)` `fposn` 합니다. 여기서는 `fpos_t` 에 저장 된 개체입니다 `pos` . 성공하면 함수는 `pos`을 반환합니다. 실패하면 잘못된 스트림 위치를 반환합니다. 스트림 위치가 잘못되었는지를 확인하려면 반환 값을 `pos_type(off_type(-1))`과 비교합니다.

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수는 제어 되는 스트림의 현재 위치를 변경 하려고 합니다. 클래스의 개체의 경우 [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>` 스트림 위치는 `fpos_t` 와이드 스트림의 구문을 분석 하는 데 필요한 모든 상태 정보 및 오프셋을 저장 하는 형식의 개체로 나타낼 수 있습니다. 오프셋 0은 스트림의 첫 번째 요소를 참조 합니다. (`pos_type` 형식의 개체는 최소한 `fpos_t` 개체를 저장합니다.)

읽기 및 쓰기용으로 열린 파일의 경우 입력 스트림과 출력 스트림이 나란히 배치됩니다. 삽입 및 추출 사이를 전환 하려면 또는를 호출 해야 [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) 합니다 [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) . `pubseekoff`(및 `seekoff` )에 대 한 호출에는 텍스트 스트림, 이진 스트림 및 와이드 스트림에 대 한 다양 한 제한이 있습니다.

와이드 스트림의 경우 스트림이 열린 이후 또는 `streampos`에 대한 마지막 호출 이후 삽입이 발생하면 함수는 [overflow](#overflow)를 호출합니다. 또한 필요에 따라 호출 하는 파일 변환 패싯을 사용 하 여 초기 변환 상태를 복원 하는 데 필요한 모든 시퀀스를 삽입 합니다 `fac` `fac.unshift` . 형식의 생성 된 각 요소 `byte` **`char`** 는 `fp` 폼의 후속 호출로 인해 파일 포인터로 지정 된 연결 된 스트림에 기록 됩니다 `fputc(byte, fp)` . 또는 쓰기에 대 한 호출이 `fac.unshift` 실패 하면 함수는 성공 하지 않습니다.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a> basic_filebuf:: setbuf

파생된 각 스트림 버퍼와 관련된 작업을 수행합니다.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

*_Buffer*\
버퍼에 대한 포인터입니다.

*수*\
버퍼의 크기입니다.

### <a name="return-value"></a>반환 값

`fp` 파일 포인터가 null 포인터인 경우 보호된 멤버 함수는 0을 반환합니다.

### <a name="remarks"></a>설명

`setbuf``setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))`을 호출 하 여 `count` *_Buffer* 에서 시작 하는 요소의 배열을 스트림의 버퍼로 제공 합니다. 해당 함수가 0이 아닌 값을 반환하는 경우 이 함수는 null 포인터를 반환합니다. 그렇지 않으면를 반환 **`this`** 하 고 성공 신호를 반환 합니다.

## <a name="basic_filebufswap"></a><a name="swap"></a> basic_filebuf:: swap

이 `basic_filebuf`의 내용을 제공된 `basic_filebuf`의 내용으로 교환합니다.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
다른에 대 한 lvalue 참조 `basic_filebuf` 입니다.

## <a name="basic_filebufsync"></a><a name="sync"></a> basic_filebuf:: sync

제어된 스트림을 연결된 외부 스트림과 동기화하려고 합니다.

```cpp
virtual int sync();
```

### <a name="return-value"></a>반환 값

파일 포인터가 null 포인터인 경우 0을 반환 합니다 `fp` . 그렇지 않으면 [오버플로](#overflow) 를 모두 호출 하 고 `fflush(fp)` 보류 중인 모든 출력을 스트림으로 플러시하는 경우에만 0을 반환 합니다.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a> basic_filebuf:: traits_type

형식 이름을 `Tr` 템플릿 매개 변수와 연결합니다.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a> basic_filebuf:: 언더플로

입력 스트림에서 현재 요소를 추출합니다.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>반환 값

함수가 성공할 수 없는 경우를 반환 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 합니다. 그렇지 않으면 `ch` 설명 섹션에 설명 된 대로 변환 된을 반환 합니다.

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수는 입력 스트림에서 현재 요소를 추출 하 `ch` 고 요소를로 반환 하려고 시도 합니다 `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)` . 수행할 수 있는 방법은 다양합니다.

- 읽기 위치를 사용할 수 있는 경우 `ch` 읽기 위치에 저장 된 요소로를 사용 하 고 입력 버퍼에 대 한 다음 포인터를 앞으로 이동 합니다.

- 폼의 후속 호출에서와 같이 형식의 요소를 하나 이상 읽고 **`char`** `fgetc(fp)` `ch` `Char_T` 파일 변환 패싯을 사용 하 여 필요에 따라 호출 하는 형식의 요소로 변환할 수 있습니다 `fac` `fac.in` . 읽기 또는 변환이 실패하면 함수가 성공하지 못합니다.

## <a name="see-also"></a>참고 항목

[\<fstream>](../standard-library/fstream.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
