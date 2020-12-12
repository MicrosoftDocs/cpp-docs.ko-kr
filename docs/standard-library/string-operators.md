---
description: '다음에 대 한 자세한 정보: &lt; 문자열 &gt; 연산자'
title: '&lt;string&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: 9a23b4539fbb84533de83a541458deddbd13615e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183713"
---
# <a name="ltstringgt-operators"></a>&lt;string&gt; 연산자

[연산자! =](#op_neq)\
[연산자&gt;](#op_gt)\
[연산자&gt;&gt;](#op_gt_gt)\
[연산자&gt;=](#op_gt_eq)\
[연산자&lt;](#op_lt)\
[연산자&lt;&lt;](#op_lt_lt)\
[연산자&lt;=](#op_lt_eq)\
[연산자 +](#op_add)\
[연산자 = =](#op_eq_eq)

## <a name="operator"></a><a name="op_add"></a> 연산자 +

두 문자열 개체를 연결합니다.

```cpp
template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
연결할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
연결할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

입력 문자열의 연결인 문자열입니다.

### <a name="remarks"></a>설명

함수는 각 오버 로드를 오버 로드 `operator+` 하 여 클래스 템플릿 [basic_string 클래스](../standard-library/basic-string-class.md)의 두 개체를 연결 합니다. 모든를 효과적으로 반환 `basic_string< CharType, Traits, Allocator>(Left).append(right)` 합니다. 자세한 내용은 [append](../standard-library/basic-string-class.md#append)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// string_op_con.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "anti" );
   string s2 ( "gravity" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "heroine";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // Declaring a character constant
   char c1 = '!';
   cout << "The character constant c1 = " << c1 << "." << endl;

   // First member function: concatenates an  object
   // of type basic_string with an object of type basic_string
   string s12 = s1 + s2;
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;

   // Second & fourth member functions: concatenate an object
   // of type basic_string with an object of C-syle string type
   string s1s3 = s1 + s3;
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;

   // Third & fifth member functions: concatenate an object
   // of type basic_string with a character constant
   string s1s3c1 = s1s3 + c1;
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;
}
```

```Output
The basic_string s1 = anti.
The basic_string s2 = gravity.
The C-style string s3 = heroine.
The character constant c1 = !.
The string concatenating s1 & s2 is: antigravity
The string concatenating s1 & s3 is: antiheroine
The string concatenating s1 & s3 is: antiheroine!
```

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체와 같지 않은지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 문자열 개체가 우변에 있는 문자열 개체와 사전순으로 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

string 개체 간의 비교는 해당 문자의 쌍 단위 어휘 비교를 기반으로 합니다. 문자 수와 개별 문자 값이 같은 두 문자열은 동일한 문자열입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// string_op_ne.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 != s2 )
      cout << "The strings s1 & s2 are not equal." << endl;
   else
      cout << "The strings s1 & s2 are equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 != s3 )
      cout << "The strings s1 & s3 are not equal." << endl;
   else
      cout << "The strings s1 & s3 are equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 != s2 )
      cout << "The strings s3 & s2 are not equal." << endl;
   else
      cout << "The strings s3 & s2 are equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체와 같은지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 string 개체의 사전순으로가 우변에 있는 string 개체와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

string 개체 간의 비교는 해당 문자의 쌍 단위 어휘 비교를 기반으로 합니다. 문자 수와 개별 문자 값이 같은 두 문자열은 동일한 문자열입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// string_op_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 == s2 )
      cout << "The strings s1 & s2 are equal." << endl;
   else
      cout << "The strings s1 & s2 are not equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 == s3 )
      cout << "The strings s1 & s3 are equal." << endl;
   else
      cout << "The strings s1 & s3 are not equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 == s2 )
      cout << "The strings s3 & s2 are equal." << endl;
   else
      cout << "The strings s3 & s2 are not equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 작은지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 문자열 개체가 우변에 있는 문자열 개체 보다 사전순으로 면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

문자열 간의 어휘 비교에서는 다음이 확인될 때까지 두 문자열의 문자를 하나씩 비교합니다.

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

```cpp
// string_op_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 < s2 )
      cout << "The string s1 is less than the string s2." << endl;
   else
      cout << "The string s1 is not less than the string s2." << endl;

   // Second member function: comparison between left-hand object
   // of type basic_string & right-hand object of C-syle string type
   if ( s1 < s3 )
      cout << "The string s1 is less than the string s3." << endl;
   else
      cout << "The string s1 is not less than the string s3." << endl;

   // Third member function: comparison between left-hand object
   // of C-syle string type & right-hand object of type basic_string
   if ( s3 < s2 )
      cout << "The string s3 is less than the string s2." << endl;
   else
      cout << "The string s3 is not less than the string s2." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than the string s2.
The string s1 is not less than the string s3.
The string s3 is less than the string s2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 작거나 같은지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 문자열 개체가 우변에 있는 문자열 개체 보다 작거나 같으면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

문자열 간의 어휘 비교에서는 다음이 확인될 때까지 두 문자열의 문자를 하나씩 비교합니다.

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

```cpp
// string_op_le.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 <= s2 )
      cout << "The string s1 is less than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 <= s3 )
      cout << "The string s1 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s3." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type  & right-side object of type basic_string
   if ( s2 <= s3 )
      cout << "The string s2 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than or equal to the string s2.
The string s1 is less than or equal to the string s3.
The string s2 is greater than the string s3.
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

문자열을 출력 스트림에 기록하는 템플릿 함수입니다.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>매개 변수

*_Ostr*\
문자열이 기록되는 출력 스트림입니다.

*문자열*\
출력 스트림에 입력할 문자열입니다.

### <a name="return-value"></a>반환 값

지정 된 문자열의 값을 출력 스트림에 *_Ostr* 씁니다.

### <a name="remarks"></a>설명

템플릿 함수 오버 로드 **연산자를<<** 하 여 클래스 템플릿 [basic_string](../standard-library/basic-string-class.md) 의 개체 *str* 을 스트림 *\_ ostr* 에 삽입할 수 있습니다. 함수는를 효과적으로 반환 `_Ostr.write( str.c_str, str.size )` 합니다.

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 큰지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 문자열 개체가 우변에 있는 문자열 개체 보다 사전순으로 면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

문자열 간의 어휘 비교에서는 다음이 확인될 때까지 두 문자열의 문자를 하나씩 비교합니다.

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

```cpp
// string_op_gt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 > s2 )
      cout << "The string s1 is greater than "
           << "the string s2." << endl;
   else
      cout << "The string s1 is not greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 > s1 )
      cout << "The string s3 is greater than "
           << "the string s1." << endl;
   else
      cout << "The string s3 is not greater than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 > s3 )
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
   else
      cout << "The string s2 is not greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is not greater than the string s2.
The string s3 is greater than the string s1.
The string s2 is greater than the string s3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 크거나 같은지 테스트합니다.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

*오른쪽*\
비교할 `basic_string` 형식의 C 스타일 문자열 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자의 좌 변에 있는 문자열 개체가 우변에 있는 문자열 개체 보다 크거나 같으면이 고, 그렇지 않으면 사전순으로입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

문자열 간의 어휘 비교에서는 다음이 확인될 때까지 두 문자열의 문자를 하나씩 비교합니다.

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

```cpp
// string_op_ge.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 >= s2 )
      cout << "The string s1 is greater than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is less than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 >= s1 )
      cout << "The string s3 is greater than or equal to "
           << "the string s1." << endl;
   else
      cout << "The string s3 is less than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 >= s3 )
      cout << "The string s2 is greater than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is less than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is less than the string s2.
The string s3 is greater than or equal to the string s1.
The string s2 is greater than or equal to the string s3.
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a> 연산자&gt;&gt;

입력 스트림에서 문자열을 읽는 템플릿 함수입니다.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*_Istr*\
시퀀스를 추출하는 데 사용되는 입력 스트림입니다.

*오른쪽*\
입력 스트림에서 추출되는 문자열입니다.

### <a name="return-value"></a>반환 값

*_Istr* 에서 지정 된 문자열의 값을 읽고 *오른쪽* 으로 반환 합니다.

### <a name="remarks"></a>설명

`skipws` 플래그가 설정된 경우가 아니면 연산자는 선행 공백을 건너뜁니다. 그리고 다음 문자가 공백이거나 파일의 끝에 도달할 때까지 뒤에 오는 모든 문자를 읽습니다.

템플릿 함수는 **>>연산자** 를 오버 로드 하 여 *right* 로 제어 되는 시퀀스를 *_Istr* 스트림에서 추출 된 요소 시퀀스로 바꿉니다. 다음과 같은 경우 추출이 중지됩니다.

- 파일의 끝.

- 함수가 `_Istr`을 추출한 후 값이 0이 아닌 경우 **width** 요소

함수가 `_Istr`을 추출한 후 [max_size](../standard-library/basic-string-class.md#max_size) 요소

- 함수는  [](../standard-library/basic-filebuf-class.md#open) <  **ctype** \< **CharType**> > () use_facet 요소를 추출 `getloc` 합니다. **is**( **ctype** \< **CharType**> :: **space**, *ch*)는 true 이며,이 경우 문자는 다시 배치 됩니다.

함수가 요소를 추출 하지 않으면 [setstate](../standard-library/basic-ios-class.md#setstate)()를 호출 `ios_base::failbit` 합니다. 어떤 경우든 **istr**. **width**(0) 및는를 반환 \* **`this`** 합니다.

### <a name="example"></a>예제

```cpp
// string_op_read_.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string c0;
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";
   cin >> c0;
   cout << "The string entered is c0 = " << c0 << endl;
}
```

## <a name="see-also"></a>참고 항목

[\<string>](../standard-library/string.md)
