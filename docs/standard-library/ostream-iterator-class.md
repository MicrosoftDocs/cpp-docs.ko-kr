---
description: Ostream_iterator 클래스에 대해 자세히 알아보세요.
title: ostream_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: 2123c2a9addb5024877364a1906800b244b91edb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118370"
---
# <a name="ostream_iterator-class"></a>ostream_iterator 클래스

클래스 템플릿은 연속 요소를 추출 하 여 출력 스트림에 쓰는 출력 반복기 개체를 설명 ostream_iterator 합니다 `operator <<` .

## <a name="syntax"></a>구문

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>매개 변수

*입력할*\
출력 스트림에 삽입될 개체의 형식입니다.

*CharType*\
`ostream_iterator`의 문자 형식을 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 **`char`** 입니다.

*특징이*\
`ostream_iterator`의 문자 형식을 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 `char_traits` \< *CharType> . *입니다.

ostream_iterator 클래스는 출력 반복기에 대한 요구 사항을 충족해야 합니다. 알고리즘은 `ostream_iterator`를 사용하여 출력 스트림에 직접 쓸 수 있습니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[ostream_iterator](#ostream_iterator)|출력 스트림으로 쓰도록 초기화 및 구분된 `ostream_iterator`를 구성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|`ostream_iterator`의 문자 형식을 허용하는 형식입니다.|
|[ostream_type](#ostream_type)|`ostream_iterator`의 스트림 형식을 허용하는 형식입니다.|
|[traits_type](#traits_type)|`ostream_iterator`의 특성 형식을 허용하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자](#op_star)|출력 반복기 식을 구현 하는 데 사용 되는 역참조 연산자 \* `i`  =  `x` 입니다.|
|[operator + +](#op_add_add)|연산이 호출되기 전에 주소 지정한 동일한 개체에 `ostream_iterator`를 반환한 비함수 증분 연산자.|
|[연산자 =](#op_eq)|\* `i`  =  출력 스트림에 쓰기 위해 출력 반복기 식을 구현 하는 데 사용 되는 할당 연산자 `x` 입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a> ostream_iterator:: char_type

반복기의 문자 형식을 제공하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `CharType`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a> ostream_iterator:: operator *

출력 반복기 식 ii x를 구현 하는 데 사용 되는 역참조 연산자 \*   =  입니다.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>반환 값

`ostream_iterator`에 대한 참조입니다.

### <a name="remarks"></a>설명

에서 충족 해야 하는 출력 반복기에 대 한 요구 사항에는 `ostream_iterator` ii t 식만 유효 해야 하 \*   =   고 **`operator`** 또는 자체에는 아무 것도 표시 되지 않습니다 `operator=` . 이 구현에서 멤버 연산자는 **\* this** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a> ostream_iterator:: operator + +

연산이 호출되기 전에 주소 지정한 동일한 개체에 `ostream_iterator`를 반환한 비함수 증분 연산자.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>반환 값

`ostream_iterator`에 대한 참조입니다.

### <a name="remarks"></a>설명

이러한 멤버 연산자는 모두 **\* this** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a> ostream_iterator:: operator =

\* `i`  =  출력 스트림에 쓰기 위해 output_iterator 식을 구현 하는 데 사용 되는 할당 연산자 `x` 입니다.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
출력 스트림에 삽입될 `Type` 형식의 개체 값입니다.

### <a name="return-value"></a>반환 값

연산자는 개체와 연결 된 출력 스트림에 *val* 을 삽입 한 다음 [ostream_iterator 생성자](#ostream_iterator) 에 지정 된 구분 기호 (있는 경우)를 입력 하 고에 대 한 참조를 반환 합니다 `ostream_iterator` .

### <a name="remarks"></a>설명

에서 충족 해야 하는 출력 반복기에 대 한 요구 사항에는 `ostream_iterator` 식만 \* `ii`  =  `t` 유효 하 고 연산자 또는 operator =에 대해서는 아무 것도 필요 하지 않습니다. 이 멤버 연산자는 **`*this`** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a> ostream_iterator:: ostream_iterator

출력 스트림으로 쓰도록 초기화 및 구분된 `ostream_iterator`를 구성합니다.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>매개 변수

*_Ostr*\
반복할 [ostream_iterator::ostream_type](#ostream_type) 형식의 출력 스트림입니다.

*_Delimiter*\
출력 스트림에서 값 사이에 삽입되는 구분 기호입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `&_Ostr`로 출력 스트림 포인터를 초기화합니다. 구분 기호 문자열 포인터는 빈 문자열을 지정합니다.

두 번째 생성자는로 출력 스트림 포인터를 초기화 `&_Ostr` 하 고 *_Delimiter* 를 사용 하 여 구분 기호 문자열 포인터를 초기화 합니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a> ostream_iterator:: ostream_type

반복기의 스트림 형식을 제공하는 형식입니다.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>설명

형식은 [](../standard-library/basic-ostream-class.md) <  `CharType` `Traits` 기록에 사용할 수 있는 개체를 정의 하는 iostream 계층의 스트림 클래스인 basic_ostream>의 동의어입니다.

### <a name="example"></a>예제

`ostream_type`을 선언하고 사용하는 방법의 예제는 [ostream_iterator](#ostream_iterator)를 참조하세요.

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a> ostream_iterator:: traits_type

반복기의 특성 형식을 제공하는 형식입니다.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Traits`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
