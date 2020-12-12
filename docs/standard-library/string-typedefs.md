---
description: '자세한 정보: &lt; 문자열 &gt; 형식 정의'
title: '&lt;string&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 129d1105defaf06031333b7b06265f8d1bad4a98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183700"
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt; 형식 정의

[문자열](#string)\
[u16string](#u16string)\
[u32string](#u32string)\
[wstring](#wstring)

## <a name="string"></a><a name="string"></a> 문자열

형식의 요소를 사용 하 여 [basic_string](../standard-library/basic-string-class.md) 클래스 템플릿의 특수화를 설명 하는 형식 **`char`** 입니다.

`basic_string`을 특수화하는 기타 형식 정의에는 [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string), [u32string](../standard-library/string-typedefs.md#u32string) 등이 있습니다.

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>설명

아래의 코드 두 줄은 동일한 선언입니다.

```cpp
string str("");

basic_string<char> str("");
```

문자열 생성자 목록은 [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string)을 참조하세요.

## <a name="u16string"></a><a name="u16string"></a> u16string

형식의 요소를 사용 하 여 [basic_string](../standard-library/basic-string-class.md) 클래스 템플릿의 특수화를 설명 하는 형식 **`char16_t`** 입니다.

`basic_string`을 특수화하는 기타 형식 정의에는 [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string), [u32string](../standard-library/string-typedefs.md#u32string) 등이 있습니다.

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>설명

문자열 생성자 목록은 [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string)을 참조하세요.

## <a name="u32string"></a><a name="u32string"></a> u32string

형식의 요소를 사용 하 여 [basic_string](../standard-library/basic-string-class.md) 클래스 템플릿의 특수화를 설명 하는 형식 **`char32_t`** 입니다.

`basic_string`을 특수화하는 기타 형식 정의에는 [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), [wstring](../standard-library/string-typedefs.md#wstring) 등이 있습니다.

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>설명

문자열 생성자 목록은 [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string)을 참조하세요.

## <a name="wstring"></a><a name="wstring"></a> wstring

형식의 요소를 사용 하 여 [basic_string](../standard-library/basic-string-class.md) 클래스 템플릿의 특수화를 설명 하는 형식 **`wchar_t`** 입니다.

`basic_string`을 특수화하는 기타 형식 정의에는 [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), [u32string](../standard-library/string-typedefs.md#u32string) 등이 있습니다.

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>설명

아래의 코드 두 줄은 동일한 선언입니다.

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

문자열 생성자 목록은 [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string)을 참조하세요.

> [!NOTE]
> 의 크기는 **`wchar_t`** 구현에서 정의 됩니다. 코드가 특정 크기에 의존 **`wchar_t`** 하는 경우 플랫폼의 구현 (예: 사용)을 확인 `sizeof(wchar_t)` 합니다. 모든 플랫폼에서 너비가 동일하게 유지되도록 보장되는 문자열 문자 형식이 필요한 경우에는 [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) 또는 [u32string](../standard-library/string-typedefs.md#u32string)을 사용합니다.

## <a name="see-also"></a>참고 항목

[\<string>](../standard-library/string.md)
