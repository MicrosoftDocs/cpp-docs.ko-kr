---
description: '다음에 대 한 자세한 정보: strstreambuf 클래스'
title: strstreambuf 클래스
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: 7eaed8a540fc4d9e53f7c6c5b8bbb69b3a7c4653
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183505"
---
# <a name="strstreambuf-class"></a>strstreambuf 클래스

배열 개체에 저장 된 요소의 시퀀스에서의 요소 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다 **`char`** .

## <a name="syntax"></a>구문

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>설명

개체 생성 방법에 따라 시퀀스의 변경 내용을 수용하도록 필요에 따라 개체를 할당, 확장 및 해제할 수 있습니다.

`strstreambuf` 클래스의 개체는 모드 정보의 여러 비트를 해당 `strstreambuf` 모드로 저장합니다. 이러한 비트는 제어되는 시퀀스가 다음과 같은지 여부를 나타냅니다.

- 할당되었으며 결국 해제해야 하는지 여부

- 수정할 수 있는지 여부

- 스토리지를 다시 할당하여 확장 가능합니다.

- 고정되어 개체가 아닌 에이전시에서 해당 개체를 삭제하거나 해제(할당된 경우)하기 전에 고정 해제해야 하는지 여부

고정된 제어되는 시퀀스는 이러한 별도 모드 비트의 상태에 관계없이 수정하거나 확장할 수 없습니다.

개체는 `strstreambuf` 할당을 제어하는 두 함수에 대한 포인터를 저장합니다. null 포인터인 경우 개체가 제어되는 시퀀스에 대한 스토리지를 할당 및 해제하는 고유한 메서드를 만듭니다.

> [!NOTE]
> 이 클래스는 사용되지 않습니다. 대신 [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) 또는 [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)를 사용하는 것이 좋습니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[strstreambuf](#strstreambuf)|`strstreambuf` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[고정](#freeze)|스트림 버퍼 작업을 통해 스트림 버퍼를 사용할 수 없게 합니다.|
|[오버플로](#overflow)|가득 찬 버퍼에 새 문자를 삽입할 때 호출할 수 있는 보호된 가상 함수입니다.|
|[pbackfail](#pbackfail)|요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 하는 보호된 가상 멤버 함수입니다.|
|[pcount](#pcount)|제어되는 시퀀스에 기록되는 요소 수의 개수를 반환합니다.|
|[seekoff](#seekoff)|제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.|
|[seekpos](#seekpos)|제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.|
|[str](#str)|[freeze](#freeze)를 호출한 다음 제어되는 시퀀스의 시작 부분에 대한 포인터를 반환합니다.|
|[언더플로가](#underflow)|입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<strstream>

**네임스페이스:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a> strstreambuf:: freeze

스트림 버퍼 작업을 통해 스트림 버퍼를 사용할 수 없게 합니다.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>매개 변수

*_Freezeit*\
**`bool`** 스트림을 고정 시킬 것인지 여부를 나타내는입니다.

### <a name="remarks"></a>설명

*_Freezeit* true 이면 함수는 저장 된 모드를 변경 `strstreambuf` 하 여 제어 되는 시퀀스가 고정 되도록 합니다. 그렇지 않은 경우에는 제어되는 시퀀스를 고정하지 않습니다.

[str](#str)은 `freeze`를 의미합니다.

> [!NOTE]
> 고정된 버퍼는 `strstreambuf` 소멸 중에 해제되지 않습니다. 메모리 누수를 방지하려면 버퍼를 해제하기 전에 고정을 취소해야 합니다.

### <a name="example"></a>예제

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="strstreambufoverflow"></a><a name="overflow"></a> strstreambuf:: 오버플로

가득 찬 버퍼에 새 문자를 삽입할 때 호출할 수 있는 보호된 가상 함수입니다.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>매개 변수

*_Meta*\
버퍼에 삽입할 문자 또는 `EOF`입니다.

### <a name="return-value"></a>반환 값

함수는 정상적으로 실행되지 않으면 `EOF`를 반환합니다. 그렇지 않으면 *\_ Meta* 인 경우  ==  `EOF` 이외의 값을 반환 `EOF` 합니다. 그렇지 않으면 *\_ Meta* 을 반환 합니다.

### <a name="remarks"></a>설명

*\_ Meta* ! = 인 경우 `EOF` 보호 된 가상 멤버 함수는 요소를 `(char)_Meta` 출력 버퍼에 삽입 하려고 합니다. 수행할 수 있는 방법은 다양합니다.

- 쓰기 위치를 사용할 수 있는 경우 요소를 쓰기 위칭에 저장하고 출력 버퍼에 대해 다음 포인터를 증분할 수 있습니다.

- 저장된 strstreambuf 모드에서 제어되는 시퀀스가 수정/확장 가능하며 고정되어 있지 않음을 나타내면 함수는 출력 버퍼에 대해 쓰기 위치를 새로 할당하여 사용 가능하도록 설정할 수 있습니다. 이러한 방식으로 출력 버퍼를 확장하면 연결된 입력 버퍼도 확장됩니다.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a> strstreambuf::p backfail

요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 하는 보호된 가상 구성원 함수입니다.

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>매개 변수

*_Meta*\
버퍼에 삽입할 문자 또는 `EOF`입니다.

### <a name="return-value"></a>반환 값

함수는 정상적으로 실행되지 않으면 `EOF`를 반환합니다. 그렇지 않으면 *\_ Meta* 인 경우  ==  `EOF` 이외의 값을 반환 `EOF` 합니다. 그렇지 않으면 *\_ Meta* 을 반환 합니다.

### <a name="remarks"></a>설명

보호된 가상 구성원 함수는 요소를 입력 버퍼에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 합니다.

*\_ Meta* 인 경우  ==  `EOF` 다시 푸시할 요소는 실제로 현재 요소 이전 스트림에 이미 있는 요소입니다. 그렇지 않으면 해당 요소는로 바뀝니다 `ch = (char)_Meta` . 함수는 여러 가지 방법으로 요소를 다시 넣을 수 있습니다.

- Putback 위치를 사용할 수 있고에 저장 된 요소가와 비교 되는 경우 `ch` 입력 버퍼에 대 한 다음 포인터를 감소 시킬 수 있습니다.

- Putback 위치를 사용할 수 있고 strstreambuf 모드에서 제어 되는 시퀀스를 수정할 수 있는 경우 함수는 `ch` putback 위치에 저장 하 고 입력 버퍼에 대 한 다음 포인터를 감소 시킬 수 있습니다.

## <a name="strstreambufpcount"></a><a name="pcount"></a> strstreambuf::p 수

제어되는 시퀀스에 기록되는 요소 수의 개수를 반환합니다.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>반환 값

제어되는 시퀀스에 기록되는 요소 수의 개수입니다.

### <a name="remarks"></a>설명

구체적으로 [pptr](../standard-library/basic-streambuf-class.md#pptr)이 null 포인터이면 함수는 0을 반환합니다. 그렇지 않으면 `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)를 반환 합니다.

### <a name="example"></a>예제

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="strstreambufseekoff"></a><a name="seekoff"></a> strstreambuf:: seekoff

제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.

```cpp
virtual streampos seekoff(streamoff _Off,
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

함수는 스트림 위치 중 하나 또는 두 위치를 모두 정상적으로 변경하면 결과 스트림 위치를 반환합니다. 그렇지 않으면 함수는 실패하며 잘못된 스트림 위치가 반환됩니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다. strstreambuf 클래스 개체의 경우 스트림 위치는 스트림 오프셋으로만 구성됩니다. 오프셋 0은 제어되는 시퀀스의 첫 번째 요소를 지정합니다.

새 위치는 다음과 같이 결정됩니다.

- 인 경우 `_Way == ios_base::beg` 새 위치는 스트림 시작 부분에 *_Off* 을 더한 값입니다.

- 인 경우 `_Way == ios_base::cur` 새 위치는 현재 스트림 위치에 *_Off* 을 더한 값입니다.

- 인 경우 `_Way == ios_base::end` 새 위치는 스트림의 끝에 *_Off* 을 더한 값입니다.

`_Which & ios_base::in`가 0이 아니고 입력 버퍼가 있으면 함수는 입력 버퍼에서 읽을 다음 위치를 변경 합니다. `_Which & ios_base::out`도이 0이 아니고 `_Way != ios_base::cur` 출력 버퍼가 있는 경우이 함수는 읽을 다음 위치와 일치 하도록 쓸 다음 위치를 설정 합니다.

그렇지 않고 `_Which & ios_base::out`이 0이 아니며 출력 버퍼가 있으면 함수는 출력 버퍼에서 쓸 다음 위치를 변경합니다. 그렇지 않은 경우 위치 지정 작업이 실패합니다. 위치 지정 작업을 정상적으로 수행하려면 결과 스트림 위치가 제어되는 시퀀스 내에 있어야 합니다.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a> strstreambuf:: seekpos

제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

*_Sp*\
찾을 위치입니다.

*_Which*\
포인터 위치에 대한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

함수는 스트림 위치 중 하나 또는 두 위치를 모두 정상적으로 변경하면 결과 스트림 위치를 반환합니다. 그렇지 않으면 함수는 실패하며 잘못된 스트림 위치가 반환됩니다. 스트림 위치가 잘못되었는지를 확인하려면 반환 값을 `pos_type(off_type(-1))`과 비교합니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다. strstreambuf 클래스 개체의 경우 스트림 위치는 스트림 오프셋으로만 구성됩니다. 오프셋 0은 제어되는 시퀀스의 첫 번째 요소를 지정합니다. 새 위치는 *_Sp* 에 의해 결정 됩니다.

`_Which` & **ios_base::in** 이 0이 아니고 입력 버퍼가 있으면 함수는 입력 버퍼에서 읽을 다음 위치를 변경합니다. `_Which` & `ios_base::out`이 0이 아니고 출력 버퍼가 있는 경우 함수는 읽을 다음 위치와 일치하도록 쓸 다음 위치도 설정합니다. 그렇지 않고 `_Which` & `ios_base::out`이 0이 아니며 출력 버퍼가 있으면 함수는 출력 버퍼에서 쓸 다음 위치를 변경합니다. 그렇지 않은 경우 위치 지정 작업이 실패합니다. 위치 지정 작업을 정상적으로 수행하려면 결과 스트림 위치가 제어되는 시퀀스 내에 있어야 합니다.

## <a name="strstreambufstr"></a><a name="str"></a> strstreambuf:: str

[freeze](#freeze)를 호출한 다음 제어되는 시퀀스의 시작 부분에 대한 포인터를 반환합니다.

```cpp
char *str();
```

### <a name="return-value"></a>반환 값

제어되는 시퀀스의 시작 부분에 대한 포인터입니다.

### <a name="remarks"></a>설명

종료 null 요소는 명시적으로 삽입한 경우가 아니면 없습니다.

### <a name="example"></a>예제

**str** 을 사용하는 샘플은 [strstreambuf::freeze](#freeze)를 참조하세요.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a> strstreambuf:: strstreambuf

`strstreambuf` 형식의 개체를 생성합니다.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* alloc_func)(size_t),
    void (* free_func)(void*));

strstreambuf(char* getptr,
    streamsize count,
    char* putptr = 0);

strstreambuf(signed char* getptr,
    streamsize count,
    signed char* putptr = 0);

strstreambuf(unsigned char* getptr,
    streamsize count,
    unsigned char* putptr = 0);

strstreambuf(const char* getptr,
    streamsize count);

strstreambuf(const signed char* getptr,
    streamsize count);

strstreambuf(const unsigned char* getptr,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

*alloc_func*\
버퍼 메모리를 할당하는 데 사용되는 함수입니다.

*수*\
*Getptr* 에서 가리키는 버퍼의 길이를 결정 합니다. *Getptr* 이 인수 (첫 번째 생성자 형식)가 아닌 경우에는 버퍼에 대해 제안 된 할당 크기입니다.

*_Freefunc*\
버퍼 메모리를 확보하는 데 사용되는 함수입니다.

*getptr*\
입력에 사용되는 버퍼입니다.

*putptr*\
출력에 사용되는 버퍼입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 입력 버퍼, 출력 버퍼 및 strstreambuf 할당을 제어하는 모든 포인터에 null 포인터를 저장합니다. 이 생성자는 제어되는 시퀀스를 수정/확장할 수 있도록 저장된 strstreambuf 모드를 설정합니다. 또한 제안 된 초기 할당 크기로 *수* 를 허용 합니다.

두 번째 생성자는 첫 번째 생성자와 같이 동작 합니다. 단,이 경우에는를 호출 하 여 저장소를 할당 하기 위해 호출 하는 함수에 대 *free_func* 한 포인터로 *alloc_func* 를 저장 하 고,를 호출 하 여 해당 저장소를 해제할 수 있도록

아래에 3개 생성자의 코드가 나와 있습니다.

```cpp
strstreambuf(char *getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

는 *getptr* 에서 제어 되는 시퀀스를 보유 하는 데 사용 되는 배열 개체를 지정 한다는 점을 제외 하 고 첫 번째 처럼 동작 합니다. 따라서 null 포인터가 아니어야 합니다. 배열의 *N* 요소 수는 다음과 같이 결정 됩니다.

- (*Count* > 0) 이면 *N* 은 *count* 입니다.

- (*Count* = = 0) 인 경우 *N* 은 `strlen((const char *) getptr )` 입니다.

- (*Count* < 0) 이면 *N* 이 **INT_MAX** 됩니다.

*Putptr* 이 null 포인터인 경우 함수는 다음을 실행 하 여 입력 버퍼만 설정 합니다.

```cpp
setg(getptr,
    getptr,
    getptr + N);
```

그렇지 않으면 다음 코드를 실행하여 입력 버퍼와 출력 버퍼를 모두 설정합니다.

```cpp
setg(getptr,
    getptr,
    putptr);

setp(putptr,
    getptr + N);
```

이 경우 *putptr* 은 [ *getptr*, *getptr*  +  *N*] 간격 내에 있어야 합니다.

마지막으로, 아래 코드에 나와 있는 세 가지 생성자는

```cpp
strstreambuf(const char *getptr,
    streamsize count);

strstreambuf(const signed char *getptr,
    streamsize count);

strstreambuf(const unsigned char *getptr,
    streamsize count);
```

모두 다음 코드와 동일하게 동작합니다.

```cpp
streambuf((char *)getptr, count);
```

단, 저장된 모드로 인해 제어되는 시퀀스를 수정하거나 확장할 수는 없습니다.

## <a name="strstreambufunderflow"></a><a name="underflow"></a> strstreambuf:: 언더플로

입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>반환 값

함수는 정상적으로 실행되지 않으면 `EOF`를 반환합니다. 그렇지 않으면 위에서 설명한 대로 변환된 입력 스트림의 현재 요소를 반환합니다.

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수는 입력 버퍼에서 현재 요소를 추출한 `ch` 다음 현재 스트림 위치로 이동 하 고 요소를로 반환 시도한 `(int)(unsigned char)ch` 합니다. 한 가지 방법으로이 작업을 수행할 수 있습니다. 읽기 위치를 사용할 수 있는 경우 `ch` 읽기 위치에 저장 된 요소로를 사용 하 고 입력 버퍼의 다음 포인터로 이동 합니다.

## <a name="see-also"></a>참고 항목

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
