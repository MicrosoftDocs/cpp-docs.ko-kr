---
description: '다음에 대 한 자세한 정보: char_traits 구조체'
title: char_traits 구조체
ms.date: 05/07/2019
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: a42aa29f2400d4610974530de04699daa32b7f1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325237"
---
# <a name="char_traits-struct"></a>char_traits 구조체

char_traits 구조체는 문자와 연결된 특성을 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>매개 변수

*CharType*\
요소 데이터 형식입니다.

## <a name="remarks"></a>설명

템플릿 구조체는 형식에 대 한 다양 한 문자 특성을 설명 합니다 `CharType` . 클래스 템플릿 [basic_string](../standard-library/basic-string-class.md) 및 [basic_ios](../standard-library/basic-ios-class.md)를 비롯 한 몇 가지 iostream 클래스 템플릿은이 정보를 사용 하 여 형식의 요소를 조작 `CharType` 합니다. 이러한 요소 형식은 명시적 생성 또는 소멸을 요구하지 않아야 합니다. 기본 생성자, 복사 생성자 및 대입 연산자에 예상 의미 체계를 제공해야 합니다. 비트 복사는 할당과 동일한 효과가 있어야 합니다. char_traits 구조체의 멤버 함수는 예외를 발생시킬 수 없습니다.

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|문자 형식입니다.|
|[int_type](#int_type)|`char_type` 형식의 문자 또는 EOF(파일 끝) 문자를 나타낼 수 있는 정수 형식입니다.|
|[off_type](#off_type)|스트림 내의 위치 간 오프셋을 나타낼 수 있는 정수 형식입니다.|
|[pos_type](#pos_type)|스트림 내의 위치를 나타낼 수 있는 정수 형식입니다.|
|[state_type](#state_type)|스트림 내의 멀티바이트 문자에 대한 변환 상태를 나타내는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[assign](#assign)|한 문자 값을 다른 문자 값에 할당합니다.|
|[과](#compare)|두 문자열의 문자를 지정한 개수까지 비교합니다.|
|[copy](#copy)|한 문자열에서 다른 문자열로 지정한 개수의 문자를 복사합니다. 더 이상 사용되지 않습니다. 대신 [char_traits::_Copy_s](#copy_s)를 사용합니다.|
|[_Copy_s](#copy_s)|한 문자열에서 다른 문자열로 지정한 개수의 문자를 복사합니다.|
|[객체](#eof)|EOF(파일 끝) 문자를 반환합니다.|
|[eq](#eq)|두 `char_type` 문자가 같은지 테스트합니다.|
|[eq_int_type](#eq_int_type)|`int_type`로 표시된 두 문자가 같은지 테스트합니다.|
|[find](#find)|문자 범위에서 지정한 문자의 첫 번째 발생을 검색합니다.|
|[length](#length)|문자열의 길이를 반환합니다.|
|[lt](#lt)|한 문자가 다른 문자보다 작은지 테스트합니다.|
|[move](#move)|한 시퀀스에서 겹칠 수 있는 다른 시퀀스로 지정한 개수의 문자를 복사합니다. 더 이상 사용되지 않습니다. 대신 [char_traits::_Move_s](#move_s)를 사용합니다.|
|[_Move_s](#move_s)|한 시퀀스에서 겹칠 수 있는 다른 시퀀스로 지정한 개수의 문자를 복사합니다.|
|[not_eof](#not_eof)|문자가 EOF(파일 끝) 문자인지 테스트합니다.|
|[to_char_type](#to_char_type)|`int_type` 문자를 해당하는 `char_type` 문자로 변환하고 결과를 반환합니다.|
|[to_int_type](#to_int_type)|`char_type` 문자를 해당하는 `int_type` 문자로 변환하고 결과를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<string>

**네임스페이스:** std

## <a name="char_traitsassign"></a><a name="assign"></a> char_traits:: assign

문자열의 다른 요소 또는 다양한 요소에 하나의 문자 값을 할당합니다.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>매개 변수

값을 할당할 문자에서 **_** *charfrom*

*_CharTo*\
문자 값을 할당받을 요소입니다.

*strTo*\
초기 요소가 문자 값을 할당받을 문자열 또는 문자 배열입니다.

*_Num*\
값을 할당받을 예정인 요소의 수입니다.

### <a name="return-value"></a>반환 값

두 번째 멤버 함수는 첫 번째 *_Num* 요소에 *_CharFrom* 값이 할당 된 문자열에 대 한 포인터를 반환 합니다.

### <a name="example"></a>예제

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_traitschar_type"></a><a name="char_type"></a> char_traits:: char_type

문자 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `CharType`의 동의어입니다.

### <a name="example"></a>예제

`char_type`을 선언하고 사용하는 방법에 대한 예제는 [copy](#copy)의 예제를 참조하세요.

## <a name="char_traitscompare"></a><a name="compare"></a> char_traits:: compare

두 문자열의 문자를 지정한 개수까지 비교합니다.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>매개 변수

*str1*\
서로 비교할 두 문자열의 첫 번째입니다.

*str2*\
서로 비교할 두 문자열의 두 번째입니다.

*_Num*\
비교할 문자열에 있는 요소의 수입니다.

### <a name="return-value"></a>반환 값

첫 번째 문자열이 두 번째 문자열보다 작은 경우 음수 값, 두 문자열이 같은 경우 0, 첫 번째 문자열이 두 번째 문자열보다 큰 경우 양수 값입니다.

### <a name="remarks"></a>설명

요소별로 두 문자열을 비교합니다. 먼저 요소가 서로 같은지 테스트한 후 시퀀스에서 요소 쌍이 같지 않으면 더 작은지 테스트합니다.

두 문자열이 범위에 대해 같은지 비교하되 하나가 다른 문자열보다 길면 두 문자열 중 짧은 문자열이 더 긴 문자열보다 작습니다.

### <a name="example"></a>예제

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="char_traitscopy"></a><a name="copy"></a> char_traits:: copy

한 문자열에서 다른 문자열로 지정한 개수의 문자를 복사합니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다. 대신 [char_traits::_Copy_s](#copy_s)를 사용하는 것이 좋습니다.

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>매개 변수

*_To*\
복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*_From*\
복사할 소스 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*_Num*\
복사할 요소의 수입니다.

### <a name="return-value"></a>반환 값

복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열로 복사되는 첫 번째 요소입니다.

### <a name="remarks"></a>설명

소스 및 대상 문자 시퀀스는 겹치지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="char_traits_copy_s"></a><a name="copy_s"></a> char_traits:: _Copy_s

한 문자열에서 다른 문자열로 지정한 개수의 문자를 복사합니다.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>매개 변수

*dest*\
복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열입니다.

*dest_size*\
*대상* 의 크기입니다. `char_type`가 이면 **`char`** 이 크기는 바이트 단위입니다. `char_type`가 이면 **`wchar_t`** 이 크기는 단어 단위입니다.

*_From*\
복사할 소스 문자열 또는 문자 배열입니다.

*수*\
복사할 요소의 수입니다.

### <a name="return-value"></a>반환 값

복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열입니다.

### <a name="remarks"></a>설명

소스 및 대상 문자 시퀀스는 겹치지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="char_traitseof"></a><a name="eof"></a> char_traits:: eof

EOF(파일 끝) 문자를 반환합니다.

```cpp
static int_type eof();
```

### <a name="return-value"></a>반환 값

EOF 문자입니다.

### <a name="remarks"></a>설명

EOF 또는 WEOF 파일의 끝을 나타내는 값입니다.

C++ 표준에서는 이 값이 유효한 `char_type` 값에 해당하면 안 됩니다. Microsoft c + + 컴파일러는 형식에 대해서는이 제약 조건을 적용 하지만 형식에는 적용 **`char`** 하지 않습니다 **`wchar_t`** . 아래 예제에서는 이 작업을 보여 줍니다.

### <a name="example"></a>예제

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="char_traitseq"></a><a name="eq"></a> char_traits:: eq

두 `char_type` 문자가 같은지 테스트합니다.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>매개 변수

*_Ch1*\
같은지 테스트할 두 문자 중 첫 번째입니다.

*_Ch2*\
같은지 테스트할 두 문자 중 두 번째입니다.

### <a name="return-value"></a>반환 값

**`true`** 첫 번째 문자가 두 번째 문자와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="char_traitseq_int_type"></a><a name="eq_int_type"></a> char_traits:: eq_int_type

`int_type`으로 표시된 두 문자가 같은지 여부를 테스트합니다.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>매개 변수

*_Ch1*\
S로 같은지 테스트할 두 문자 중 첫 번째 문자입니다 `int_type` .

*_Ch2*\
`int_type`이 같은지 테스트할 두 문자 중 두 번째입니다.

### <a name="return-value"></a>반환 값

**`true`** 첫 번째 문자가 두 번째 문자와 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="char_traitsfind"></a><a name="find"></a> char_traits:: find

문자 범위에서 지정한 문자의 첫 번째 발생을 검색합니다.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>매개 변수

*문자열*\
검색할 문자열의 첫 번째 문자입니다.

*_Num*\
검색할 범위에서의 위치 수입니다(첫 번째부터 계산).

*_Ch*\
범위에서 검색할 문자입니다.

### <a name="return-value"></a>반환 값

일치 항목이 발견되는 경우 범위에서 지정된 문자 중 처음 나오는 문자에 대한 포인터입니다. 일치 항목이 발견되지 않으면 Null 포인터입니다.

### <a name="example"></a>예제

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="char_traitsint_type"></a><a name="int_type"></a> char_traits:: int_type

`char_type` 형식의 문자 또는 EOF(파일 끝) 문자를 나타낼 수 있는 정수 형식입니다.

```cpp
typedef long int_type;
```

### <a name="remarks"></a>설명

형식의 값을 형식으로 캐스팅 `CharType` `int_type` 한 다음 `CharType` 원래 값을 변경 하지 않고 다시로 변환할 수 있어야 합니다.

### <a name="example"></a>예제

`int_type`을 선언하고 사용하는 방법에 대한 예제는 [eq_int_type](#eq_int_type)의 예제를 참조하세요.

## <a name="char_traitslength"></a><a name="length"></a> char_traits:: length

문자열의 길이를 반환합니다.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>매개 변수

*문자열*\
길이를 측정할 C 문자열입니다.

### <a name="return-value"></a>반환 값

측정되는 시퀀스의 요소 수입니다(Null 종결자를 포함하지 않음).

### <a name="example"></a>예제

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="char_traitslt"></a><a name="lt"></a> char_traits:: lt

한 문자가 다른 문자보다 작은지 테스트합니다.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>매개 변수

*_Ch1*\
작은지 테스트할 두 문자 중 첫 번째입니다.

*_Ch2*\
작은지 테스트할 두 문자 중 두 번째입니다.

### <a name="return-value"></a>반환 값

**`true`** 첫 번째 문자가 두 번째 문자 보다 작은 경우 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="char_traitsmove"></a><a name="move"></a> char_traits:: move

한 시퀀스에서 겹칠 수 있는 다른 시퀀스로 지정한 개수의 문자를 복사합니다.

이 메서드는 전달된 값이 정확한지 확인하기 위해 호출자를 사용하므로 보안상 위험할 수 있습니다. 대신 [char_traits::_Move_s](#move_s)를 사용하는 것이 좋습니다.

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>매개 변수

*_To*\
복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*_From*\
복사할 소스 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*_Num*\
소스 문자열에서 복사할 요소의 수입니다.

### <a name="return-value"></a>반환 값

첫 번째 요소는 복사 된 문자 시퀀스를 수신 하도록 지정 된 문자열 또는 문자 배열로 복사 *_To* 합니다.

### <a name="remarks"></a>설명

소스 및 대상이 겹칠 수 있습니다.

### <a name="example"></a>예제

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="char_traits_move_s"></a><a name="move_s"></a> char_traits:: _Move_s

한 시퀀스에서 겹칠 수 있는 다른 시퀀스로 지정한 개수의 문자를 복사합니다.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>매개 변수

*dest*\
복사된 문자 시퀀스를 수신하도록 지정된 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*dest_size*\
*대상* 의 크기입니다. `char_type`가 이면 **`char`** 바이트 단위입니다. `char_type`가 이면 **`wchar_t`** 단어 단위입니다.

*_From*\
복사할 소스 문자열 또는 문자 배열의 시작 부분에 있는 요소입니다.

*수*\
소스 문자열에서 복사할 요소의 수입니다.

### <a name="return-value"></a>반환 값

복사 된 문자 시퀀스를 수신 하도록 지정 된 대상 문자열 또는 문자 배열로 복사 되는 첫 *번째 요소입니다* .

### <a name="remarks"></a>설명

소스 및 대상이 겹칠 수 있습니다.

### <a name="example"></a>예제

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="char_traitsnot_eof"></a><a name="not_eof"></a> char_traits:: not_eof

문자가 EOF(파일 끝) 문자인지 아닌지 테스트합니다.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>매개 변수

*_Ch*\
EOF 문자인지 여부를 테스트할 `int_type`으로 표시된 문자입니다.

### <a name="return-value"></a>반환 값

`int_type` `int_type` 문자의가 EOF 문자의와 같지 않은 경우 테스트 한 문자의 표현입니다.

문자 `int_type` 값이 EOF 값과 같으면이 `int_type` 고, 그렇지 않으면 **`false`** 입니다.

### <a name="example"></a>예제

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="char_traitsoff_type"></a><a name="off_type"></a> char_traits:: off_type

스트림 내의 위치 간 오프셋을 나타낼 수 있는 정수 형식입니다.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>설명

이 형식은 다양한 스트림 위치 지정 작업과 관련된 바이트 오프셋을 저장할 수 있는 개체를 설명하는 부호 있는 정수입니다. 일반적으로 이 형식은 [streamoff](../standard-library/ios-typedefs.md#streamoff)의 동의어이며, 기본적으로 해당 형식과 동일한 속성을 가집니다.

## <a name="char_traitspos_type"></a><a name="pos_type"></a> char_traits::p os_type

스트림 내의 위치를 나타낼 수 있는 정수 형식입니다.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>설명

이 형식은 스트림 내의 임의 파일 위치 표시기를 복원하는 데 필요한 모든 정보를 저장할 수 있는 개체를 설명합니다. 일반적으로 이 형식은 [streampos](../standard-library/ios-typedefs.md#streampos)의 동의어이며, 어떤 경우에든 기본적으로 해당 형식과 동일한 속성을 가집니다.

## <a name="char_traitsstate_type"></a><a name="state_type"></a> char_traits:: state_type

스트림 내 멀티바이트 문자에 대한 변환 상태를 나타내는 형식입니다.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>설명

형식은 변환 상태를 나타낼 수 있는 개체에 대해 설명합니다. 일반적으로 이 형식은 `mbstate_t`의 동의어이며, 어떤 경우에든 기본적으로 해당 형식과 동일한 속성을 가집니다.

## <a name="char_traitsto_char_type"></a><a name="to_char_type"></a> char_traits:: to_char_type

`int_type` 문자를 해당하는 `char_type` 문자로 변환하고 결과를 반환합니다.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>매개 변수

*_Ch*\
`char_type`으로 나타낼 `int_type` 문자입니다.

### <a name="return-value"></a>반환 값

`int_type` 문자에 해당하는 `char_type` 문자입니다.

*_Ch* 값은 지정 되지 않은 결과를 생성 하는 것으로 나타낼 수 없습니다.

### <a name="remarks"></a>설명

변환 작업 [to_int_type](#to_int_type) 및 `to_char_type`은 서로 역수이므로 다음이 성립합니다.

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

위의 식은 임의의 `int_type` *x* 에 대해 적용되고,

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

위의 식은 임의의 `char_type` *x* 에 대해 적용됩니다.

### <a name="example"></a>예제

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="char_traitsto_int_type"></a><a name="to_int_type"></a> char_traits:: to_int_type

`char_type` 문자를 해당하는 `int_type` 문자로 변환하고 결과를 반환합니다.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>매개 변수

*_Ch*\
`int_type`으로 나타낼 `char_type` 문자입니다.

### <a name="return-value"></a>반환 값

`char_type` 문자에 해당하는 `int_type` 문자입니다.

### <a name="remarks"></a>설명

변환 작업 `to_int_type` 및 [to_char_type](#to_char_type)은 서로 역수이므로 다음이 성립합니다.

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

모든 `int_type` *x*, 및의 경우

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

위의 식은 임의의 `char_type` *x* 에 대해 적용됩니다.

### <a name="example"></a>예제

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
