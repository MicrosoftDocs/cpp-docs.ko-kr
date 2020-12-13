---
description: Num_put 클래스에 대해 자세히 알아보세요.
title: num_put 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 44f7d5248914969b360454bbec80e767a21be55f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338066"
---
# <a name="num_put-class"></a>num_put 클래스

숫자 값에서 형식의 시퀀스로 변환을 제어 하는 로캘 패싯으로 사용할 수 있는 개체를 설명 하는 클래스 템플릿입니다 `CharType` .

## <a name="syntax"></a>구문

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>매개 변수

*CharType*\
로캘의 문자를 인코딩하기 위해 프로그램 내 사용하는 형식입니다.

*OutputIterator*\
숫자 put 함수가 출력을 쓰는 반복기의 형식입니다.

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 **id** 에 고유한 양수 값이 저장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[num_put](#num_put)|`num_put` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.|
|[iter_type](#iter_type)|출력 반복기에 대해 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[do_put](#do_put)|숫자를 지정된 로캘에 대해 서식이 지정된 숫자를 나타내는 `CharType`의 시퀀스로 변환하기 위해 호출하는 가상 함수입니다.|
|[보관](#put)|숫자를 지정된 로캘에 대해 서식이 지정된 숫자를 나타내는 `CharType`의 시퀀스로 변환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="num_putchar_type"></a><a name="char_type"></a> num_put:: char_type

로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `CharType`의 동의어입니다.

## <a name="num_putdo_put"></a><a name="do_put"></a> num_put::d o_put

숫자를 지정된 로캘에 대해 서식이 지정된 숫자를 나타내는 `CharType`의 시퀀스로 변환하기 위해 호출하는 가상 함수입니다.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>매개 변수

*그런*\
삽입된 문자열의 첫 번째 요소 주소를 지정하는 반복기입니다.

*_Iosbase*\
출력 및 출력 서식 지정을 위한 플래그에 문장 부호를 적용하는 데 사용되는 numpunct 패싯이 들어 있는 로캘을 포함하는 스트림을 지정합니다.

*_Fill*\
간격에 사용되는 문자입니다.

*짧은*\
출력할 숫자 또는 부울 형식입니다.

### <a name="return-value"></a>반환 값

생성된 마지막 요소에서 한 위치 다음의 위치 주소를 지정하는 출력 반복기입니다.

### <a name="remarks"></a>설명

첫 번째 보호 된 가상 멤버 함수는 *다음* 에서 시작 하는 순차 요소를 생성 하 여 *val* 값에서 정수 출력 필드를 생성 합니다. 함수는 생성된 정수 출력 필드를 지나 요소를 삽입할 다음 위치를 지정하는 반복기를 반환합니다.

정수 출력 필드는 파일에 일련의 요소를 생성 하기 위해 인쇄 함수에서 사용 하는 것과 동일한 규칙을 사용 하 여 생성 됩니다 **`char`** . 이러한 각 char 요소는 단순 하 고 일대일 매핑으로 형식의 동등한 요소에 매핑되는 것으로 간주 됩니다 `CharType` . 그러나 print 함수는 공백이 나 숫자 0으로 필드를 채웁니다 `do_put` . 대신는를 사용 `fill` 합니다. 동일한 인쇄 변환 사양은 다음과 같이 결정됩니다.

- **iosbase**. [](../standard-library/ios-base-class.md#flags)  &  `ios_base::basefield` 플래그  ==  `ios_base::` [10 월](../standard-library/ios-functions.md#oct), 변환 사양은 `lo` 입니다.

- **Iosbase. flags**  &  **ios_base:: basefield**  ==  `ios_base::` [hex](../standard-library/ios-functions.md#hex)인 경우 변환 사양은 `lx` 입니다.

- 그렇지 않으면 변환 사양은 `ld`입니다.

**iosbase**. [width](../standard-library/ios-base-class.md#width)가 0이 아닌 경우 이 값의 필드 너비가 앞에 추가됩니다. 그런 후에 이 함수는 **iosbase**. **width**(0)을 호출하여 필드 너비를 0으로 다시 설정합니다.

출력 필드를 지정하는 데 필요한 최소 요소 수 *N* 이 **iosbase**. [너비](../standard-library/ios-base-class.md#width). 이러한 패딩은 채우기의 *N*  -  **너비** 복사본 시퀀스로 구성 됩니다 . 그런 후에 다음과 같이 채우기가 수행됩니다.

- **iosbase**.   &  `ios_base::adjustfield` 플래그  ==  `ios_base::` [왼쪽](../standard-library/ios-functions.md#left)으로 플래그를 **-** 앞에 붙습니다. 채우기는 생성된 텍스트 뒤에서 수행됩니다.

- **Iosbase. flags**  &  **ios_base:: adjustfield**  ==  `ios_base::` [internal](../standard-library/ios-functions.md#internal)인 경우 플래그 **0** 이 앞에 붙습니다. 숫자 출력 필드의 경우에는 print 함수가 0으로 채우는 위치에서 채우기가 수행됩니다.

- 그렇지 않은 경우에는 추가 플래그가 앞에 추가되지 않습니다. 채우기는 생성된 시퀀스 앞에서 수행됩니다.

그리고 마지막으로 다음과 같이 채우기가 수행됩니다.

- **iosbase**.   &  플래그 `ios_base::` [showpos](../standard-library/ios-functions.md#showpos) 가 0이 아니면 **+** 변환 사양 앞에 플래그를 지정 합니다.

- **iosbase**. **플래그**  &  **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) 가 0이 아니면 **#** 변환 사양 앞에 플래그가 붙습니다.

정수 출력 필드의 형식은 호출 [use_facet](../standard-library/locale-functions.md#use_facet) [](../standard-library/locale-class.md#facet_class)  <  [numpunct](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**)에서 반환 된 로캘 패싯 fac에 의해 추가로 결정 됩니다. [getloc](../standard-library/ios-base-class.md#getloc))에서 반환됩니다. 특히 다음 사항에 주의하세요.

- **fac**. [그룹화](../standard-library/numpunct-class.md#grouping) 는 소수점이 하 자릿수를 그룹화 하는 방법을 결정 합니다.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 은 소수점 왼쪽의 숫자 그룹을 구분 하는 시퀀스를 결정 합니다.

**fac**, **grouping** 에 의해 그룹화 제약 조건이 적용되지 않는 경우(해당 첫 번째 요소값이 CHAR_MAX임) **fac**. `thousands_sep`의 인스턴스가 출력 필드에서 생성되지 않습니다. 그렇지 않은 경우에는 인쇄 변환이 수행된 후에 구분 기호가 삽입됩니다.

두 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

이 함수는 `ld`의 변환 사양을 `lu`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

세 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

이 함수는 **val**. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point)의 값에서 부동 소수점 출력 필드를 생성하며 정수 자릿수와 소수 자릿수를 구분하는 시퀀스를 결정한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 동일한 인쇄 변환 사양은 다음과 같이 결정됩니다.

- **iosbase**.   &  `ios_base::floatfield` 플래그  ==  `ios_base::` [](../standard-library/ios-functions.md#fixed)변환 사양은 `lf` 입니다.

- **iosbase**. **플래그**  &  **ios_base:: floatfield**  ==  `ios_base::` [과학적](../standard-library/ios-functions.md#scientific), 변환 사양은 `le` 입니다. **iosbase**.   &  플래그 `ios_base::` [대문자](../standard-library/ios-functions.md#uppercase) 는 0이 아닌 값으로 `e` 대체 됩니다 `E` .

- 그렇지 않으면 변환 사양은 **lg** 입니다. **iosbase**. **플래그**  &  **ios_base:: 대문자** 는 0이 아닌 값으로 `g` 대체 됩니다 `G` .

**iosbase**. **플래그**  &  **ios_base:: fixed** 가 0이 아니거나 **iosbase** 인 경우 [precision](../standard-library/ios-base-class.md#precision)이 0보다 크면 **iosbase**. **precision** 값이 포함된 전체 자릿수가 변환 사양 앞에 추가됩니다. 모든 채우기는 정수 출력 필드에 대해 동일하게 동작합니다. 채우기 문자는 **fill** 입니다. 그리고 마지막으로 다음과 같이 채우기가 수행됩니다.

- **iosbase**.   &  플래그 `ios_base::` [showpos](../standard-library/ios-functions.md#showpos) 가 0이 아니면 **+** 변환 사양 앞에 플래그를 지정 합니다.

- **iosbase**.   &  플래그 `ios_base::` [showpoint](../standard-library/ios-functions.md#showpoint) 가 0이 아니면 **#** 변환 사양 앞에 플래그가 붙습니다.

네 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

`l`변환 사양의 한정자가로 대체 되는 점을 제외 하 고 세 번째와 동일한 동작을 수행 합니다 `L` .

다섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

이 함수는 변환 사양이 `p`**및** 채우기를 지하는 데 필요한 한정자라는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

여섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

*val* 에서 부울 출력 필드를 생성 한다는 점을 제외 하 고는 첫 번째와 동일 하 게 동작 합니다.

부울 출력 필드는 두 가지 형식 중 하나를 사용합니다. `iosbase.flags & ios_base::` [Boolalpha](../standard-library/ios-functions.md#boolalpha) 가 인 경우 **`false`** 멤버 함수는 `do_put(_Next, _Iosbase, _Fill, (long)val)` 일반적으로 0 (의 경우 **`false`** ) 또는 1 (의 경우)의 생성 된 시퀀스를 생성 하는를 반환 합니다 **`true`** . 그렇지 않으면 생성 된 시퀀스는 *fac* 입니다. [falsename](../standard-library/numpunct-class.md#falsename) (의 경우 **`false`** ) 또는 *fac*.[ truename](../standard-library/numpunct-class.md#truename) (의 경우 **`true`** ).

일곱 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

이 함수는 `ld`의 변환 사양을 `lld`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

여덟 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

이 함수는 `ld`의 변환 사양을 `llu`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

### <a name="example"></a>예제

`do_put`을 호출하는 [put](#put)에 대한 예제를 참조하세요.

## <a name="num_putiter_type"></a><a name="iter_type"></a> num_put:: iter_type

출력 반복기에 대해 설명하는 형식입니다.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **OutputIterator** 와 동일한 의미입니다.

## <a name="num_putnum_put"></a><a name="num_put"></a> num_put:: num_put

`num_put` 형식의 개체에 대한 생성자입니다.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>매개 변수

*_Refs*\
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

### <a name="remarks"></a>설명

*_Refs* 매개 변수에 사용할 수 있는 값과 해당 의미는 다음과 같습니다.

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \> 1: 이러한 값은 정의 되지 않습니다.

소멸자는 보호되므로 직접적인 예제는 확인할 수 없습니다.

생성자는 **locale::**[Facet](../standard-library/locale-class.md#facet_class)(_ *Refs*)를 사용 하 여 해당 기본 개체를 초기화 합니다.

## <a name="num_putput"></a><a name="put"></a> num_put::p

숫자를 `CharType` 지정 된 로캘에 대해 서식이 지정 된 숫자를 나타내는의 시퀀스로 변환 합니다.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>매개 변수

*dest*\
삽입된 문자열의 첫 번째 요소 주소를 지정하는 반복기입니다.

*_Iosbase*\
출력 및 출력 서식 지정을 위한 플래그에 문장 부호를 적용하는 데 사용되는 numpunct 패싯이 들어 있는 로캘을 포함하는 스트림을 지정합니다.

*_Fill*\
간격에 사용되는 문자입니다.

*짧은*\
출력할 숫자 또는 부울 형식입니다.

### <a name="return-value"></a>반환 값

생성된 마지막 요소에서 한 위치 다음의 위치 주소를 지정하는 출력 반복기입니다.

### <a name="remarks"></a>설명

모든 멤버 함수는 [do_put](#do_put)( `next` , `_Iosbase` , `_Fill` , `val` )를 반환 합니다.

### <a name="example"></a>예제

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)\
[패싯 클래스](../standard-library/locale-class.md#facet_class)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
