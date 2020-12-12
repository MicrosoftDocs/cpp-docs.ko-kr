---
description: '자세한 정보: bitset 클래스'
title: bitset 클래스
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: 061bbe77a701e2161b3a33ffa94d3b8231b9f541
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325467"
---
# <a name="bitset-class"></a>bitset 클래스

일련의 항목 또는 조건에 대한 플래그를 유지하는 간단한 방법을 제공하는 고정 비트 수로 구성된 시퀀스를 저장하는 개체의 유형에 대해 설명합니다. bitset 클래스에서는 비트 컬렉션을 포함하고 각 비트에 대한 constant-time 액세스 권한을 제공하는 형식 bitset의 개체에 대한 작업을 지원합니다.

## <a name="syntax"></a>구문

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>매개 변수

*개의*\
컴파일 타임에 알려진 형식의 0이 아닌 정수를 사용 하 여 bitset 개체의 비트 수를 지정 합니다 `size_t` .

## <a name="remarks"></a>설명

유사한 [vector \<bool> 클래스](../standard-library/vector-bool-class.md)와 달리 bitset 클래스는 반복기를 포함 하지 않으며 c + + 표준 라이브러리 컨테이너가 아닙니다. 또한 \<bool> **\<N\> bitset** 가 선언 될 때 템플릿 매개 변수 *N* 으로 지정 된 크기에 따라 컴파일 시에 고정 되는 특정 크기가 벡터와 다릅니다.

비트는 값이 1이면 설정되고, 값이 0이면 재설정 합니다. 비트를 대칭 이동하거나 반전한다는 것은 값을 1에서 0 또는 0에서 1로 변경하는 것입니다. bitset의 *N* 비트는 0에서 *N*-1 범위의 정수 값으로 인덱싱되며, 여기서 0은 첫 번째 비트 위치를 인덱싱하고 *N*-1은 최종 비트 위치를 인덱싱합니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[bitset](#bitset)|클래스 `bitset\<N>`의 개체를 생성하고 비트를 0, 지정된 일부 값 또는 문자열의 문자에서 얻은 값으로 초기화합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[element_type](#element_type)|데이터 형식에 대 한 동의어이 **`bool`** 고에서 요소 비트를 참조 하는 데 사용할 수 있는 형식입니다 `bitset` .|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[모두가](#all)|이의 모든 비트를 테스트 `bitset` 하 여 모두로 설정 되었는지 여부를 확인 **`true`** 합니다.|
|[일부](#any)|멤버 함수는 시퀀스의 모든 비트가 1로 설정되었는지 여부를 테스트합니다.|
|[count](#count)|멤버 함수는 비트 시퀀스에 설정된 비트 수를 반환합니다.|
|[flip](#flip)|`bitset`에 있는 모든 비트의 값을 반전하거나 지정된 위치에서 단일 비트를 반전합니다.|
|[없음](#none)|`bitset` 개체에서 1로 설정된 비트가 없는지 테스트합니다.|
|[reset](#reset)|`bitset`에 있는 모든 비트를 0으로 재설정하거나 지정된 위치의 비트를 0으로 재설정합니다.|
|[set](#set)|`bitset`에 있는 모든 비트를 1로 설정하거나 지정된 위치의 비트를 1로 설정합니다.|
|[size](#size)|`bitset` 개체의 비트 수를 반환합니다.|
|[테스트](#test).|`bitset`에서 지정된 위치의 비트가 1로 설정되어 있는지 테스트합니다.|
|[to_string](#to_string)|`bitset` 개체를 문자열 표현으로 변환합니다.|
|[to_ullong](#to_ullong)|에 있는 비트 값의 합계를로 반환 합니다 `bitset` **`unsigned long long`** .|
|[to_ulong](#to_ulong)|개체를을 `bitset` **`unsigned long`** 초기화 하는 데 사용 되는 경우 포함 된 비트 시퀀스를 생성할로 변환 합니다 `bitset` .|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[reference](#reference)|`bitset`의 `operator[]`에 대한 도우미 클래스로서 개별 비트에 액세스하고 조작하는 데 사용되는 `bitset`에 포함된 비트를 참조하는 프록시 클래스입니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](#op_neq)|지정한 `bitset`와 다른지 알기 위해 대상 `bitset`을 테스트합니다.|
|[연산자&=](#op_and_eq)|논리적 `AND` 작업과 bitsets의 비트 조합을 수행합니다.|
|[연산자<<](#op_lshift)|왼쪽의 `bitset`에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 새 `bitset`에 반환합니다.|
|[연산자<<=](#op_lshift_eq)|왼쪽의 `bitset`에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 대상으로 지정된 `bitset`에 반환합니다.|
|[연산자 = =](#op_eq_eq)|지정한 `bitset`와 같은지 알기 위해 대상 `bitset`을 테스트합니다.|
|[연산자>>](#op_rshift)|오른쪽의 `bitset`에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 새 `bitset`에 반환합니다.|
|[연산자>>=](#op_rshift_eq)|오른쪽의 `bitset`에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 대상으로 지정된 `bitset`에 반환합니다.|
|[operator&#91;&#93;](#op_at)|`bitset`을 수정할 수 있을 경우 `bitset`에서 지정된 위치의 비트에 대한 참조를 반환하고, 그렇지 않으면 해당 위치서 비트 값을 반환합니다.|
|[operator ^ =](#op_xor_eq)|배타적 `OR` 작업과 bitsets의 비트 조합을 수행합니다.|
|[연산자&#124;=](#op_or_eq)|포괄적 `OR` 작업과 bitsets의 비트 조합을 수행합니다.|
|[연산자 ~](#op_not)|대상 `bitset`의 모든 비트를 반전하고 결과를 반환합니다.|

### <a name="structures"></a>구조체

|Name|설명|
|-|-|
|[hash](#hash)||

### <a name="all"></a><a name="all"></a> 모두가

이 bitset의 모든 비트를 테스트하여 모두 true로 설정되었는지 확인합니다.

```cpp
bool all() const;
```

#### <a name="return-value"></a>반환 값

이 집합의 모든 비트가 true이면 true를 반환합니다. **`false`** 하나 이상의 비트가 false 이면를 반환 합니다.

### <a name="any"></a><a name="any"></a> 일부

시퀀스의 모든 비트가 1로 설정되어 있는지를 테스트합니다.

```cpp
bool any() const;
```

#### <a name="return-value"></a>반환 값

**`true`** bitset의 비트가 1로 설정 되어 있으면이 고, 그렇지 않으면입니다. **`false`** 모든 비트가 0 이면입니다.

#### <a name="example"></a>예제

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a><a name="bitset"></a> bitset

클래스 `bitset\<N>`의 개체를 생성하고 비트를 0, 지정된 일부 값 또는 문자열의 문자에서 얻은 값으로 초기화합니다.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>매개 변수

*짧은*\
생성 중인 bitset의 비트를 초기화하기 위해 두 개의 기본 표현이 사용되는 부호 없는 정수입니다.

*문자열*\
bitset 비트 값을 초기화하는 데 사용되는 0과 1의 문자열입니다.

*_CStr*\
bitset 비트 값을 초기화하는 데 사용되는 0과 1의 C 스타일 문자열입니다.

*_Pos*\
문자열에서 문자의 위치이며, 0에서 시작하고 왼쪽에서 오른쪽으로 계산되고 bitset의 첫 번째 비트를 초기화하는 데 사용됩니다.

*수*\
bitset의 비트에 초기 값을 제공하는 데 사용되는 문자열의 문자 수입니다.

*_Zero*\
0을 나타내는 데 사용되는 문자입니다. 기본값은 ‘0’입니다.

*_One*\
1을 나타내는 데 사용되는 문자입니다. 기본값은 ‘1’입니다.

#### <a name="remarks"></a>설명

세 가지 생성자를 사용하여 `bitset\<N>` 클래스의 개체를 생성할 수 있습니다.

- 첫 번째 생성자는 매개 변수를 허용하지 않고, `bitset\<N>` 클래스의 개체를 생성하며, 모든 N 비트를 기본값 0으로 초기화합니다.

- 두 번째 생성자는 클래스의 개체를 생성 하 `bitset\<N>` 고 단일 매개 변수를 사용 하 여 비트를 초기화 합니다 **`unsigned long long`** .

- 세 번째 생성자는 `bitset\<N>` 클래스의 개체를 생성하여, 0과 1의 C 스타일 문자열로 제공된 문자에 해당하는 값으로 N 비트를 초기화합니다. 문자열을 `bitset<5> b5("01011");` 문자열 형식으로 전환하지 않고 생성자를 호출합니다.

제공된 두 개의 생성자 템플릿이 있습니다.

- 첫 번째 생성자 템플릿은 `bitset\<N>` 클래스의 개체를 구성하고 0과 1의 문자열로 제공된 문자에서 비트를 초기화합니다. 문자열에 0 또는 1이 아닌 문자가 있는 경우 생성자는 [잘못된 인수](../standard-library/invalid-argument-class.md) 클래스의 개체를 throw합니다. 지정 된 위치 (*_Pos*)가 문자열의 길이를 초과 하는 경우 생성자는 [out_of_range](../standard-library/out-of-range-class.md)클래스의 개체를 throw 합니다. 생성자는 `_Pos + j` 위치에 있는 문자열의 문자가 1인 bitset에서 *j* 위치에 있는 비트만 설정합니다. 기본적으로 *_Pos* 는 0입니다.

- 두 번째 생성자 템플릿은 첫 번째 생성자와 비슷하지만 초기화할 비트 수를 지정 하는 데 사용 되는 추가 매개 변수 (*개수*)를 포함 합니다. 또한 두 개의 선택적 매개 변수 *_Zero* 및 *_One* 있습니다 .이 매개 변수는 *str* 에서 각각 0 비트와 1 비트를 의미 하는 문자를 의미 하는 문자를 표시 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a><a name="count"></a> 수

비트 시퀀스에 설정된 비트 수를 반환합니다.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>반환 값

비트 시퀀스에 설정된 비트 수입니다.

#### <a name="example"></a>예제

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a><a name="element_type"></a> element_type

데이터 형식에 대 한 동의어이 **`bool`** 고 bitset의 요소 비트를 참조 하는 데 사용할 수 있는 형식입니다.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>예제

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a><a name="flip"></a> 넘김

bitset에 있는 모든 비트의 값을 반전하거나 지정된 위치에서 단일 비트를 반전합니다.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
값이 반전될 비트의 위치입니다.

#### <a name="return-value"></a>반환 값

멤버 함수가 호출된, 수정된 bitset의 복사본입니다.

#### <a name="remarks"></a>설명

매개 변수로 지정 된 위치가 비트가 반전 된 **bitset \<** *N* **>** 의 *N* 크기 보다 큰 경우 두 번째 멤버 함수는 [out_of_range](../standard-library/out-of-range-class.md) 예외를 throw 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a><a name="hash"></a> 해시로

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a><a name="none"></a> 없음을

bitset 개체에서 1로 설정된 비트가 없는지 테스트합니다.

```cpp
bool none() const;
```

#### <a name="return-value"></a>반환 값

**`true`** bitset의 비트가 1로 설정 되지 않은 경우 **`false`** 하나 이상의 비트가 1로 설정 된 경우

#### <a name="example"></a>예제

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="operator"></a><a name="op_neq"></a> 연산자! =

대상 bitset가 지정된 bitset와 다른지를 테스트합니다.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 bitset와 다른지를 비교할 bitset입니다.

#### <a name="return-value"></a>반환 값

**`true`** bitset가 다른 경우 같으면 **`false`** 이 고, 그렇지 않으면입니다.

#### <a name="remarks"></a>설명

멤버 연산자 함수로 다른지를 테스트하려면 두 bitset의 크기가 같아야 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatoramp"></a><a name="op_and_eq"></a> 연산자&amp;=

논리적 `AND` 작업과 bitsets의 비트 조합을 수행합니다.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 bitset와 비트로 결합할 bitset입니다.

#### <a name="return-value"></a>반환 값

비트 `AND` 연산에서 매개 변수로 지정 된 bitset로 생성 되는 수정 된 대상 bitset입니다.

#### <a name="remarks"></a>설명

연산자에 의해 결합 된 두 비트 `AND` **`true`** 는 각 비트가 true 이면를 반환 하 고, 그렇지 않으면 조합에서을 반환 **`false`** 합니다.

Bitsets의 크기는 `AND` 멤버 연산자 함수에 의해 연산자와 비트 조합으로 결합 되어야 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_lshift"></a> 연산자\<\<

왼쪽의 bitset에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 새 bitset로 반환합니다.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
bitset에 있는 비트를 이동해야 할 왼쪽에 있는 위치의 수입니다.

#### <a name="return-value"></a>반환 값

필요한 위치 수만큼 왼쪽으로 이동한 비트가 있는 수정된 bitset입니다.

#### <a name="remarks"></a>설명

멤버 연산자 함수는 **bitset**( **\* this**) **<<= pos를** 반환 합니다 [<<=](#op_lshift_eq) . 여기서 bitset의 비트를 지정 된 위치 수 만큼 왼쪽으로 이동 하 고 결과를 대상 bitset로 반환 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="operatorltlt"></a><a name="op_lshift_eq"></a> 연산자&lt;&lt;=

bitset에 있는 비트를 지정된 위치 수만큼 왼쪽으로 이동하고 결과를 대상으로 지정된 bitset로 반환합니다.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
bitset에 있는 비트를 이동해야 할 왼쪽에 있는 위치의 수입니다.

#### <a name="return-value"></a>반환 값

필요한 위치 수만큼 비트가 왼쪽으로 이동하도록 수정된 대상 bitset입니다.

#### <a name="remarks"></a>설명

위치로 이동할 요소가 없으면 함수는 비트를 0 값으로 지웁니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

대상 bitset가 지정된 bitset와 같은지를 테스트합니다.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 bitset와 같은지를 비교할 bitset입니다.

#### <a name="return-value"></a>반환 값

**`true`** bitset가 동일 하면이 고, **`false`** 다른 경우입니다.

#### <a name="remarks"></a>설명

멤버 연산자 함수로 같은지를 테스트하려면 두 bitset의 크기가 같아야 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatorgtgt"></a><a name="op_rshift"></a> 연산자&gt;&gt;

오른쪽의 bitset에 있는 비트를 지정된 위치 수만큼 이동하고 결과를 새 bitset로 반환합니다.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
bitset에 있는 비트를 이동해야 할 오른쪽에 있는 위치의 수입니다.

#### <a name="return-value"></a>반환 값

대상 bitset를 기준으로 비트가 필요한 위치 수만큼 오른쪽으로 이동한 새 bitset입니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="operatorgtgt"></a><a name="op_rshift_eq"></a> 연산자&gt;&gt;=

bitset에 있는 비트를 지정된 위치 수만큼 오른쪽으로 이동하고 결과를 대상으로 지정된 bitset로 반환합니다.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
bitset에 있는 비트를 이동해야 할 오른쪽에 있는 위치의 수입니다.

#### <a name="return-value"></a>반환 값

필요한 위치 수만큼 비트가 오른쪽으로 이동하도록 수정된 대상 bitset입니다.

#### <a name="remarks"></a>설명

위치로 이동할 요소가 없으면 함수는 비트를 0 값으로 지웁니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="operator"></a><a name="op_at"></a> operator[]

bitset를 수정할 수 있는 경우 bitset 내 지정된 위치의 비트에 대한 참조를 반환하고, 수정할 수 없는 경우 해당 위치의 비트 값을 반환합니다.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
bitset 내에서 비트를 찾는 위치입니다.

#### <a name="remarks"></a>설명

빌드에서 [ \_ 반복기 \_ 디버그 \_ 수준을](../standard-library/iterator-debug-level.md) 1 또는 2로 정의 하면 bitset 범위 밖의 요소에 액세스 하려고 할 때 실행 파일에서 런타임 오류가 발생 합니다. 자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

#### <a name="example"></a>예제

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="operator"></a><a name="op_xor_eq"></a> operator ^ =

배타적 `OR` 작업과 bitsets의 비트 조합을 수행합니다.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 bitset와 비트로 결합할 bitset입니다.

#### <a name="return-value"></a>반환 값

매개 변수로 지정된 bitset와 배타적 비트 `OR` 연산을 수행한 결과인 수정된 대상 bitset입니다.

#### <a name="remarks"></a>설명

두 비트 중 하나 이상이 아닌 경우 배타적 **OR** 연산자로 결합 된 두 비트가 반환 **`true`** 되 **`true`** 고, 그렇지 않으면 조합이 반환 **`false`** 됩니다.

멤버 연산자 함수를 이용해 배타적 `OR` 연산자와 비트로 결합하려면 두 bitset의 크기가 같아야 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator124"></a><a name="op_or_eq"></a> 연산자&#124;=

포괄적 `OR` 작업과 bitsets의 비트 조합을 수행합니다.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 bitset와 비트로 결합할 bitset입니다.

#### <a name="return-value"></a>반환 값

매개 변수로 지정된 bitset와 포괄적 비트 `OR` 연산을 수행한 결과인 수정된 대상 bitset입니다.

#### <a name="remarks"></a>설명

포함 연산자에 의해 결합 된 두 비트는 `OR` **`true`** 비트 중 하나 이상이 이면를 반환 하 고, **`true`** 두 비트가 모두 이면 **`false`** 조합에서을 반환 **`false`** 합니다.

멤버 연산자 함수를 이용해 포괄적 `OR` 연산자와 비트로 결합하려면 두 bitset의 크기가 같아야 합니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_not"></a> 연산자 ~

대상 bitset의 모든 비트를 반전하고 결과를 반환합니다.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>반환 값

대상 bitset에 대해 모든 비트가 반전된 bitset입니다.

#### <a name="example"></a>예제

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a><a name="reference"></a> 참조일

bitset 클래스의 `operator[]`에 대한 도우미 클래스로서 개별 비트에 액세스하고 조작하는 데 사용되는 bitset에 포함된 비트를 참조하는 프록시 클래스입니다.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>매개 변수

*짧은*\
**`bool`** Bitset의 비트에 할당할 형식의 개체 값입니다.

*_Bitref*\
*x* bitset의 *i* 위치에 있는 비트에 대한 *x [ i ]* 형식의 참조입니다.

#### <a name="return-value"></a>반환 값

클래스 참조의 첫 번째, 두 번째 및 다섯 번째 멤버 함수에 대 한 인수 위치로 지정 된 bitset의 비트에 대 한 참조이 **`true`** 고 **`false`** , 또는 클래스 참조의 세 번째 및 네 번째 멤버 함수에 대 한 bitset의 수정 된 비트 값을 반영 하기 위해 또는입니다.

#### <a name="remarks"></a>설명

`reference` 클래스는 `operator[]` bitset에 대한 도우미 클래스로서만 존재합니다. 멤버 클래스는 bitset 내 개별 비트에 액세스할 수 있는 개체를 설명합니다. *B* 는 **`bool`** **bitset \<** *N* **>** 형식의 *x* 및 *y* 개체와 해당 개체 내에서 *i* 및 *j* 유효한 위치 형식의 개체를 사용 합니다. *x [i]* 표기법은 *x* bitset 내 *i* 위치에 있는 비트를 참조합니다. `reference` 클래스의 멤버 함수는 다음 연산을 차례로 제공합니다.

|연산|정의|
|---------------|----------------|
|*x*[*i*] = *b*|**`bool`** 값 *b* 를 bitset x  의 비트 위치에 저장 합니다.|
|*x*[*i*] = *y*[*j*]|*y*[ *j*] 비트의 값을 *x* bitset 내 *i* 비트 위치에 저장합니다.|
|*b* = ~ *x*[*i*]|*X*[ *i*] 비트의 대칭 이동 된 값을 **`bool`** *b* 에 저장 합니다.|
|*b*  =  *x*[*i*]|B의 비트 *x*[ *i*] 값을 저장 **`bool`** 합니다.|
|*x*[*i*]. `flip`( )|*x*[ *i*] 비트의 대칭 이동된 값을 *x* 내 *i* 비트 위치에 다시 저장합니다.|

#### <a name="example"></a>예제

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a><a name="reset"></a> 다시 설정

bitset에 있는 모든 비트를 0으로 다시 설정하거나 지정된 위치의 비트를 0으로 다시 설정합니다.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
값을 0으로 다시 설정할 bitset 내 비트의 위치입니다.

#### <a name="return-value"></a>반환 값

멤버 함수가 호출된 bitset의 복사본입니다.

#### <a name="remarks"></a>설명

지정된 위치가 bitset의 크기보다 큰 경우 두 번째 멤버 함수는 [out_of_range](../standard-library/out-of-range-class.md) 예외를 throw합니다.

#### <a name="example"></a>예제

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a><a name="set"></a> 설정

bitset에 있는 모든 비트를 1로 설정하거나 지정된 위치의 비트를 1로 설정합니다.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
값을 할당하도록 설정할 bitset 내 비트의 위치입니다.

*짧은*\
지정된 위치에 있는 비트에 할당할 값입니다.

#### <a name="return-value"></a>반환 값

멤버 함수가 호출된 bitset의 복사본입니다.

#### <a name="remarks"></a>설명

지정된 위치가 bitset의 크기보다 큰 경우 두 번째 멤버 함수는 [out_of_range](../standard-library/out-of-range-class.md) 예외를 throw합니다.

#### <a name="example"></a>예제

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a><a name="size"></a> 크기가

bitset 개체의 비트 수를 반환합니다.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>반환 값

Bitset의 비트 수 ( *N*)입니다 \<N> .

#### <a name="example"></a>예제

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a><a name="test"></a> 테스트할

bitset에서 지정된 위치의 비트가 1로 설정되어 있는지 테스트합니다.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>매개 변수

*_Pos*\
값을 테스트할 bitset 내 비트의 위치입니다.

#### <a name="return-value"></a>반환 값

**`true`** 인수 위치로 지정 된 비트가 1로 설정 된 경우 그렇지 않으면 **`false`** 입니다.

#### <a name="remarks"></a>설명

멤버 함수는 [out_of_range](../standard-library/out-of-range-class.md)를 throw합니다.

### <a name="to_string"></a><a name="to_string"></a> to_string

Bitset 개체를 문자열 표현으로 변환 합니다.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>반환 값

`basic_string`Bitset에 설정 된 각 비트의 해당 문자가 1이 고, 비트가 설정 되지 않은 경우 0의 문자가 있는 클래스의 문자열 개체입니다.

#### <a name="example"></a>예제

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a><a name="to_ullong"></a> to_ullong

**`unsigned long long`** Bitset 개체의 내용과 동일한 비트가 설정 된 값을 반환 합니다.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>반환 값

비트 시퀀스에 있는 비트 값의 합계를로 반환 합니다 **`unsigned long long`** . **`unsigned long long`** Bitset를 초기화 하는 데 사용 되는 경우이 값은 동일한 집합 비트를 다시 만듭니다.

#### <a name="exceptions"></a>예외

비트 시퀀스의 비트에 형식 값으로 표현할 수 없는 비트 값이 있는 경우 [overflow_error](overflow-error-class.md) 개체를 throw **`unsigned long long`** 합니다.

#### <a name="remarks"></a>설명

비트 시퀀스에 있는 비트 값의 합계를로 반환 합니다 **`unsigned long long`** .

### <a name="to_ulong"></a><a name="to_ulong"></a> to_ulong

Bitset 개체를 bitset를 초기화 하는 데 사용 되는 경우 포함 된 비트 시퀀스를 생성 하는 정수로 변환 합니다.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>반환 값

Bitset의 초기화에 사용 되는 경우 bitset에서 비트를 생성 하는 정수입니다.

#### <a name="remarks"></a>설명

멤버 함수를 적용 하면 bitset에 포함 된 비트 시퀀스에 있는 것과 동일한 시퀀스 1과 0을 포함 하는 정수를 반환 합니다.

비트 시퀀스의 비트에 형식 값으로 표현할 수 없는 비트 값이 있는 경우 멤버 함수는 [overflow_error](overflow-error-class.md) 개체를 throw 합니다 **`unsigned long`** .

#### <a name="example"></a>예제

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
