---
description: '자세히 알아보기: &lt; istream &gt; 형식 정의'
title: '&lt;istream&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 576d1be7733a01689b4cfc511049dfad89390f63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277858"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; 형식 정의

[iostream](#iostream)\
[istream](#istream)\
[wiostream](#wiostream)\
[wistream](#wistream)

## <a name="iostream"></a><a name="iostream"></a> iostream

`basic_iostream`에서 특수화 된 형식 **`char`** 입니다.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-iostream-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_iostream의 동의어입니다.

## <a name="istream"></a><a name="istream"></a> istream

`basic_istream`에서 특수화 된 형식 **`char`** 입니다.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-istream-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_istream의 동의어입니다.

## <a name="wiostream"></a><a name="wiostream"></a> wiostream

`basic_iostream`에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-iostream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_iostream의 동의어입니다.

## <a name="wistream"></a><a name="wistream"></a> wistream

`basic_istream`에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-istream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_istream의 동의어입니다.

## <a name="see-also"></a>참고 항목

[\<istream>](../standard-library/istream.md)
