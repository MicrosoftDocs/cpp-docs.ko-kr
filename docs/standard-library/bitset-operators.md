---
description: '자세한 정보: &lt; bitset &gt; 연산자'
title: '&lt;bitset&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: 5157b3e8a8fa94152a4a2446b1d9a4c124677ddd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325453"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 연산자

## <a name="operatoramp"></a><a name="op_amp"></a> 연산자&amp;

두 bitset 간에 비트 `AND`를 수행합니다.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
각각의 요소를 비트 `AND`로 결합할 두 bitset 중 첫 번째입니다.

*오른쪽*\
각각의 요소를 비트 `AND`로 결합할 두 valarray 중 두 번째입니다.

### <a name="return-value"></a>반환 값

요소가 `AND` *left* 및 *right* 의 해당 요소에 대 한 작업을 수행한 결과인 bitset입니다.

### <a name="example"></a>예제

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

비트 시퀀스의 텍스트 표현을 출력 스트림에 삽입합니다.

```cpp
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
출력 스트림에 문자열로 삽입할 **bitset \<N>** 형식의 개체입니다.

### <a name="return-value"></a>반환 값

에 있는 비트 시퀀스의 텍스트 표현 `ostr` 입니다.

### <a name="remarks"></a>설명

템플릿 함수 오버 로드를 사용 하 여 `operator<<` bitset을 먼저 문자열로 변환 하지 않고 기록할 수 있습니다. 템플릿 함수는 다음을 효과적으로 실행합니다.

`ostr << right.`[to_string](bitset-class.md)`<CharType, Traits, allocator<CharType>>()`

### <a name="example"></a>예제

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a> 연산자&gt;&gt;

bitset에 대한 비트 문자의 문자열을 읽습니다.

```cpp
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& i_str,
    bitset<N>& right);
```

### <a name="parameters"></a>매개 변수

*i_str*\
bitset에 삽입할 입력 스트림에 입력되는 문자열입니다.

*오른쪽*\
입력 스트림에서 비트를 수신하는 bitset입니다.

### <a name="return-value"></a>반환 값

템플릿 함수는 *i_str* 문자열을 반환 합니다.

### <a name="remarks"></a>설명

Bitset에 저장 되는 템플릿 함수 오버 로드는 `operator>>` 값을 *오른쪽* 으로 설정 합니다 `bitset(str)` `str` . 여기서는 [](basic-string-class.md) `< CharType, Traits, allocator< CharType > >&` *i_str* 에서 추출 된 basic_string 형식의 개체입니다.

템플릿 함수는 *i_str* 에서 요소를 추출 하 여 다음이 될 때까지 bitset에 삽입 합니다.

- 모든 비트 요소가 입력 스트림에서 추출되어 bitset에 저장될 때까지

- bitset가 입력 스트림의 비트로 채워질 때까지

- 0 또는 1이 아닌 입력 요소가 발견될 때까지

### <a name="example"></a>예제

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="operator"></a><a name="op_xor"></a> operator ^

두 bitset 간에 비트 `EXCLUSIVE-OR`를 수행합니다.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
각각의 요소를 비트 `EXCLUSIVE-OR`로 결합할 두 bitset 중 첫 번째입니다.

*오른쪽*\
각각의 요소를 비트 `EXCLUSIVE-OR`로 결합할 두 valarray 중 두 번째입니다.

### <a name="return-value"></a>반환 값

요소가 `EXCLUSIVE-OR` *left* 및 *right* 의 해당 요소에 대 한 작업을 수행한 결과인 bitset입니다.

### <a name="example"></a>예제

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="operator124"></a><a name="op_or"></a> 연산자&#124;

두 bitset 간에 비트 `OR`를 수행합니다.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
각각의 요소를 비트 `OR`로 결합할 두 bitset 중 첫 번째입니다.

*오른쪽*\
각각의 요소를 비트 `OR`로 결합할 두 valarray 중 두 번째입니다.

### <a name="return-value"></a>반환 값

요소가 `OR` *left* 및 *right* 의 해당 요소에 대 한 작업을 수행한 결과인 bitset입니다.

### <a name="example"></a>예제

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
