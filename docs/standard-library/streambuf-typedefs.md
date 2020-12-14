---
description: '자세한 정보: &lt; streambuf &gt; typedef'
title: '&lt;streambuf&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: ae5394213143b05704d452e38eaae0b3581849cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221971"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; 형식 정의

[streambuf](#streambuf)\
[wstreambuf](#wstreambuf)

## <a name="streambuf"></a><a name="streambuf"></a> streambuf

를 `basic_streambuf` 템플릿 매개 변수로 사용 하는의 특수화입니다 **`char`** .

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>설명

이 형식은 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_streambuf](../standard-library/basic-streambuf-class.md)의 동의어입니다 **`char`** .

## <a name="wstreambuf"></a><a name="wstreambuf"></a> wstreambuf

를 `basic_streambuf` 템플릿 매개 변수로 사용 하는의 특수화입니다 **`wchar_t`** .

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>설명

이 형식은 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_streambuf](../standard-library/basic-streambuf-class.md)의 동의어입니다 **`wchar_t`** .

## <a name="see-also"></a>참고 항목

[\<streambuf>](../standard-library/streambuf.md)
