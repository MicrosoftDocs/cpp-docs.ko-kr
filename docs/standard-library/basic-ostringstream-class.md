---
title: basic_ostringstream 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fb0027ba6afbceed8cc5f1daafef8cb183759ce
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955236"
---
# <a name="basicostringstream-class"></a>basic_ostringstream 클래스

[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 클래스의 스트림 버퍼에 요소 및 인코드된 개체를 삽입하는 방법을 제어하는 개체를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

*Alloc* 할당자 클래스입니다.

*Elem* 문자열 기본 요소의 형식입니다.

*Tr* 문자열의 기본 요소에서 특수화 된 문자 특성입니다.

## <a name="remarks"></a>설명

형식의 요소가 있는 스트림 버퍼에 요소 삽입을 제어 하는 개체 및 인코드된 개체를 설명 하는 클래스 `Elem`에서 문자 특성이 클래스에 의해 결정 됩니다 `Tr`을의 할당자에 의해 할당 되는 요소가 클래스 `Alloc`합니다. 이 개체는 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 클래스의 개체를 저장합니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|`basic_ostringstream` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|형식은 템플릿 매개 변수에 대 한 동의어 *Alloc*합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[rdbuf](#rdbuf)|`pointer` 형식의 저장된 스트림 버퍼 주소를 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>로 반환합니다.|
|[str](#str)|쓰기 위치를 변경하지 않고 문자열 버퍼에서 텍스트를 설정하거나 가져옵니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<sstream>

**네임스페이스:** std

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

형식은 템플릿 매개 변수에 대 한 동의어 *Alloc*합니다.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

Basic_ostringstream 형식의 개체를 생성합니다.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>매개 변수

*모드 (_m)* 의 열거형 중 하나 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode)합니다.

*str* 형식의 개체 `basic_string`합니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 기본 클래스를 호출 하 여 초기화 [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), 여기서 `sb` 클래스의 저장 개체인 [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**하십시오 **Tr**, `Alloc`>. 또한 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`)을 호출하여 **sb**를 초기화합니다.

두 번째 생성자는 basic_ostream( **sb**)를 호출하여 기본 개체를 초기화합니다. 또한 초기화 `sb` basic_stringbuf 호출 하 여 < **Elem**, **Tr**를 `Alloc`> (_ *Str*를 `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

형식의 저장 된 스트림 버퍼 주소를 반환 합니다 `pointer` 를 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**하십시오 **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>반환 값

형식의 저장 된 스트림 버퍼의 주소 `pointer` basic_stringbuf에 < **Elem**하십시오 **Tr**, `Alloc`>.

### <a name="remarks"></a>설명

형식의 저장 된 스트림 버퍼 주소를 반환 하는 멤버 함수 `pointer` basic_stringbuf에 < **Elem**하십시오 **Tr**, `Alloc`>.

### <a name="example"></a>예

`rdbuf`의 사용 예제는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="str"></a>  basic_ostringstream::str

쓰기 위치를 변경하지 않고 문자열 버퍼에서 텍스트를 설정하거나 가져옵니다.

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>매개 변수

*_Newstr* 새 문자열입니다.

### <a name="return-value"></a>반환 값

[basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 클래스의 개체를 반환합니다. 이 개체의 제어된 시퀀스는 **\*this**에 의해 제어된 시퀀스의 복사본입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)을 반환합니다. 두 번째 멤버 함수는 `rdbuf` -> **str**( `_Newstr`)을 호출합니다.

### <a name="example"></a>예

참조 [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) 사용 하는 예제에 대 한 `str`합니다.

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
