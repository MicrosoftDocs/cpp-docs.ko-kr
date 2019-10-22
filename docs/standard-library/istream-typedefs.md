---
title: '&lt;istream&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689486"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; 형식 정의

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

**Char**에 특수화 된 형식 `basic_iostream`입니다.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>주의

이 형식은 기본 문자 특성을 포함 하는 **char** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_iostream](../standard-library/basic-iostream-class.md)의 동의어입니다.

## <a name="istream"></a>  istream

**Char**에 특수화 된 형식 `basic_istream`입니다.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>주의

이 형식은 기본 문자 특성을 포함 하는 **char** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_istream](../standard-library/basic-istream-class.md)의 동의어입니다.

## <a name="wiostream"></a>  wiostream

**Wchar_t**에서 특수화 된 형식 `basic_iostream`입니다.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>주의

이 형식은 기본 문자 특성을 포함 하는 **wchar_t** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_iostream](../standard-library/basic-iostream-class.md)의 동의어입니다.

## <a name="wistream"></a>  wistream

**Wchar_t**에서 특수화 된 형식 `basic_istream`입니다.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>주의

이 형식은 기본 문자 특성을 포함 하는 **wchar_t** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_istream](../standard-library/basic-istream-class.md)의 동의어입니다.

## <a name="see-also"></a>참조

[\<istream>](../standard-library/istream.md)
