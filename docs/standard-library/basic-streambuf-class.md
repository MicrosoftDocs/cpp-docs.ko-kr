---
title: basic_streambuf 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
dev_langs:
- C++
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7453120d40efc05fd0dce919a7b85869710a9b18
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848913"
---
# <a name="basicstreambuf-class"></a>basic_streambuf 클래스

스트림의 특정 표현과 요소 간의 전송을 제어하는 스트림 버퍼 파생을 위한 추상 기본 클래스에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>매개 변수

`Elem` A [char_type](#char_type)합니다.

`Tr` 문자 [traits_type](#traits_type)합니다.

## <a name="remarks"></a>설명

템플릿 클래스는 스트림의 특정 표현과 요소 간의 전송을 제어하는 스트림 버퍼 파생을 위한 추상 기본 클래스에 대해 설명합니다. `basic_streambuf` 클래스의 개체는 문자 특성이 [char_traits](../standard-library/char-traits-struct.md)([traits_type](#traits_type)이라고도 함) 클래스에 의해 결정되는 `Tr`([char_type](#char_type)이라고도 함) 형식의 요소가 있는 스트림을 제어하는 데 도움이 됩니다.

모든 스트림 버퍼는 추출용(입력)과 삽입용(출력)의 독립적인 두 스트림을 개념적으로 제어합니다. 그러나 특정 표현의 경우 이러한 스트림 중 어느 하나 또는 모두를 액세스할 수 없도록 만들 수 있습니다. 일반적으로 두 스트림 간의 일부 관계는 유지합니다. 예를 들어 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> 개체의 출력 스트림에 삽입하는 내용은 나중에 해당 입력 스트림에서 추출하는 내용입니다. [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 개체의 한 스트림을 배치할 때 다른 스트림은 나란히 배치합니다.

템플릿 클래스 `basic_streambuf`에 대한 공용 인터페이스에서는 모든 스트림 버퍼에 공통되지만 특수화된 작업을 제공합니다. 보호된 인터페이스에서는 해당 작업을 수행하기 위해 스트림의 특정 표현에 필요한 작업을 제공합니다. 보호된 가상 멤버 함수를 사용하면 스트림의 특정 표현에 대한 파생된 스트림 버퍼의 동작을 사용자 지정할 수 있습니다. 이 라이브러리에 있는 파생된 각 스트림 버퍼는 보호된 가상 멤버 함수의 동작을 특수화하는 방법을 설명합니다. 이 항목에는 종종 아무것도 수행하지 않는 기본 클래스의 기본 동작이 설명되어있습니다.

나머지 보호된 멤버 함수는 스트림과의 버퍼 전송에 제공된 저장소에 복사하거나 이러한 저장소에서 복사하는 것을 제어합니다. 예를 들어 입력 버퍼의 특징은 다음과 같습니다.

- [eback](#eback) - 버퍼의 시작 부분에 대한 포인터입니다.

- [gptr](#gptr) - 읽을 다음 요소에 대한 포인터입니다.

- [egptr](#egptr) - 버퍼의 끝을 바로 지난 포인터입니다.

마찬가지로, 출력 버퍼의 특징은 다음과 같습니다.

- [pbase](#pbase) - 버퍼의 시작 부분에 대한 포인터입니다.

- [pptr](#pptr) - 쓸 다음 요소에 대한 포인터입니다.

- [epptr](#epptr) - 버퍼의 끝을 바로 지난 포인터입니다.

모든 버퍼에 대해 다음 프로토콜이 사용됩니다.

- 다음 포인터가 null이면 버퍼가 존재하지 않습니다. 그렇지 않은 경우 세 포인터는 모두 동일한 시퀀스를 가리킵니다. 포인터는 주문을 위해 안전하게 비교할 수 있습니다.

- 출력 버퍼의 경우, 다음 포인터가 끝 포인터보다 작게 비교되는 경우 다음 포인터로 지정되는 쓰기 위치에서 요소를 저장할 수 있습니다.

- 입력 버퍼의 경우, 다음 포인터가 끝 포인터보다 작게 비교되는 경우 다음 포인터로 지정되는 읽기 위치에서 요소를 읽을 수 있습니다.

- 입력 버퍼의 경우, 시작 포인터가 다음 포인터보다 작게 비교되는 경우 감소하는 다음 포인터로 지정되는 putback 위치에서 요소를 다시 넣을 수 있습니다.

`basic_streambuf`< `Elem`, `Tr`>에서 파생 클래스에 대해 작성하는 모든 보호된 가상 멤버 함수는 이 프로토콜을 유지하는 데 서로 협력해야 합니다.

`basic_streambuf`< `Elem`, `Tr`> 클래스의 개체는 앞에서 설명한 6개의 포인터를 저장합니다. 이 클래스는 파생된 스트림 버퍼가 사용할 것에 대비하여 [locale](../standard-library/locale-class.md) 형식의 개체에 로캘 개체를 저장합니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[basic_streambuf](#basic_streambuf)|`basic_streambuf` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|형식 이름을 `Elem` 템플릿 매개 변수와 연결합니다.|
|[int_type](#int_type)|`basic_streambuf` 범위 내의 형식 이름을 `Elem` 템플릿 매개 변수와 연결합니다.|
|[off_type](#off_type)|`basic_streambuf` 범위 내의 형식 이름을 `Elem` 템플릿 매개 변수와 연결합니다.|
|[pos_type](#pos_type)|`basic_streambuf` 범위 내의 형식 이름을 `Elem` 템플릿 매개 변수와 연결합니다.|
|[traits_type](#traits_type)|형식 이름을 `Tr` 템플릿 매개 변수와 연결합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[eback](#eback)|포인터를 입력 버퍼의 시작 부분에 반환하는 보호된 함수입니다.|
|[egptr](#egptr)|입력 버퍼의 끝 부분을 막 지나는 포인터를 반환하는 보호된 함수입니다.|
|[epptr](#epptr)|출력 버퍼의 끝 부분을 막 지나는 포인터를 반환하는 보호된 함수입니다.|
|[gbump](#gbump)|입력 버퍼에 대한 다음 포인터에 `count`를 추가하는 보호된 함수입니다.|
|[getloc](#getloc)|`basic_streambuf` 개체의 로캘을 가져옵니다.|
|[gptr](#gptr)|포인터를 입력 버퍼의 다음 요소에 반환하는 보호된 함수입니다.|
|[imbue](#imbue)|[pubimbue](#pubimbue)에 의해 호출되는 보호된 가상 함수입니다.|
|[in_avail](#in_avail)|버퍼에서 읽을 준비가 된 요소의 수를 반환합니다.|
|[overflow](#overflow)|가득 찬 버퍼에 새 문자를 삽입할 때 호출할 수 있는 보호된 가상 함수입니다.|
|[pbackfail](#pbackfail)|보호된 가상 멤버 함수는 요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 합니다.|
|[pbase](#pbase)|포인터를 출력 버퍼의 시작 부분에 반환하는 보호된 함수입니다.|
|[pbump](#pbump)|출력 버퍼에 대한 다음 포인터에 `count`를 추가하는 보호된 함수입니다.|
|[pptr](#pptr)|포인터를 출력 버퍼의 다음 요소에 반환하는 보호된 함수입니다.|
|[pubimbue](#pubimbue)|`basic_streambuf` 개체의 로캘을 설정합니다.|
|[pubseekoff](#pubseekoff)|파생 클래스에서 재정의되는 보호된 가상 함수인 [seekoff](#seekoff)를 호출합니다.|
|[pubseekpos](#pubseekpos)|파생 클래스에서 재정의되고, 현재 포인터 위치를 재설정하는 보호된 가상 함수인 [seekpos](#seekpos)를 호출합니다.|
|[pubsetbuf](#pubsetbuf)|파생 클래스에서 재정의되는 보호된 가상 함수인 [setbuf](#setbuf)를 호출합니다.|
|[pubsync](#pubsync)|파생 클래스에서 재정의되고, 이 버퍼와 연결된 외부 스트림을 업데이트하는 보호된 가상 함수인 [sync](#sync)를 호출합니다.|
|[sbumpc](#sbumpc)|스트림 포인터를 이동하여 현재 요소를 읽고 반환합니다.|
|[seekoff](#seekoff)|보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다.|
|[seekpos](#seekpos)|보호된 가상 멤버 함수는 제어된 스트림의 현재 위치를 변경하려고 합니다.|
|[setbuf](#setbuf)|보호된 가상 멤버 함수는 파생된 각 스트림 버퍼와 관련된 작업을 수행합니다.|
|[setg](#setg)|입력 버퍼에 대한 시작 포인터에서 `_Gbeg`, 다음 포인터에서 `_Gnext`, 끝 포인터에서 `_Gend`를 저장하는 보호된 함수입니다.|
|[setp](#setp)|출력 버퍼에 대한 시작 포인터에서 `_Pbeg`, 끝 포인터에서 `_Pend`를 저장하는 보호된 함수입니다.|
|[sgetc](#sgetc)|스트림에서 위치를 변경하지 않고 현재 요소를 반환합니다.|
|[sgetn](#sgetn)|읽힌 요소 수를 반환합니다.|
|[showmanyc](#showmanyc)|입력 스트림에서 추출할 수 있는 문자 수를 반환하고 프로그램이 무기한 대기하지 않도록 해주는 보호된 가상 멤버 함수입니다.|
|[snextc](#snextc)|현재 요소를 읽고 다음 요소를 반환합니다.|
|[sputbackc](#sputbackc)|스트림에 `char_type`을 넣습니다.|
|[sputc](#sputc)|스트림에 문자를 넣습니다.|
|[sputn](#sputn)|스트림에 문자열을 넣습니다.|
|[stossc](#stossc)|스트림에서 현재 요소를 지나 이동합니다.|
|[sungetc](#sungetc)|스트림에서 문자를 가져옵니다.|
|[swap](#swap)|이 개체에 있는 값을 제공된 `basic_streambuf` 개체 매개 변수에 있는 값으로 교환합니다.|
|[sync](#sync)|제어된 스트림을 연결된 외부 스트림과 동기화하려고 하는 보호된 가상 함수입니다.|
|[uflow](#uflow)|입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.|
|[underflow](#underflow)|입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.|
|[xsgetn](#xsgetn)|입력 스트림에서 요소를 추출하는 보호된 가상 함수입니다.|
|[xsputn](#xsputn)|요소를 출력 스트림에 삽입하는 보호된 가상 함수입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator=](#op_eq)|이 개체의 값을 다른 `basic_streambuf` 개체에서 할당합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<streambuf>

**네임스페이스:** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

`basic_streambuf` 형식의 개체를 생성합니다.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>매개 변수

`right` 에 대 한 lvalue 참조는 `basic_streambuf` 이 대 한 값을 설정 하는 데 사용 되는 개체 `basic_streambuf` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 보호된 생성자는 입력 버퍼와 출력 버퍼를 제어하는 모든 포인터에 null 포인터를 저장합니다. 또한 `locale::classic`을 로캘 개체에 저장합니다. 자세한 내용은 [locale:: classic](../standard-library/locale-class.md#classic)을 참조하세요.

두 번째 보호된 생성자는 `right`에서 포인터와 로캘을 복사합니다.

## <a name="char_type"></a>  basic_streambuf::char_type

형식 이름을 **Elem** 템플릿 매개 변수와 연결합니다.

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

포인터를 입력 버퍼의 시작 부분에 반환하는 보호된 함수입니다.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>반환 값

입력 버퍼의 시작 부분에 대한 포인터입니다.

## <a name="egptr"></a>  basic_streambuf::egptr

입력 버퍼의 끝 부분을 막 지나는 포인터를 반환하는 보호된 함수입니다.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>반환 값

입력 버퍼의 끝을 바로 지난 포인터입니다.

## <a name="epptr"></a>  basic_streambuf::epptr

출력 버퍼의 끝 부분을 막 지나는 포인터를 반환하는 보호된 함수입니다.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>반환 값

출력 버퍼의 끝을 바로 지난 포인터입니다.

## <a name="gbump"></a>  basic_streambuf::gbump

입력 버퍼에 대한 다음 포인터에 `count`를 추가하는 보호된 함수입니다.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>매개 변수

`count` 포인터를 이동 하는 기준인 양입니다.

## <a name="getloc"></a>  basic_streambuf::getloc

Basic_streambuf 개체의 로캘을 가져옵니다.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>반환 값

저장된 로캘 개체입니다.

### <a name="remarks"></a>설명

관련 내용은 [ios_base::getloc](../standard-library/ios-base-class.md#getloc)를 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a>  basic_streambuf::gptr

포인터를 입력 버퍼의 다음 요소에 반환하는 보호된 함수입니다.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>반환 값

입력 버퍼의 다음 요소에 대한 포인터입니다.

## <a name="imbue"></a>  basic_streambuf::imbue

[pubimbue](#pubimbue)에 의해 호출되는 보호된 가상 함수입니다.

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>매개 변수

`_Loc` 로캘의에 대 한 참조입니다.

### <a name="remarks"></a>설명

기본 동작은 아무것도 수행하지 않는 것입니다.

## <a name="in_avail"></a>  basic_streambuf::in_avail

버퍼에서 읽을 준비가 된 요소의 수를 반환합니다.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>반환 값

버퍼에서 읽을 준비가 된 요소의 수입니다.

### <a name="remarks"></a>설명

경우는 [읽기 위치](../standard-library/basic-streambuf-class.md) ´ 멤버 함수가 반환 [egptr](#egptr) - [gptr](#gptr)합니다. 아닌 경우 [showmanyc](#showmanyc)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a>  basic_streambuf::int_type

basic_streambuf 범위 내 형식 이름을 템플릿 매개 변수의 형식 중 하나와 연결합니다.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

basic_streambuf 범위 내 형식 이름을 템플릿 매개 변수의 형식 중 하나와 연결합니다.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator=

이 개체의 값을 다른 `basic_streambuf` 개체에서 할당합니다.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>매개 변수

`right` 에 대 한 lvalue 참조는 `basic_streambuf` 이 개체에 값을 할당 하는 데 사용 되는 개체입니다.

### <a name="remarks"></a>설명

보호된 멤버 연산자는 입력 버퍼와 출력 버퍼를 제어하는 포인터를 `right`에서 복사합니다. 또한 `right.`[getloc()](#getloc)를 `locale object`에 저장합니다. `*this`를 반환합니다.

## <a name="overflow"></a>  basic_streambuf::overflow

가득 찬 버퍼에 새 문자를 삽입할 때 호출할 수 있는 보호된 가상 함수입니다.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>매개 변수

`_Meta` 버퍼에 삽입 하는 문자 또는 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)합니다.

### <a name="return-value"></a>반환 값

함수가 성공할 수 없는 경우 **traits_type::eof**를 반환하거나 예외를 throw합니다. 아닌 경우 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)를 반환합니다. 기본 동작은 **traits_type::eof**를 반환하는 것입니다.

### <a name="remarks"></a>설명

_ *Meta*가 **traits_type::eof**와 비교하여 같지 않은 경우 보호되는 가상 멤버 함수는 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 요소를 출력 스트림에 삽입하려고 합니다. 수행할 수 있는 방법은 다양합니다.

- `write position`이 사용 가능한 경우 요소를 쓰기 위치에 저장하고 출력 버퍼에 대해 다음 포인터를 증가시킬 수 있습니다.

- 출력 버퍼에 대해 새 저장소 또는 추가 저장소를 할당하여 쓰기 위치를 사용 가능하게 만들 수 있습니다.

- 출력 버퍼의 시작 포인터와 다음 포인터 사이의 일부 또는 모든 요소를 외부 대상에 기록하여 쓰기 위치를 사용 가능하게 만들 수 있습니다.

가상 오버플로 함수는 [sync](#sync) 및 [underflow](#underflow) 함수와 함께 streambuf 파생 클래스의 특성을 정의합니다. 각 파생 클래스는 오버플로를 다르게 구현할 수 있지만, 호출하는 스트림 클래스와의 인터페이스는 동일합니다.

`overflow` 함수는 put 영역이 꽉 찼을 때 `sputc` 및 `sputn` 같은 공용 `streambuf` 함수에서 가장 자주 호출되지만 스트림 클래스를 비롯한 다른 클래스는 언제든지 `overflow`를 호출할 수 있습니다.

이 함수는 `pbase` 및 `pptr` 포인터 사이의 put 영역에 있는 문자를 사용하고 put 영역을 다시 초기화합니다. `overflow` 함수는 또한 `nCh`를 소비해야 하거나(`nCh`가 `EOF`가 아닐 경우), 다음 호출 시에 소비되도록 해당 문자를 새로운 put 영역에 둘 수 있습니다.

소비의 정의는 파생 클래스에 따라 다릅니다. 예를 들어, `filebuf` 클래스는 문자를 파일에 기록하는 반면, `strstreambuf` 클래스는 문자를 버퍼에 보관하고(버퍼가 동적으로 지정된 경우) 오버플로 호출에 대한 응답으로 버퍼를 확장합니다. 이 확장은 이전 버퍼를 해제하고 더 큰 새 버퍼로 대체하여 수행됩니다. 포인터는 필요에 따라 조정됩니다.

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

보호된 가상 멤버 함수는 요소를 입력 스트림에 다시 넣은 후 다음 포인터에서 가리키는 현재 요소로 설정하려고 합니다.

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>매개 변수

`_Meta` 버퍼에 삽입 하는 문자 또는 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)합니다.

### <a name="return-value"></a>반환 값

함수가 성공할 수 없는 경우 **traits_type::eof**를 반환하거나 예외를 throw합니다. 성공할 경우 다른 값을 반환합니다. 기본 동작은 **traits_type::eof**를 반환하는 것입니다.

### <a name="remarks"></a>설명

_ *Meta*가 **traits_type::eof**와 비교하여 같은 경우 다시 푸시할 요소는 실제로 현재 요소 이전 스트림에 이미 있는 요소입니다. 아닌 경우 해당 요소는 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*)로 바뀝니다. 함수는 여러 가지 방법으로 요소를 다시 넣을 수 있습니다.

- putback 위치가 사용 가능한 경우 요소를 putback 위치에 저장하고 입력 버퍼에 대해 다음 포인터를 증가시킬 수 있습니다.

- 입력 버퍼에 대해 새 저장소 또는 추가 저장소를 할당하여 putback 위치를 사용 가능하게 만들 수 있습니다.

- 공통된 입력 및 출력 스트림이 있는 스트림 버퍼의 경우, 출력 버퍼에 대한 시작 포인터와 다음 포인터 사이의 일부 또는 모든 요소를 외부 대상에 기록하여 putback 위치를 사용 가능하게 만들 수 있습니다.

## <a name="pbase"></a>  basic_streambuf::pbase

포인터를 출력 버퍼의 시작 부분에 반환하는 보호된 함수입니다.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>반환 값

출력 버퍼의 시작 부분에 대한 포인터입니다.

## <a name="pbump"></a>  basic_streambuf::pbump

출력 버퍼에 대한 다음 포인터에 `count`를 추가하는 보호된 함수입니다.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>매개 변수

`count` 쓰기 위치를 앞으로 이동 하는 기준인 문자 수를 지정 합니다.

## <a name="pos_type"></a>  basic_streambuf::pos_type

basic_streambuf 범위 내 형식 이름을 템플릿 매개 변수의 형식 중 하나와 연결합니다.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

포인터를 출력 버퍼의 다음 요소에 반환하는 보호된 함수입니다.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>반환 값

출력 버퍼의 다음 요소에 대한 포인터입니다.

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

basic_streambuf 개체의 로캘을 설정합니다.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>매개 변수

`_Loc` 로캘의에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

로캘 개체에 저장된 이전 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 로캘 개체에 _ *Loc*를 저장하고 [imbue](#imbue)를 호출합니다.

### <a name="example"></a>예제

`pubimbue`의 사용 예제는 [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)를 참조하세요.

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

파생 클래스에서 재정의되는 보호된 가상 함수인 [seekoff](#seekoff)를 호출합니다.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

`_Off` 기준으로 찾을 대 한 위치 `_Way`합니다.

`_Way` 오프셋된 작업에 대 한 시작 지점입니다. 가능한 값은 [seekdir](../standard-library/ios-base-class.md#seekdir)을 참조하세요.

`_Which` 포인터 위치에 대 한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

새 위치 또는 잘못된 스트림 위치 ( [seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`) )를 반환합니다.

### <a name="remarks"></a>설명

`_Way`를 기준으로 포인터를 이동합니다.

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

파생 클래스에서 재정의되고, 현재 포인터 위치를 재설정하는 보호된 가상 함수인 [seekpos](#seekpos)를 호출합니다.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

`_Sp` 에 대 한 검색 위치입니다.

`_Which` 포인터 위치에 대 한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

새 위치 또는 잘못된 스트림 위치입니다. 스트림 위치가 잘못되었는지를 확인하려면 반환 값을 `pos_type(off_type(-1))`과 비교합니다.

### <a name="remarks"></a>설명

멤버 함수는 [seekpos](#seekpos)(_ *Sp*, `_Which`)를 반환합니다.

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

파생 클래스에서 재정의되는 보호된 가상 함수인 [setbuf](#setbuf)를 호출합니다.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

`_Buffer` 에 대 한 포인터 `char_type` 이 인스턴스화에 대 한 합니다.

`count` 버퍼의 크기입니다.

### <a name="return-value"></a>반환 값

[setbuf](#setbuf)( `_Buffer`, `count`)를 반환합니다.

## <a name="pubsync"></a>  basic_streambuf::pubsync

파생 클래스에서 재정의되고, 이 버퍼와 연결된 외부 스트림을 업데이트하는 보호된 가상 함수인 [sync](#sync)를 호출합니다.

```cpp
int pubsync();
```

### <a name="return-value"></a>반환 값

반환 [동기화](#sync) 또는-1 이면 실패 합니다.

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

스트림 포인터를 이동하여 현재 요소를 읽고 반환합니다.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>반환 값

현재 요소입니다.

### <a name="remarks"></a>설명

읽기 위치가 사용 가능한 경우 멤버 함수는 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **\***[gptr](#gptr))을 반환하고 입력 버퍼에 대한 다음 포인터를 증가시킵니다. 아닌 경우 [uflow](#uflow)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Output

3

```

```Output

      33
51
```

## <a name="seekoff"></a>  basic_streambuf::seekoff

제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

`_Off` 기준으로 찾을 대 한 위치 `_Way`합니다.

`_Way` 오프셋된 작업에 대 한 시작 지점입니다. 가능한 값은 [seekdir](../standard-library/ios-base-class.md#seekdir)을 참조하세요.

`_Which` 포인터 위치에 대 한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

새 위치 또는 잘못된 스트림 위치 ( `seekoff` (_ *Off*, `_Way`, `_Which`) )를 반환합니다.

### <a name="remarks"></a>설명

새 위치는 다음과 같이 결정됩니다.

- `_Way` == `ios_base::beg`인 경우 새 위치는 스트림 시작 부분에 _ *Off*를 더한 위치입니다.

- `_Way` == `ios_base::cur`인 경우 새 위치는 현재 스트림 위치에 _ *Off*를 더한 위치입니다.

- `_Way` == `ios_base::end`인 경우 새 위치는 스트림 끝에 _ *Off*를 더한 위치입니다.

일반적으로 **which & ios_base::in**이 0이 아닌 경우 입력 스트림이 영향을 받고, **which & ios_base::out**이 0이 아닌 경우 출력 스트림이 영향을 받습니다. 그러나 이 매개 변수의 실제 사용은 파생 스트림 버퍼 간에 다릅니다.

하나 이상의 스트림 위치를 정상적으로 변경하는 경우 함수는 결과 스트림 위치 또는 결과 스트림 위치 중 하나를 반환합니다. 실패하면 잘못된 스트림 위치를 반환합니다. 기본 동작은 잘못된 스트림 위치를 반환하는 것입니다.

## <a name="seekpos"></a>  basic_streambuf::seekpos

제어되는 스트림의 현재 위치를 변경하려고 하는 보호된 가상 멤버 함수입니다.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

`_Sp` 에 대 한 검색 위치입니다.

`_Which` 포인터 위치에 대 한 모드를 지정합니다. 기본적으로는 읽기 및 쓰기 위치를 수정할 수 있습니다.

### <a name="return-value"></a>반환 값

새 위치 또는 잘못된 스트림 위치입니다. 스트림 위치가 잘못되었는지를 확인하려면 반환 값을 `pos_type(off_type(-1))`과 비교합니다.

### <a name="remarks"></a>설명

새 위치는 _ *Sp*입니다.

일반적으로 **which & ios_base::in**이 0이 아닌 경우 입력 스트림이 영향을 받고, **which & ios_base::out**이 0이 아닌 경우 출력 스트림이 영향을 받습니다. 그러나 이 매개 변수의 실제 사용은 파생 스트림 버퍼 간에 다릅니다.

하나 이상의 스트림 위치를 정상적으로 변경하는 경우 함수는 결과 스트림 위치 또는 결과 스트림 위치 중 하나를 반환합니다. 아닌 경우 잘못된 스트림 위치(-1)를 반환합니다. 기본 동작은 잘못된 스트림 위치를 반환하는 것입니다.

## <a name="setbuf"></a>  basic_streambuf::setbuf

파생된 각 스트림 버퍼와 관련된 작업을 수행하는 보호된 가상 멤버 함수입니다.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

`_Buffer` 버퍼에 대 한 포인터입니다.

`count` 버퍼의 크기입니다.

### <a name="return-value"></a>반환 값

기본 동작은 **this**를 반환하는 것입니다.

### <a name="remarks"></a>설명

[basic_filebuf](../standard-library/basic-filebuf-class.md)를 참조하세요. `setbuf`는 사용할 `streambuf` 개체에 대한 메모리 영역을 제공합니다. 버퍼가 사용되는 방법은 파생 클래스에서 정의됩니다.

## <a name="setg"></a>  basic_streambuf::setg

입력 버퍼에 대한 시작 포인터에 _ *Gbeg*, 다음 포인터에 `_Gnext`, 끝 포인터 `_Gend`를 저장하는 보호된 함수입니다.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>매개 변수

*_Gbeg* 버퍼의 시작 부분에 대 한 포인터입니다.

`_Gnext` 위치에 대 한 포인터 버퍼 중간에 있습니다.

`_Gend` 버퍼의 끝에 대 한 포인터입니다.

## <a name="setp"></a>  basic_streambuf::setp

출력 버퍼에 대한 시작 포인터에서 `_Pbeg`, 끝 포인터에서 `_Pend`를 저장하는 보호된 함수입니다.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>매개 변수

`_Pbeg` 버퍼의 시작 부분에 대 한 포인터입니다.

`_Pend` 버퍼의 끝에 대 한 포인터입니다.

## <a name="sgetc"></a>  basic_streambuf::sgetc

스트림에서 위치를 변경하지 않고 현재 요소를 반환합니다.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>반환 값

현재 요소입니다.

### <a name="remarks"></a>설명

읽기 위치가 사용 가능한 경우 멤버 함수는 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr))을 반환합니다. 아닌 경우 [underflow](#underflow)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a>  basic_streambuf::sgetn

입력 버퍼에서 최대 `count`개 문자를 추출하고 제공된 버퍼 `ptr`에 저장합니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

`ptr` 버퍼는 추출 된 문자를 포함할입니다.

`count` 읽을 수 있는 요소의 수입니다.

### <a name="return-value"></a>반환 값

읽은 요소의 수입니다. 자세한 내용은 [streamsize](../standard-library/ios-typedefs.md#streamsize)를 참조하세요.

### <a name="remarks"></a>설명

멤버 함수는 [xsgetn](#xsgetn)( `ptr`, `count`)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

입력 스트림에서 추출할 수 있는 문자 수를 반환하고 프로그램이 무기한 대기하지 않도록 해주는 보호된 가상 멤버 함수입니다.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>반환 값

기본 동작은 0을 반환하는 것입니다.

## <a name="snextc"></a>  basic_streambuf::snextc

현재 요소를 읽고 다음 요소를 반환합니다.

```cpp
int_type snextc();
```

### <a name="return-value"></a>반환 값

스트림에서 다음 요소입니다.

### <a name="remarks"></a>설명

멤버 함수는 [sbumpc](#sbumpc)를 반환합니다. 해당 함수가 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)를 반환하는 경우 **traits_type::eof**를 반환합니다. 아닌 경우 [sgetc](#sgetc)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Output

aa

```

```Output

aa97
```

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

스트림에 char_type을 넣습니다.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>매개 변수

`_Ch` 문자입니다.

### <a name="return-value"></a>반환 값

문자 또는 실패를 반환합니다.

### <a name="remarks"></a>설명

putback 위치가 사용 가능하고 `_Ch`가 그 위치에 저장된 문자와 같은 경우, 멤버 함수는 입력 버퍼에 대한 다음 포인터를 감소시키고 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`)를 반환합니다. 아닌 경우 [pbackfail](#pbackfail)( `_Ch`)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a>  basic_streambuf::sputc

스트림에 문자를 넣습니다.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>매개 변수

`_Ch` 문자입니다.

### <a name="return-value"></a>반환 값

성공할 경우 해당 문자를 반환합니다.

### <a name="remarks"></a>설명

`write position`이 사용 가능한 경우 멤버 함수는 쓰기 위치에 `_Ch`를 저장하고, 출력 버퍼에 대한 다음 포인터를 증가시키고, **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`)를 반환합니다. 아닌 경우 [overflow](#overflow)( `_Ch`)를 반환합니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a>  basic_streambuf::sputn

스트림에 문자열을 넣습니다.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>매개 변수

`ptr` 문자열입니다.

`count` 문자 수입니다.

### <a name="return-value"></a>반환 값

실제로 스트림에 삽입되는 문자의 수입니다.

### <a name="remarks"></a>설명

멤버 함수는 [xsputn](#xsputn)( `ptr`, `count`)를 반환합니다. 자세한 내용은 이 멤버의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a>  basic_streambuf::stossc

스트림에서 현재 요소를 지나 이동합니다.

```cpp
void stossc();
```

### <a name="remarks"></a>설명

멤버 함수는 [sbumpc](#sbumpc)를 호출합니다. 이 멤버 함수를 제공하는 데에는 구현이 필요하지 않습니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a>  basic_streambuf::sungetc

스트림에서 문자를 가져옵니다.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>반환 값

문자 또는 실패를 반환합니다.

### <a name="remarks"></a>설명

Putback 위치가 사용 가능한 경우 멤버 함수는 입력 버퍼에 대한 다음 포인터를 감소시키고 `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr](#gptr))을 반환합니다. 그러나 현재 버퍼의 상태에서 캡처될 수 있도록 마지막으로 읽은 문자를 확인하는 것이 항상 가능하지는 않습니다. 이것이 true인 경우 함수는 [pbackfail](#pbackfail)을 반환합니다. 이러한 상황을 방지하려면 다시 넣을 문자를 추적하고 `sputbackc(ch)`를 호출합니다. 스트림의 시작에서 호출하지 않거나 두 개 이상의 문자를 다시 넣으려고 시도하지 않는 한 실패하지 않습니다.

### <a name="example"></a>예제

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a>  basic_streambuf::swap

이 개체에 있는 값을 제공된 `basic_streambuf` 개체에 있는 값으로 교환합니다.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|`right`|값을 교환하는 데 사용되는 `basic_streambuf` 개체에 대한 lvalue 참조입니다.|

### <a name="remarks"></a>설명

보호된 멤버 함수는 `input buffer` 및 `output buffer`를 제어하는 모든 포인터를 `right`와 교환합니다. 또한 `right.`[getloc()](#getloc)을 `locale` 개체와 교환합니다.

## <a name="sync"></a>  basic_streambuf::sync

제어된 스트림을 연결된 외부 스트림과 동기화하려고 하는 보호된 가상 함수입니다.

```cpp
virtual int sync();
```

### <a name="return-value"></a>반환 값

성공하지 못하면 함수는 -1을 반환합니다. 기본 동작은 0을 반환하는 것입니다.

### <a name="remarks"></a>설명

`sync`에는 출력 버퍼에 대한 시작 포인터와 다음 포인터 사이의 모든 요소를 기록하는 것이 포함됩니다. 입력 버퍼에 대한 다음 포인터와 끝 포인터 사이의 모든 요소를 되돌려 놓는 것은 포함되지 않습니다.

## <a name="traits_type"></a>  basic_streambuf::traits_type

형식 이름을 **Tr** 템플릿 매개 변수와 연결합니다.

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>반환 값

현재 요소입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 입력 버퍼에서 현재 요소 **ch** 추출을 시도한 다음 현재 스트림 위치로 이동하여 요소를 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)로서 반환합니다. 수행할 수 있는 방법은 다양합니다.

- 읽기 위치를 사용할 수 있으면 함수는 읽기 위치에 저장된 요소로 **ch**를 가져온 후 입력 버퍼의 다음 포인터로 이동합니다.

- 일부 외부 소스에서 요소를 직접 읽고, **ch** 값으로서 전달할 수 있습니다.

- 공통된 입력 및 출력 스트림이 있는 스트림 버퍼의 경우, 출력 버퍼에 대한 시작 포인터와 다음 포인터 사이의 일부 또는 모든 요소를 외부 대상에 기록하여 읽기 위치를 사용 가능하게 만들 수 있습니다. 또는 입력 버퍼에 대해 새 저장소 또는 추가 저장소를 할당할 수 있습니다. 그런 다음 함수는 일부 외부 소스에서 하나 이상의 요소를 읽습니다.

성공하지 못할 경우 함수는 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)를 반환하거나 예외를 throw합니다. 성공할 경우, 위에서 설명한 대로 변환된 입력 스트림에서 현재 요소 `ch`를 반환하고 입력 버퍼의 다음 포인터로 이동합니다. 기본 동작은 [underflow](#underflow)를 호출하는 것입니다. 해당 함수가 **traits_type::eof**를 반환할 경우 **traits_type::eof**를 반환합니다. 아닌 경우, 위에서 설명한 대로 변환된 입력 스트림에서 현재 요소 **ch**를 반환하고 입력 버퍼의 다음 포인터로 이동합니다.

## <a name="underflow"></a>  basic_streambuf::underflow

입력 스트림에서 현재 요소를 추출하는 보호된 가상 함수입니다.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>반환 값

현재 요소입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 입력 스트림에서 현재 요소 **ch** 추출을 시도한 다음 현재 스트림 위치로 이동하여 요소를 `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)로서 반환합니다. 수행할 수 있는 방법은 다양합니다.

- 읽기 위치를 사용할 수 있는 경우 **ch**는 읽기 위치에 저장된 요소입니다. 이에 대한 자세한 내용은 [basic_streambuf 클래스](../standard-library/basic-streambuf-class.md)의 설명 섹션을 참조하세요.

- 입력 버퍼에 대해 새 저장소 또는 추가 저장소를 할당한 다음 일부 외부 소스에서 하나 이상의 요소를 읽음으로써 읽기 위치를 사용 가능하게 만들 수 있습니다. 이에 대한 자세한 내용은 [basic_streambuf 클래스](../standard-library/basic-streambuf-class.md)의 설명 섹션을 참조하세요.

성공하지 못할 경우 함수는 `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()`를 반환하거나 예외를 throw합니다. 성공할 경우 위에서 설명한 대로 변환된 입력 스트림의 현재 요소를 반환합니다. 기본 동작은 `traits_type::eof()`를 반환하는 것입니다.

가상 `underflow` 함수는 [sync](#sync) 및 [overflow](#overflow) 함수와 함께 `streambuf` 파생 클래스의 특성을 정의합니다. 각 파생 클래스는 `underflow`를 다르게 구현할 수 있지만, 호출하는 스트림 클래스와의 인터페이스는 동일합니다.

`underflow` 함수는 get 영역이 비었을 때 [sgetc](#sgetc) 및 [sgetn](#sgetn) 같은 공용 `streambuf` 함수에서 가장 자주 호출되지만 스트림 클래스를 비롯한 다른 클래스는 언제든지 `underflow`를 호출할 수 있습니다.

`underflow` 함수는 get 영역에 입력 소스의 문자를 제공합니다. get 영역에 문자가 포함되어 있으면 `underflow`는 첫 번째 문자를 반환합니다. get 영역이 비어 있으면 get 영역 채우고 다음 문자(get 영역에 남겨둔)를 반환합니다. 더 이상 사용 가능한 문자가 없으면 `underflow`는 `EOF`를 반환하고 get 영역을 비워 둡니다.

`strstreambuf` 클래스에서 `underflow`는 `overflow`에 대한 호출에 의해 동적으로 할당된 저장소에 액세스하도록 [egptr](#egptr) 포인터를 조정합니다.

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

입력 스트림에서 요소를 추출하기 위한 보호된 가상 함수입니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>매개 변수

`ptr` 버퍼는 추출 된 문자를 포함할입니다.

`count` 추출할 요소의 수입니다.

### <a name="return-value"></a>반환 값

추출된 요소의 수입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 [sbumpc](#sbumpc)에 대한 반복 호출인 것처럼 입력 스트림에서 최대 `count`개의 요소를 추출하고, `ptr`에서 시작하는 배열에 저장합니다. 실제로 추출된 요소의 수를 반환합니다.

## <a name="xsputn"></a>  basic_streambuf::xsputn

요소를 출력 스트림에 삽입하기 위한 보호된 가상 함수입니다.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>매개 변수

`ptr` 삽입할 요소에 대 한 포인터입니다.

`count` 삽입할 요소의 수입니다.

### <a name="return-value"></a>반환 값

실제로 스트림에 삽입된 요소의 수입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 [sbumpc](#sputc)에 대한 반복 호출인 것처럼, `ptr`에서 시작하는 배열에서 출력 스트림에 최대 `count`개의 요소를 삽입합니다. `count`개 문자가 모두 기록된 경우 또는 `sputc( count)`를 호출하면 `traits::eof()`가 반환되는 경우 출력 스트림에 대한 문자 삽입이 중지됩니다. 실제로 삽입된 요소의 수를 반환합니다.

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
