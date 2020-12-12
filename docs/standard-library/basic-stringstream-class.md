---
description: Basic_stringstream 클래스에 대해 자세히 알아보세요.
title: basic_stringstream 클래스
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: a236f8b382a2c0f8d77f971493fc16b9ac9da81f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325588"
---
# <a name="basic_stringstream-class"></a>basic_stringstream 클래스

[](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**,> basic_stringbuf 클래스의 스트림 버퍼를 사용 하 여 요소 및 인코드된 개체의 삽입 및 추출을 제어 하는 개체에 대해 설명 합니다 `Alloc` .

## <a name="syntax"></a>구문

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>매개 변수

*#C4*\
할당자 클래스입니다.

*E*\
문자열 기본 요소의 형식입니다.

*비교한*\
문자열의 기본 요소에서 특수화된 문자 특성입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 클래스 [](../standard-library/basic-stringbuf-class.md) <    `Alloc` `Elem` 에서 문자 특성을 결정 하 `Tr` 고 해당 요소가 클래스의 할당자에 의해 할당 되는 형식의 요소가 있는 Elem, Tr,> basic_stringbuf 클래스의 스트림 버퍼를 사용 하 여 요소 및 인코드된 개체의 삽입 및 추출을 제어 하는 개체를 설명 합니다 `Alloc` . 이 개체는 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 클래스의 개체를 저장합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[basic_stringstream](#basic_stringstream)|`basic_stringstream` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|이 형식은 템플릿 매개 변수 `Alloc`의 동의어입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[rdbuf](#rdbuf)|Basic_stringbuf,>의 저장 된 스트림 버퍼 주소를 `pointer` 반환 [](../standard-library/basic-stringbuf-class.md) <  `Elem` `Tr` `Alloc` 합니다.|
|[str](#str)|쓰기 위치를 변경하지 않고 문자열 버퍼에서 텍스트를 설정하거나 가져옵니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<sstream>

**네임스페이스:** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a> basic_stringstream:: allocator_type

이 형식은 템플릿 매개 변수 `Alloc`의 동의어입니다.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a> basic_stringstream:: basic_stringstream

`basic_stringstream` 형식의 개체를 생성합니다.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>매개 변수

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode)의 열거형 중 하나입니다.

*문자열*\
`basic_string` 형식의 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**)를 호출 하 여 기본 클래스를 초기화 합니다 `sb` . 여기서는 [](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**,> basic_stringbuf 클래스의 저장 된 개체입니다 `Alloc` . 또한 `sb` **Elem**, **Tr**,> () basic_stringbuf< 호출 하 여 초기화 `Alloc` `_Mode` 합니다.

두 번째 생성자는 basic_iostream( **sb**)를 호출하여 기본 개체를 초기화합니다. 또한 `sb` **Elem**, **Tr**, `Alloc`> (_ *Str*,) basic_stringbuf<를 호출 하 여 초기화 `_Mode` 합니다.

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a> basic_stringstream:: rdbuf

**pointer** 형식의 저장된 스트림 버퍼 주소를 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>로 반환합니다.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>반환 값

`pointer` **Elem**, **Tr**,>< basic_stringbuf 되는 형식의 저장 된 스트림 버퍼 주소입니다 `Alloc` .

### <a name="example"></a>예제

`rdbuf`의 사용 예제는 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)를 참조하세요.

## <a name="basic_stringstreamstr"></a><a name="str"></a> basic_stringstream:: str

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
