---
description: '다음에 대 한 자세한 정보: &lt; a m&gt;'
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 5f0c5307073c2296f20df0adb663bce9b4b97d59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169101"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

할당 된 배열 개체에 저장 된 시퀀스에 대 한 iostreams 작업을 지 원하는 여러 클래스 템플릿을 정의 합니다. 이러한 시퀀스는 [basic_string](../standard-library/basic-string-class.md)클래스 템플릿 개체와 쉽게 변환 됩니다.

## <a name="syntax"></a>구문

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>매개 변수

*비어*\
`sstream` 개체에 대한 참조입니다.

*오른쪽*\
`sstream` 개체에 대한 참조입니다.

## <a name="remarks"></a>설명

형식의 개체 `char *` 는의 기능을 사용 하 여 스트리밍할 수 있습니다 [\<strstream>](../standard-library/strstream.md) . 그러나 \<strstream>은 사용되지 않으며 \<sstream>을 사용하는 것이 좋습니다.

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|`basic_istringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`char`** .|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|`basic_ostringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`char`** .|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|`basic_stringbuf`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`char`** .|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|`basic_stringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`char`** .|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|`basic_istringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`wchar_t`** .|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|`basic_ostringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`wchar_t`** .|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|`basic_stringbuf`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`wchar_t`** .|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|`basic_stringstream`템플릿 매개 변수에서 특수화 된 형식을 만듭니다 **`wchar_t`** .|

### <a name="manipulators"></a>조작자

|Name|설명|
|-|-|
|[스왑을](../standard-library/sstream-functions.md#sstream_swap)|두 `sstream` 개체 간에 값을 교환합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|배열 개체에 저장된 요소의 시퀀스에서 문자 특성이 `Tr` 클래스에 의해 결정되는 `Elem` 형식 요소의 전송을 제어하는 스트림 버퍼에 대해 설명합니다.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|[](../standard-library/basic-stringbuf-class.md) <   `Alloc` `Elem` 문자 특성이 클래스에 의해 결정 되 `Tr` 고 해당 요소가 클래스의 할당자에 의해 할당 되는 형식의 요소가 있는 클래스 basic_stringbuf Elem, Tr,>의 스트림 버퍼에서 요소 및 인코드된 개체의 추출을 제어 하는 개체에 대해 설명 합니다 `Alloc` .|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|[](../standard-library/basic-stringbuf-class.md) <   `Alloc` `Elem` 문자 특성이 클래스에 의해 결정 되 `Tr` 고 해당 요소가 클래스의 할당자에 의해 할당 되는 형식의 요소가 있는 클래스 basic_stringbuf Elem, Tr,>의 스트림 버퍼에 요소 및 인코드된 개체 삽입을 제어 하는 개체에 대해 설명 합니다 `Alloc` .|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|[](../standard-library/basic-stringbuf-class.md) <   `Alloc` `Elem` 문자 특성이 클래스에 의해 결정 되 `Tr` 고 해당 요소가 클래스의 할당자에 의해 할당 되는 형식의 요소가 있는 Elem, Tr,> basic_stringbuf 클래스의 스트림 버퍼를 사용 하 여 요소 및 인코드된 개체의 삽입 및 추출을 제어 하는 개체에 대해 설명 합니다 `Alloc` .|

## <a name="requirements"></a>요구 사항

- **헤더:**\<sstream>

- **네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
