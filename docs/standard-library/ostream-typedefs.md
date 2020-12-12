---
description: '자세한 정보: &lt; ostream &gt; typedef'
title: '&lt;ostream&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 886fb729f389fac161e4d154e00898b530d1d9f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193021"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; 형식 정의

[ostream](#ostream)\
[wostream](#wostream)

## <a name="ostream"></a><a name="ostream"></a> ostream

에서 특수화 되 고 특수화 된 basic_ostream에서 형식을 **`char`** 만듭니다 `char_traits` **`char`** .

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-ostream-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_ostream의 동의어입니다.

## <a name="wostream"></a><a name="wostream"></a> wostream

에서 특수화 되 고 특수화 된 basic_ostream에서 형식을 **`wchar_t`** 만듭니다 `char_traits` **`wchar_t`** .

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-ostream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_ostream의 동의어입니다.

## <a name="see-also"></a>참고 항목

[\<ostream>](../standard-library/ostream.md)
