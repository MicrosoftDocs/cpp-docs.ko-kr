---
description: '자세한 정보: &lt; 로캘 &gt; 함수'
title: '&lt;locale&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 6bad3cab6886fcee34fba06e88ce54e216db4649
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284618"
---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt; 함수

[has_facet](#has_facet)\
[isalnum](#isalnum)\
[isalpha](#isalpha)\
[iscntrl](#iscntrl)\
[isdigit](#isdigit)\
[isgraph](#isgraph)\
[islower](#islower)\
[isprint](#isprint)\
[ispunct](#ispunct)\
[isspace](#isspace)\
[isupper](#isupper)\
[isxdigit](#isxdigit)\
[tolower](#tolower)\
[toupper](#toupper)\
[use_facet](#use_facet)

## <a name="has_facet"></a><a name="has_facet"></a> has_facet

특정 패싯이 지정된 로캘에 저장되었는지를 테스트합니다.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>매개 변수

*Loc*\
패싯이 있는지 테스트할 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 로캘에 테스트 된 패싯이 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `use_facet`을 호출하여 패싯이 없는 경우 throw되는 예외를 방지하기 전에 필수가 아닌 패싯이 로캘에 나열되는지 여부를 확인하는 데 유용합니다.

### <a name="example"></a>예제

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a><a name="isalnum"></a> isalnum

로캘의 요소가 알파벳인지 또는 숫자인지를 테스트합니다.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 영숫자 요소입니다.

*Loc*\
테스트할 영숫자 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 영숫자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="example"></a>예제

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a><a name="isalpha"></a> isalpha

로캘의 요소가 영문자인지를 테스트합니다.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 영문자 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 한 요소가 영문자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [는](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **alpha**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a><a name="iscntrl"></a> iscntrl

로캘의 요소가 제어 문자인지를 테스트합니다.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 한 요소가 제어 문자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **cntrl**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a><a name="isdigit"></a> isdigit

로캘의 요소가 숫자인지를 테스트합니다.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 숫자 문자인 경우 **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [는](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **digit**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a><a name="isgraph"></a> isgraph

로캘의 요소가 영숫자인지 문장 부호인지를 테스트합니다.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 영숫자 또는 문장 부호 문자인 경우 **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **graph**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a><a name="islower"></a> islower

로캘의 요소가 소문자인지를 테스트합니다.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 소문자 문자인 경우 **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **lower**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a><a name="isprint"></a> isprint

로캘의 요소가 인쇄 가능한 문자인지를 테스트합니다.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 인쇄 가능한 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **print**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a><a name="ispunct"></a> ispunct

로캘의 요소가 문장 부호 문자인지를 테스트합니다.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 문장 부호 문자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) `<` [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **punct**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a><a name="isspace"></a> isspace

로캘의 요소가 공백 문자인지를 테스트합니다.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 공백 문자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [는](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **space**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a><a name="isupper"></a> isupper

로캘의 요소가 대문자인지를 테스트합니다.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 대문자 이면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **upper**, `Ch` )입니다.

### <a name="example"></a>예제

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a><a name="isxdigit"></a> isxdigit

로캘의 요소가 16자 숫자를 나타내는 데 사용되는 문자인지를 테스트합니다.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
테스트할 요소입니다.

*Loc*\
테스트할 요소를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

**`true`** 테스트 된 요소가 16 진수를 나타내는 데 사용 되는 문자인 경우 **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [는](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**> :: **xdigit**, `Ch` )입니다.

16진수는 16을 기준으로 사용하여 숫자를 나타내는데, 숫자 0-9와 대/소문자를 구분하지 않는 문자 A-F를 사용하여 10진수 0-15를 나타냅니다.

### <a name="example"></a>예제

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a><a name="tolower"></a> tolower

문자를 소문자로 변환합니다.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
소문자로 변환할 문자입니다.

*Loc*\
변환할 문자를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

소문자로 변환된 문자입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [tolower](../standard-library/ctype-class.md#tolower)( `Ch` ).

### <a name="example"></a>예제

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a><a name="toupper"></a> toupper

문자를 대문자로 변환합니다.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>매개 변수

*Ch*\
대문자로 변환할 문자입니다.

*Loc*\
변환할 문자를 포함하는 로캘입니다.

### <a name="return-value"></a>반환 값

대문자로 변환된 문자입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > () use_facet 반환 합니다 `Loc` . [toupper](../standard-library/ctype-class.md#toupper)( `Ch` ).

### <a name="example"></a>예제

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a><a name="use_facet"></a> use_facet

로캘에 저장된 지정된 형식의 패싯에 대한 참조를 반환합니다.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>매개 변수

*Loc*\
참조되는 패싯의 형식을 포함하는 const 로캘입니다.

### <a name="return-value"></a>반환 값

인수 로캘 내에 포함된 `Facet` 클래스의 패싯에 대한 참조입니다.

### <a name="remarks"></a>설명

템플릿 함수에서 반환한 패싯에 대한 참조는 포함하는 로캘의 모든 복사본이 존재하는 한 유효한 상태로 유지됩니다. `Facet` 클래스의 이러한 패싯 개체가 인수 로캘에 나열되지 않는 경우 이 함수는 `bad_cast` 예외를 throw합니다.

### <a name="example"></a>예제

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)
