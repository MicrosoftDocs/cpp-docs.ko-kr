---
description: Basic_ostringstream 클래스에 대해 자세히 알아보세요.
title: basic_ostringstream 클래스
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: b745f6b733d093b620e15d0aa22593713988caf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325643"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream 클래스

[](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**,> basic_stringbuf 클래스의 스트림 버퍼에 요소 및 인코드된 개체 삽입을 제어 하는 개체에 대해 설명 합니다 `Alloc` .

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

*#C4*\
할당자 클래스입니다.

*E*\
문자열 기본 요소의 형식입니다.

*비교한*\
문자열의 기본 요소에서 특수화된 문자 특성입니다.

## <a name="remarks"></a>설명

이 클래스는 `Elem` 문자 특성이 클래스에 의해 결정 되 `Tr` 고 해당 요소가 클래스의 할당자에 의해 할당 되는 형식의 요소를 사용 하 여 스트림 버퍼에 요소 및 인코드된 개체 삽입을 제어 하는 개체를 설명 합니다 `Alloc` . 이 개체는 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 클래스의 개체를 저장합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|`basic_ostringstream` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|형식은 템플릿 매개 변수 *할당* 의 동의어입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[rdbuf](#rdbuf)|Basic_stringbuf,>의 저장 된 스트림 버퍼 주소를 `pointer` 반환 [](../standard-library/basic-stringbuf-class.md) <  `Elem` `Tr` `Alloc` 합니다.|
|[str](#str)|쓰기 위치를 변경하지 않고 문자열 버퍼에서 텍스트를 설정하거나 가져옵니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<sstream>

**네임스페이스:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a> basic_ostringstream:: allocator_type

형식은 템플릿 매개 변수 *할당* 의 동의어입니다.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a> basic_ostringstream:: basic_ostringstream

Basic_ostringstream 형식의 개체를 생성합니다.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>매개 변수

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode)의 열거형 중 하나입니다.

*문자열*\
`basic_string` 형식의 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**)를 호출 하 여 기본 클래스를 초기화 합니다 `sb` . 여기서는 [](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**,> basic_stringbuf 클래스의 저장 된 개체입니다 `Alloc` . 또한 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`)을 호출하여 **sb** 를 초기화합니다.

두 번째 생성자는 basic_ostream( **sb**)를 호출하여 기본 개체를 초기화합니다. 또한 `sb` **Elem**, **Tr**, `Alloc`> (_ *Str*, &#124;) basic_stringbuf<를 호출 하 여 초기화 `_Mode` `ios_base::out` 합니다.

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a> basic_ostringstream:: rdbuf

형식의 저장 된 스트림 버퍼 주소를 `pointer` [](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**,> basic_stringbuf 반환 합니다 `Alloc` .

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>반환 값

형식 `pointer` basic_stringbuf< **Elem**, **Tr**,>의 저장 된 스트림 버퍼 주소입니다 `Alloc` .

### <a name="remarks"></a>설명

멤버 함수는 `pointer` **Elem**, **Tr**,>< basic_stringbuf에 대 한 형식의 저장 된 스트림 버퍼 주소를 반환 합니다 `Alloc` .

### <a name="example"></a>예제

`rdbuf`의 사용 예제는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="basic_ostringstreamstr"></a><a name="str"></a> basic_ostringstream:: str

쓰기 위치를 변경하지 않고 문자열 버퍼에서 텍스트를 설정하거나 가져옵니다.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>매개 변수

*_Newstr*\
새 문자열입니다.

### <a name="return-value"></a>반환 값

[Basic_string](../standard-library/basic-string-class.md) <  **Elem**, **Tr**,> 클래스의 개체를 반환 `Alloc` 합니다 .이 개체는 제어 되는 시퀀스가 **\* 이** 에 의해 제어 되는 시퀀스의 복사본입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [rdbuf](#rdbuf)  ->  [str](../standard-library/basic-stringbuf-class.md#str)을 반환 합니다. 두 번째 멤버 함수는 `rdbuf`  ->  **str**()를 호출 합니다 `_Newstr` .

### <a name="example"></a>예제

을 사용 하는 예제는 [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) 을 참조 하세요 `str` .

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
