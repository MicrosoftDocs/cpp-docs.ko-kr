---
title: ostream_iterator 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c166b39a6252c3b49427f06d88c179bd9ca25ce8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108334"
---
# <a name="ostreamiterator-class"></a>ostream_iterator 클래스

템플릿 클래스 ostream_iterator는 연속 요소를 추출 출력 스트림에 쓰는 출력 반복기 개체를 설명 `operator <<`합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>매개 변수

*Type*<br/>
출력 스트림에 삽입될 개체의 형식입니다.

*CharType*<br/>
`ostream_iterator`의 문자 형식을 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 **char**합니다.

*특성*<br/>
`ostream_iterator`의 문자 형식을 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `char_traits`\< *CharType>입니다.*

ostream_iterator 클래스는 출력 반복기에 대한 요구 사항을 충족해야 합니다. 알고리즘은 `ostream_iterator`를 사용하여 출력 스트림에 직접 쓸 수 있습니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[ostream_iterator](#ostream_iterator)|출력 스트림으로 쓰도록 초기화 및 구분된 `ostream_iterator`를 구성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|`ostream_iterator`의 문자 형식을 허용하는 형식입니다.|
|[ostream_type](#ostream_type)|`ostream_iterator`의 스트림 형식을 허용하는 형식입니다.|
|[traits_type](#traits_type)|`ostream_iterator`의 특성 형식을 허용하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator*](#op_star)|출력 반복기 식을 구현 하는 데 사용 된 역참조 연산자 \* `i`  =  `x`합니다.|
|[operator++](#op_add_add)|연산이 호출되기 전에 주소 지정한 동일한 개체에 `ostream_iterator`를 반환한 비함수 증분 연산자.|
|[operator=](#op_eq)|출력 반복기 식을 구현 하는 데 사용 되는 대입 연산자 \* `i`  =  `x` 출력 스트림에 작성 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<iterator>

**네임스페이스:** std

## <a name="char_type"></a>  ostream_iterator::char_type

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
\* Output:
The integers written to the output stream
by intOut are:
10
20
30
*\
```

## <a name="op_star"></a>  ostream_iterator::operator*

출력 반복기 식 \* *ii* = *x*를 구현하는 데 사용된 역참조 연산자.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>반환 값

`ostream_iterator`에 대한 참조입니다.

### <a name="remarks"></a>설명

`ostream_iterator`가 충족해야 하는 출력 반복기에 대한 요구 사항은 \* *ii* = *t* 식만 유효해야 한다는 것과 해당 반복기 자체는 **operator** 또는 `operator=`에 대해 어떤 정보도 제공하지 않아야 한다는 것입니다. 이 구현에서는 구성원 연산자가 **\*this**를 반환합니다.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_add_add"></a>  ostream_iterator::operator++

연산이 호출되기 전에 주소 지정한 동일한 개체에 `ostream_iterator`를 반환한 비함수 증분 연산자.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>반환 값

`ostream_iterator`에 대한 참조입니다.

### <a name="remarks"></a>설명

이러한 구성원 연산자는 둘 다 **\*this**를 반환합니다.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_eq"></a>  ostream_iterator::operator=

출력 반복기 식을 구현 하는 데 사용 되는 할당 연산자 \* `i`  =  `x` 출력 스트림에 작성 합니다.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>매개 변수

*val*<br/>
출력 스트림에 삽입될 `Type` 형식의 개체 값입니다.

### <a name="return-value"></a>반환 값

연산자 삽입 *val* 뒤에 지정 된 구분 기호를 개체에 연결 된 출력 스트림에 [ostream_iterator 생성자](#ostream_iterator) (있는 경우), 다음을 에대한참조를반환합니다`ostream_iterator`.

### <a name="remarks"></a>설명

출력 반복기에 대 한 요구 사항을 하는 `ostream_iterator` 충족 해야 합니다 식만 \* `ii`  =  `t` 유효 하 고 연산자 또는 연산자에 대해 아무런 언급이 자체적으로 =. 이 구성원 연산자는 `*this`를 반환합니다.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="ostream_iterator"></a>  ostream_iterator::ostream_iterator

출력 스트림으로 쓰도록 초기화 및 구분된 `ostream_iterator`를 구성합니다.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>매개 변수

*_Ostr*<br/>
반복할 [ostream_iterator::ostream_type](#ostream_type) 형식의 출력 스트림입니다.

*(_D)*<br/>
출력 스트림에서 값 사이에 삽입되는 구분 기호입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `&_Ostr`로 출력 스트림 포인터를 초기화합니다. 구분 기호 문자열 포인터는 빈 문자열을 지정합니다.

두 번째 생성자는 출력 스트림 포인터를 사용 하 여 초기화 `&_Ostr` 하 고 사용 하 여 구분 기호 문자열 포인터 *(_d)* 합니다.

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
\* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*\
```

## <a name="ostream_type"></a>  ostream_iterator::ostream_type

반복기의 스트림 형식을 제공하는 형식입니다.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>설명

이 형식은 쓰기에 사용할 수 있는 개체를 정의하는 iostream 계층의 스트림 클래스인 [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>와 동일한 의미입니다.

### <a name="example"></a>예제

`ostream_type`을 선언하고 사용하는 방법의 예제는 [ostream_iterator](#ostream_iterator)를 참조하세요.

## <a name="traits_type"></a>  ostream_iterator::traits_type

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
\* Output:
The integers written to output stream
by intOut are:
1
10
100
*\
```

## <a name="see-also"></a>참고자료

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
