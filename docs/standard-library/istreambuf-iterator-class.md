---
title: istreambuf_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 41298909b53de1c7acf3cb8ae4b999eb6260765d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448895"
---
# <a name="istreambufiterator-class"></a>istreambuf_iterator 클래스

템플릿 클래스 istreambuf_iterator는 여기에 저장되는 개체를 통해 액세스하는, `basic_streambuf`\< **CharType**, **Traits**>에 대한 형식 포인터의 입력 스트림 버퍼에서 문자 요소를 추출하는 입력 반복기 개체에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>매개 변수

*CharType*<br/>
istreambuf_iterator의 문자 형식을 나타내는 형식입니다.

*특성*<br/>
istreambuf_iterator의 문자 형식을 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `char_traits`\< *CharType>* 입니다.

## <a name="remarks"></a>설명

istreambuf_iterator 클래스는 입력 반복기에 대한 요구 사항을 충족해야 합니다.

null이 아닌 저장된 포인터를 사용하여 istreambuf_iterator 클래스의 개체를 구성하거나 증가시킨 후 개체는 연결된 입력 스트림에서 *CharType* 형식의 개체에 대해 효과적인 추출 및 저장을 시도합니다. 하지만 개체를 실제로 역참조 또는 복사할 때까지 추출이 지연될 수 있습니다. 추출이 실패할 경우 개체는 저장된 포인터를 null 포인터로 대체하여 시퀀스 끝 표시기를 만듭니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|입력 스트림에서 문자를 읽을 수 있도록 초기화된 `istreambuf_iterator`를 만듭니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|`ostreambuf_iterator`의 문자 형식을 허용하는 형식입니다.|
|[int_type](#int_type)|`istreambuf_iterator`의 정수 형식을 허용하는 형식입니다.|
|[istream_type](#istream_type)|`istream_iterator`의 스트림 형식을 허용하는 형식입니다.|
|[streambuf_type](#streambuf_type)|`istreambuf_iterator`의 스트림 형식을 허용하는 형식입니다.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|`istream_iterator`의 특성 형식을 허용하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[equal](#equal)|두 입력 스트림 버퍼 반복기가 같은지 테스트합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator*](#op_star)|역참조 연산자가 스트림의 다음 문자를 반환합니다.|
|[operator++](#op_add_add)|입력 스트림의 다음 문자를 반환하거나 개체를 증가하기 전에 복사하여 복사본을 반환합니다.|
|[operator->](#op_arrow)|멤버의 값을 반환합니다(있는 경우).|

## <a name="requirements"></a>요구 사항

**헤더:** \<iterator>

**네임스페이스:** std

## <a name="char_type"></a>  istreambuf_iterator::char_type

`ostreambuf_iterator`의 문자 형식을 허용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *CharType*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="equal"></a>  istreambuf_iterator::equal

두 입력 스트림 버퍼 반복기가 같은지 테스트합니다.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>매개 변수

*right*<br/>
같은지 확인할 반복기입니다.

### <a name="return-value"></a>반환 값

`istreambuf_iterator`가 둘 다 스트림의 끝 반복기인 경우 또는 둘 다 스트림의 끝 반복기가 아닌 경우 **true**이고, 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

범위를 정의한 합니다 `istreambuf_iterator` 반복기에서 동일 하지만 모든 비-스트림의 끝이 현재 위치를 스트림의 끝 반복기를 `equal` 멤버 함수를 불가능를 사용 하 여 하위 범위를 정의 하 `istreambuf_iterator`s입니다. `==` 및 `!=` 연산자는 의미 체계가 동일합니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="int_type"></a>  istreambuf_iterator::int_type

`istreambuf_iterator`의 정수 형식을 허용하는 형식입니다.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>설명

이 형식은 `Traits::int_type`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istream_type"></a>  istreambuf_iterator::istream_type

`istreambuf_iterator`의 스트림 형식을 허용하는 형식입니다.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>설명

이 형식은 `basic_istream`\< **CharType**, **Traits**>의 동의어입니다.

### <a name="example"></a>예제

`istream_type`을 선언하고 사용하는 방법에 대한 예제는 [istreambuf_iterator](#istreambuf_iterator)를 참조하세요.

## <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator

입력 스트림에서 문자를 읽을 수 있도록 초기화된 istreambuf_iterator를 생성합니다.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>매개 변수

*strbuf*<br/>
`istreambuf_iterator`를 연결 중인 입력 스트림 버퍼입니다.

*_Istr*<br/>
`istreambuf_iterator`를 연결 중인 입력 스트림입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 사용 하 여 입력된 스트림 버퍼 포인터를 초기화 *strbuf*합니다. 두 번째 생성자를 사용 하 여 입력된 스트림 버퍼 포인터를 초기화 *_Istr*합니다. `rdbuf`를 다음 최종적으로 추출 하 고 형식의 개체를 저장 하려고 시도 하 고 `CharType`입니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="op_star"></a>  istreambuf_iterator::operator*

역참조 연산자가 스트림의 다음 문자를 반환합니다.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>반환 값

스트림의 다음 문자입니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="op_add_add"></a>  istreambuf_iterator::operator++

입력 스트림의 다음 문자를 반환하거나 개체를 증가하기 전에 복사하여 복사본을 반환합니다.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>반환 값

`istreambuf_iterator` 또는 `istreambuf_iterator`에 대한 참조입니다.

### <a name="remarks"></a>설명

첫 번째 연산자는 최종적으로 추출 하 고 형식의 개체를 저장 하려고 시도 `CharType` 는 연결 된 입력 스트림에서 합니다. 두 번째 연산자는 개체의 복사본을 만들고 개체를 증가시킨 다음 복사본을 반환합니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="op_arrow"></a>  istreambuf_iterator::operator-&gt;

멤버의 값을 반환합니다(있는 경우).

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>반환 값

이 연산자는 **&\*\*this**를 반환합니다.

## <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type

istreambuf_iterator의 스트림 형식을 제공하는 형식입니다.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>설명

이 형식은 `basic_streambuf`\< **CharType**, **Traits**>의 동의어입니다.

### <a name="example"></a>예제

`istreambuf_type`을 선언하고 사용하는 방법에 대한 예제는 [istreambuf_iterator](#istreambuf_iterator)를 참조하세요.

## <a name="traits_type"></a>  istreambuf_iterator::traits_type

`istream_iterator`의 특성 형식을 허용하는 형식입니다.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *Traits*와 동일한 의미입니다.

### <a name="example"></a>예제

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>참고자료

[iterator 구조체](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
