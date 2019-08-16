---
title: '&lt;istream&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: f5da7c6805d10e919255ce301dae5618ef58e76d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501920"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 연산자

## <a name="op_gt_gt"></a>  operator&gt;&gt;

스트림에서 문자 및 문자열을 추출합니다.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>매개 변수

*Ch*\
단일 문자입니다.

*Istr*\
스트림입니다.

*문자열*\
문자열

*짧은*\
형식입니다.

### <a name="return-value"></a>반환 값

스트림

### <a name="remarks"></a>설명

`basic_istream` 클래스도 여러 가지 추출 연산자를 정의합니다. 자세한 내용은 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)를 참조하세요.

다음 템플릿 함수는

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

이 함수는 최대 *N* - 1개 요소를 추출하여 _ *Str*에서 시작하는 배열에 저장합니다. `Istr`. [width](../standard-library/ios-base-class.md#width)가 0보다 큰 경우 *N*은 `Istr`. **너비**; 그렇지 않으면 선언할 수 있는의 `Elem` 가장 큰 배열 크기입니다. 함수는 저장 되는 모든 `Elem()` 추출 된 요소 뒤에 값을 저장 합니다. 추출은 파일의 끝, **Elem**(0) 값을 갖는 문자(추출되지 않음) 또는 [ws](../standard-library/istream-functions.md#ws)에 의해 삭제될 모든 요소(추출되지 않음)에서 미리 중지됩니다. 함수가 요소를 추출하지 않는 경우 `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate) (**failbit**). 어떤 경우든 `Istr`. **너비** (0) 및는 *Istr*을 반환 합니다.

**보안 정보** 입력 스트림에서 추출 되는 null로 끝나는 문자열은 대상 버퍼 *str*의 크기를 초과 하면 안 됩니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

다음 템플릿 함수는

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

가능 하면 요소를 추출 하 여 *Ch*에 저장 합니다. 그렇지 않으면 **is**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)를 호출합니다. 어떤 경우 든 *Istr*을 반환 합니다.

다음 템플릿 함수는

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

`Istr >> ( char * ) str`를 반환합니다.

다음 템플릿 함수는

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

`Istr >> ( char& ) Ch`를 반환합니다.

다음 템플릿 함수는

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

`Istr >> ( char * ) str`를 반환합니다.

다음 템플릿 함수는

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

`Istr >> ( char& ) Ch`를 반환합니다.

다음 템플릿 함수는

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

을 `Istr >> val` 반환 하 고 rvalue 참조를 `Istr` 프로세스의 lvalue로 변환 합니다.

### <a name="example"></a>예제

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>참고자료

[\<istream>](../standard-library/istream.md)
