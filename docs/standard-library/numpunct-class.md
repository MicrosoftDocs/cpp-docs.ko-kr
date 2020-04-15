---
title: numpunct 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: 0bdd6556df892e5e231919dbc4ae95d14a6f95fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373622"
---
# <a name="numpunct-class"></a>numpunct 클래스

숫자 및 부울 식의 서식 및 문장 부호에 대한 `CharType` 정보를 나타내는 데 사용되는 형식의 시퀀스를 설명하는 로컬 면역할을 할 수 있는 개체를 설명하는 클래스 템플릿입니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>매개 변수

*Chartype*\
로캘의 문자를 인코딩하기 위해 프로그램 내 사용하는 형식입니다.

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 **id**에 고유한 양수 값이 저장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[numpunct](#numpunct)|`numpunct` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|Description|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.|
|[string_type](#string_type)|`CharType` 형식의 문자가 포함된 문자열을 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[decimal_point](#decimal_point)|소수점으로 사용할 로캘별 요소를 반환합니다.|
|[do_decimal_point](#do_decimal_point)|소수점으로 사용할 로캘별 요소를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_falsename](#do_falsename)|**false**값의 텍스트 표현으로 사용할 문자열을 반환하는 호출된 보호된 가상 멤버 함수입니다.|
|[do_grouping](#do_grouping)|소수점 자리 왼쪽의 숫자를 그룹화하는 방법을 결정하는 로캘별 규칙을 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_thousands_sep](#do_thousands_sep)|1000 단위 구분 기호로 사용할 로캘별 요소를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.|
|[do_truename](#do_truename)|**true** 값을 텍스트로 표현하는 데 사용할 문자열을 반환하기 위해 호출하는 보호된 가상 구성원 함수입니다.|
|[falsename](#falsename)|**false** 값을 텍스트로 표현하기 위해 사용할 문자열을 반환합니다.|
|[그룹화](#grouping)|소수점 왼쪽의 숫자를 그룹화할 방법을 결정하기 위한 로캘별 규칙을 반환합니다.|
|[thousands_sep](#thousands_sep)|1000 단위 구분 기호로 사용할 로캘별 요소를 반환합니다.|
|[truename](#truename)|**true** 값을 텍스트로 표현하기 위해 사용할 문자열을 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<locale>

**네임스페이스:** std

## <a name="numpunctchar_type"></a><a name="char_type"></a>numpunct::char_type

로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 **CharType의** 동의어입니다.

## <a name="numpunctdecimal_point"></a><a name="decimal_point"></a>numpunct::decimal_포인트

소수점으로 사용할 로캘별 요소를 반환합니다.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Return Value

소수점으로 사용할 로캘별 요소입니다.

### <a name="remarks"></a>설명

구성원 함수는 [do_decimal_point](#do_decimal_point)를 반환합니다.

### <a name="example"></a>예제

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpunctdo_decimal_point"></a><a name="do_decimal_point"></a>numpunct::do_소수점_점

소수점으로 사용할 로캘별 요소를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Return Value

소수점으로 사용할 로캘별 요소입니다.

### <a name="example"></a>예제

`decimal_point`에 의해 가상 구성원 함수가 호출되는 [decimal_point](#decimal_point)의 예제를 참조하세요.

## <a name="numpunctdo_falsename"></a><a name="do_falsename"></a>numpunct::do_falsename

보호된 가상 구성원 함수는 **false** 값을 텍스트로 표현하는 데 사용할 시퀀스를 반환합니다.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Return Value

**false** 값을 텍스트로 표현하는 데 사용할 시퀀스가 포함된 문자열입니다.

### <a name="remarks"></a>설명

구성원 함수는 모든 로캘에서 **false** 값을 나타내기 위해 "false" 문자열을 반환합니다.

### <a name="example"></a>예제

`falsename`에 의해 가상 구성원 함수가 호출되는 [falsename](#falsename)의 예제를 참조하세요.

## <a name="numpunctdo_grouping"></a><a name="do_grouping"></a>numpunct::do_grouping

소수점 자리 왼쪽의 숫자를 그룹화하는 방법을 결정하는 로캘별 규칙을 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Return Value

소수점 왼쪽의 숫자를 그룹화할 방법을 결정하기 위한 로캘별 규칙입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수가 소수점 자리 왼쪽의 숫자를 그룹화하는 방법을 결정하는 로캘별 규칙을 반환합니다. 인코딩이 **lconv::grouping**과 동일합니다.

### <a name="example"></a>예제

가상 멤버 함수가 에서 호출되는 [그룹화에](#grouping)대한 예제를 `grouping`참조하십시오.

## <a name="numpunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>numpunct::do_천_9ep

1000 단위 구분 기호로 사용할 로캘별 요소를 반환하기 위해 호출하는 보호된 가상 멤버 함수입니다.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Return Value

1000 단위 구분 기호로 사용할 로캘별 요소를 반환합니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 소수점의 `CharType` 왼쪽에 그룹 구분기호로 사용할 형식의 로캘 관련 요소를 반환합니다.

### <a name="example"></a>예제

`thousands_sep`에 의해 가상 구성원 함수가 호출되는 [thousands_sep](#thousands_sep)의 예제를 참조하세요.

## <a name="numpunctdo_truename"></a><a name="do_truename"></a>numpunct::do_truename

**true** 값을 텍스트로 표현하는 데 사용할 문자열을 반환하기 위해 호출하는 보호된 가상 구성원 함수입니다.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>설명

**true** 값을 텍스트로 표현하기 위해 사용할 문자열입니다.

모든 로캘은 **true** 값을 나타내기 위한 문자열 "true"를 반환합니다.

### <a name="example"></a>예제

`truename`에 의해 가상 구성원 함수가 호출되는 [truename](#truename)의 예제를 참조하세요.

## <a name="numpunctfalsename"></a><a name="falsename"></a>numpunct::falsename

**false** 값을 텍스트로 표현하기 위해 사용할 문자열을 반환합니다.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Return Value

`CharType` **false**값의 텍스트 표현으로 사용할 s 시퀀스를 포함하는 문자열입니다.

### <a name="remarks"></a>설명

구성원 함수는 모든 로캘에서 **false** 값을 나타내기 위해 "false" 문자열을 반환합니다.

구성원 함수는 [do_falsename](#do_falsename)을 반환합니다.

### <a name="example"></a>예제

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="numpunctgrouping"></a><a name="grouping"></a>numpunct::그룹화

소수점 왼쪽의 숫자를 그룹화할 방법을 결정하기 위한 로캘별 규칙을 반환합니다.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Return Value

소수점 왼쪽의 숫자를 그룹화할 방법을 결정하기 위한 로캘별 규칙입니다.

### <a name="remarks"></a>설명

구성원 함수는 [do_grouping](#do_grouping)을 반환합니다.

### <a name="example"></a>예제

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
```

## <a name="numpunctnumpunct"></a><a name="numpunct"></a>numpunct::numpunct

`numpunct` 형식의 개체에 대한 생성자입니다.

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>매개 변수

*_Refs*\
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

### <a name="remarks"></a>설명

*_Refs* 매개 변수와 그 중요성에 대한 가능한 값은 다음과 같습니다.

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \>1: 이러한 값은 정의되지 않습니다.

소멸자는 보호되므로 직접적인 예제는 확인할 수 없습니다.

생성자는 기본 개체를 **로캘::**[facet](../standard-library/locale-class.md#facet_class)()로`_Refs`초기화합니다.

## <a name="numpunctstring_type"></a><a name="string_type"></a>numpunct::string_type

**CharType** 형식의 문자가 포함된 문자열을 설명하는 형식입니다.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>설명

형식은 개체가 문장 부호 시퀀스의 복사본을 저장할 수 [basic_string](../standard-library/basic-string-class.md) 클래스 템플릿의 전문화에 대해 설명합니다.

## <a name="numpunctthousands_sep"></a><a name="thousands_sep"></a>numpunct:thousands_sep

1000 단위 구분 기호로 사용할 로캘별 요소를 반환합니다.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Return Value

1000 단위 구분 기호로 사용할 로캘별 요소입니다.

### <a name="remarks"></a>설명

구성원 함수는 [do_thousands_sep](#do_thousands_sep)를 반환합니다.

### <a name="example"></a>예제

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpuncttruename"></a><a name="truename"></a>numpunct::truename

**true** 값을 텍스트로 표현하기 위해 사용할 문자열을 반환합니다.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Return Value

**true** 값을 텍스트로 표현하기 위해 사용할 문자열입니다.

### <a name="remarks"></a>설명

구성원 함수는 [do_truename](#do_truename)을 반환합니다.

모든 로캘은 **true** 값을 나타내기 위한 문자열 "true"를 반환합니다.

### <a name="example"></a>예제

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>참고 항목

[\<로캘>](../standard-library/locale.md)\
[페이스트 클래스](../standard-library/locale-class.md#facet_class)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
