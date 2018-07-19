---
title: istream_iterator 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e41abbc4d7fa3cd18363982b806811b0698b44f4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959870"
---
# <a name="istreamiterator-class"></a>istream_iterator 클래스

입력 반복기 개체에 대해 설명합니다. 여기에 저장되는 개체를 통해 액세스하는, `basic_istream`< `CharType`, `Traits`>에 대한 형식 `pointer`의 입력 스트림에서 `Type` 클래스의 개체를 추출합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
 : public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>매개 변수

*형식* 입력 스트림에서 추출할 개체의 형식입니다.

*CharType* 의 문자 형식을 나타내는 형식입니다는 `istream_iterator`합니다. 이 인수는 선택 사항이 며 기본값은 **char**합니다.

*Traits* 의 문자 형식을 나타내는 형식입니다는 `istream_iterator`합니다. 이 인수는 선택 사항이며 기본값은 `char_traits`< `CharType`>입니다.

*거리* 하는 부호 있는 정수 계열 형식에 대해 차이 형식을 나타내는 `istream_iterator`합니다. 이 인수는 선택 사항이며 기본값은 `ptrdiff_t`입니다.

null이 아닌 저장된 포인터를 사용하여 istream_iterator 클래스를 구성 또는 증가한 이후 개체는 연결된 입력 스트림에서 `Type` 형식의 개체에 대해 효과적인 추출 및 저장을 시도합니다. 추출이 실패할 경우 개체는 저장된 포인터를 null 포인터로 대체하여 시퀀스 끝 표시기를 만듭니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[istream_iterator](#istream_iterator)|기본 `istream_iterator`로 스트림의 끝 반복기를 구성하거나 반복기의 스트림 형식에 초기화된 `istream_iterator`로 구성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|`istream_iterator`의 문자 형식을 허용하는 형식입니다.|
|[istream_type](#istream_type)|`istream_iterator`의 스트림 형식을 허용하는 형식입니다.|
|[traits_type](#traits_type)|`istream_iterator`의 특성 형식을 허용하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator*](#op_star)|역참조 연산자는 `Type`에서 주소 지정하는 형식 `istream_iterator`의 저장된 개체를 반환합니다.|
|[operator->](#op_arrow)|멤버의 값을 반환합니다(있는 경우).|
|[operator++](#op_add_add)|입력 스트림에서 증가된 개체를 추출하거나 개체를 증가하기 전에 복사하여 복사본을 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<iterator>

**네임스페이스:** std

## <a name="char_type"></a>  istream_iterator::char_type

`istream_iterator`의 문자 형식을 허용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Chartype`의 동의어입니다.

### <a name="example"></a>예

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iterator"></a>  istream_iterator::istream_iterator

기본 `istream_iterator`로 스트림의 끝 반복기를 구성하거나 반복기의 스트림 형식에 초기화된 `istream_iterator`로 구성합니다.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>매개 변수

*_Istr* 읽이 입력된 스트림을 초기화 하는 `istream_iterator`.

### <a name="remarks"></a>설명

첫 번째 생성자는 입력 스트림 포인터를 null 포인터로 초기화하고 스트림의 끝 반복기를 만듭니다. 두 번째 생성자는 입력된 스트림 포인터를 사용 하 여 초기화 *& _Istr*를 추출 하 고 형식의 개체를 저장 하려고 시도 `Type`합니다.

스트림의 끝 반복기를 사용하여 `istream_iterator`가 스트림의 끝에 도달했는지 테스트할 수 있습니다.

### <a name="example"></a>예

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_type"></a>  istream_iterator::istream_type

`istream_iterator`의 스트림 형식을 허용하는 형식입니다.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>설명

이 형식은 `basic_istream`\< **CharType**, **Traits**>의 동의어입니다.

### <a name="example"></a>예

`istream_type`을 선언하고 사용하는 방법에 대한 예제는 [istream_iterator](#istream_iterator)를 참조하세요.

## <a name="op_star"></a>  istream_iterator::operator*

역참조 연산자는 `Type`에서 주소 지정하는 형식 `istream_iterator`의 저장된 개체를 반환합니다.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>반환 값

형식의 저장 된 개체 `Type`합니다.

### <a name="example"></a>예

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_arrow"></a>  istream_iterator::operator-&gt;

멤버의 값을 반환합니다(있는 경우).

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>반환 값

멤버의 값입니다(있는 경우).

### <a name="remarks"></a>설명

*i* ->는 (\* *i*)와 같습니다. *m*

이 연산자는 **&\*\*this**를 반환합니다.

### <a name="example"></a>예

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_add_add"></a>  istream_iterator::operator++

입력 스트림에서 증가된 개체를 추출하거나 개체를 증가하기 전에 복사하여 복사본을 반환합니다.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>반환 값

형식의 증가 된 개체에 대 한 참조를 반환 하는 첫 번째 멤버 연산자 `Type` 입력 스트림과 두 번째 멤버 함수는 개체의 복사본에서 추출 합니다.

### <a name="example"></a>예

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="traits_type"></a>  istream_iterator::traits_type

`istream_iterator`의 특성 형식을 허용하는 형식입니다.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *Traits*와 동일한 의미입니다.

### <a name="example"></a>예

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>참고자료

[input_iterator_tag 구조체](../standard-library/input-iterator-tag-struct.md)<br/>
[iterator 구조체](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
