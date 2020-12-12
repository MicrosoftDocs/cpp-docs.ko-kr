---
description: '자세한 정보: ctype 클래스'
title: ctype 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: 9ef23707aa08e0fb3ad7edcff07bd2c6a4ae3814
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233086"
---
# <a name="ctype-class"></a>ctype 클래스

문자를 분류하고, 대문자에서 소문자로 변환하고, 네이티브 문자 집합과 로캘에서 사용하는 문자 집합 사이에서 변환하는 데 사용하는 패싯을 제공하는 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>매개 변수

*CharType*\
문자를 인코딩하기 위해 프로그램 내 사용하는 형식

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 `id`에 고유한 양수 값이 저장됩니다. 분류 기준에는 기본 클래스 ctype_base에 중첩된 비트 마스크 형식이 있습니다.

C + + 표준 라이브러리는이 클래스 템플릿에 대 한 두 가지 명시적 특수화를 정의 합니다.

- `ctype<char>`-차이를 별도로 설명 하는 명시적 특수화입니다. 자세한 내용은 [ctype &lt; char &gt; 클래스](../standard-library/ctype-char-class.md)를 참조 하세요.

- `ctype<wchar_t>`-요소를 와이드 문자로 처리 합니다.

클래스 템플릿의 기타 특수화 `ctype<CharType>` :

- 식을 사용 하 여 *chartype* 형식의 *ch* 값을 형식의 값으로 변환 **`char`** `(char)ch` 합니다.

- 형식의 값 *바이트* 를 **`char`** 식으로 *chartype* 형식의 값으로 변환 `CharType(byte)` 합니다.

다른 모든 작업은 **`char`** 명시적 특수화와 동일한 방법으로 값에 대해 수행 됩니다 `ctype<char>` .

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[ctype](#ctype)|문자의 로캘 패싯으로 사용할 수 있는 `ctype` 클래스의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하는 형식|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[do_is](#do_is)|단일 문자에 특정 특성이 있는지 여부를 테스트하거나 범위에 있는 각 문자의 특성을 분류하고 배열에 저장하기 위해 호출하는 가상 함수입니다.|
|[do_narrow](#do_narrow)|로캘에서 사용 하는 형식의 문자를 `CharType` **`char`** 네이티브 문자 집합에 있는 형식의 해당 문자로 변환 하기 위해 호출 하는 가상 함수입니다.|
|[do_scan_is](#do_scan_is)|범위에서 지정된 마스크와 일치하는 첫 번째 문자를 찾기 위해 호출하는 가상 함수입니다.|
|[do_scan_not](#do_scan_not)|범위에서 지정된 마스크와 일치하지 않는 첫 번째 문자를 찾기 위해 호출하는 가상 함수입니다.|
|[do_tolower](#do_tolower)|문자 또는 문자 범위를 소문자로 변환하기 위해 호출하는 함수입니다.|
|[do_toupper](#do_toupper)|문자 또는 문자 범위를 대문자로 변환하기 위해 호출하는 함수입니다.|
|[do_widen](#do_widen)|**`char`** 네이티브 문자 집합에서 형식의 문자를 로캘에서 사용 하는 형식의 해당 문자로 변환 하기 위해 호출 하는 가상 함수입니다 `CharType` .|
|[is](#is)|단일 문자에 특정 특성이 있는지 여부를 테스트하거나 범위에 있는 각 문자의 특성을 분류하고 배열에 저장합니다.|
|[narrow](#narrow)|로캘에서 사용하는 `CharType` 형식의 문자를 네이티브 문자 집합의 형식 문자의 해당 문자로 변환합니다.|
|[scan_is](#scan_is)|범위에서 지정된 마스크와 일치하는 첫 번째 문자를 찾습니다.|
|[scan_not](#scan_not)|범위에서 지정된 마스크와 일치하지 않는 첫 번째 문자를 찾습니다.|
|[tolower](#tolower)|문자 또는 문자 범위를 소문자로 변환합니다.|
|[toupper](#toupper)|문자 또는 문자 범위를 대문자로 변환합니다.|
|[widen](#widen)|**`char`** 네이티브 문자 집합에서 형식의 문자를 로캘에서 사용 하는 형식의 해당 문자로 변환 합니다 `CharType` .|

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="ctypechar_type"></a><a name="char_type"></a> ctype:: char_type

로캘에서 사용하는 문자를 설명하는 형식

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *Chartype* 의 동의어입니다.

### <a name="example"></a>예제

`char_type`을 반환 값으로 사용하는 예제는 멤버 함수 [widen](#widen)을 참조하세요.

## <a name="ctypectype"></a><a name="ctype"></a> ctype:: ctype

문자의 로캘 패싯으로 사용할 수 있는 ctype 클래스의 개체에 대한 생성자입니다.

```cpp
explicit ctype(size_t _Refs = 0);
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

생성자는 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`)를 통해 해당 `locale::facet` 기본 개체를 초기화합니다.

## <a name="ctypedo_is"></a><a name="do_is"></a> ctype::d o_is

단일 문자에 특정 특성이 있는지 여부를 테스트하거나 범위에 있는 각 문자의 특성을 분류하고 배열에 저장하기 위해 호출하는 가상 함수입니다.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자를 테스트할 마스크 값입니다.

*ch*\
특성을 테스트할 문자입니다.

*기본*\
특성을 분류할 범위 내 첫 번째 문자에 대한 포인터입니다.

*최신*\
특성을 분류할 범위 내 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
각 문자의 특성에 대한 특징을 지정하는 마스크 값을 저장할 배열의 시작 부분에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 **`true`** 테스트 한 문자가 마스크 값에서 설명한 특성을 포함 하는 경우 인 부울 값을 반환 하 고, 특성을 포함 하지 않으면 인 부울 값을 반환 합니다 **`false`** .

두 번째 멤버 함수는 범위 내 각 문자의 특성에 대한 특징을 지정하는 마스크 값을 포함하는 배열을 반환합니다.

### <a name="remarks"></a>설명

문자의 특성을 분류하는 마스크 값은 ctype이 파생되는 [ctype_base](../standard-library/ctype-base-class.md) 클래스에서 제공합니다. 첫 번째 멤버 함수에는 논리 비트 연산자(| , & , ^ , ~)를 통해 마스크 값을 조합하여 형성되는 첫 번째 매개 변수(비트 마스크라고도 함)에 대한 식도 사용할 수 있습니다.

### <a name="example"></a>예제

`do_is`를 호출하는 [is](#is)에 대한 예제를 참조하세요.

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a> ctype::d o_narrow

로캘에서 사용 하는 형식의 문자를 `CharType` **`char`** 네이티브 문자 집합에 있는 형식의 해당 문자로 변환 하기 위해 호출 하는 가상 함수입니다.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
로캘에서 변환하는 데 사용하는 `Chartype` 형식의 문자입니다.

*기본*\
멤버 함수에서 `CharType` 형식이 인 해당 문자를 포함 하지 않는 형식의 문자에 할당 되는 기본값입니다 **`char`** .

*기본*\
변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
**`char`** 변환 된 문자 범위를 저장 하는 대상 범위 내 형식의 첫 번째 문자에 대 한 const 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 보호 된 멤버 함수는 형식의 매개 변수 문자에 해당 하는 char 형식의 네이티브 문자를 반환 하 고 `CharType` , 해당 항목이 정의 되지 않은 경우 *기본값* 을 반환 합니다.

두 번째 보호된 멤버 함수는 `CharType` 형식의 문자에서 변환된 네이티브 문자의 대상 범위에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

두 번째 보호 된 멤버 템플릿 함수는 `dest` [ `I` `do_narrow` `first` `I` `default` `I` 0,) 간격으로에 대 한 `last`  -  `first` 값을 []에 저장 합니다.

### <a name="example"></a>예제

`do_narrow`를 호출하는 [narrow](#narrow)에 대한 예제를 참조하세요.

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a> ctype::d o_scan_is

범위에서 지정된 마스크와 일치하는 첫 번째 문자를 찾기 위해 호출하는 가상 함수입니다.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자로 일치할 마스크 값입니다.

*기본*\
검색할 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
검색할 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

지정된 마스크와 일치하는 범위의 첫 번째 문자에 대한 포인터입니다. 이러한 값이 없으면 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

Protected 멤버 함수는 `ptr` `first` `last` [do_is](#do_is)( `maskVal` , \* `ptr` )이 true 인 [,) 범위의 가장 작은 포인터를 반환 합니다.

### <a name="example"></a>예제

`do_scan_is`를 호출하는 [scan_is](#scan_is)에 대한 예제를 참조하세요.

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a> ctype::d o_scan_not

범위에서 지정된 마스크와 일치하지 않는 첫 번째 문자를 찾기 위해 호출하는 가상 함수입니다.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자로 일치하지 않을 마스크 값입니다.

*기본*\
검색할 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
검색할 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

지정된 마스크와 일치하지 않은 범위의 첫 번째 문자에 대한 포인터입니다. 이러한 값이 없으면 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

Protected 멤버 함수는 `ptr` `first` `last` [do_is](#do_is)( `maskVal` , \* `ptr` )이 false 인 [,) 범위의 가장 작은 포인터를 반환 합니다.

### <a name="example"></a>예제

`do_scan_not`을 호출하는 [scan_not](#scan_not)에 대한 예제를 참조하세요.

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a> ctype::d o_tolower

문자 또는 문자 범위를 소문자로 변환하기 위해 호출하는 가상 함수입니다.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
소문자로 변환할 문자입니다.

*기본*\
대/소문자를 변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
대/소문자를 변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 보호 된 멤버 함수는 *ch* 매개 변수의 소문자 형태를 반환 합니다. 소문자 형태가 없는 경우 *ch* 를 반환 합니다. 두 번째 보호 된 멤버 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

두 번째 보호 된 멤버 템플릿 함수는 [ `first` `I` 0,) 간격의에 대 한 각 요소 []를 `I` `last`  -  `first` `do_tolower` ( `first` [ `I` ])로 바꿉니다.

### <a name="example"></a>예제

`do_tolower`를 호출하는 [tolower](#tolower)에 대한 예제를 참조하세요.

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a> ctype::d o_toupper

문자 또는 문자 범위를 대문자로 변환하기 위해 호출하는 함수입니다.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
대문자로 변환할 문자입니다.

*기본*\
대/소문자를 변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
대/소문자를 변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 보호 된 멤버 함수는 *ch* 매개 변수의 대문자 형태를 반환 합니다. 대문자 양식이 없는 경우 *ch* 를 반환 합니다. 두 번째 보호 된 멤버 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

두 번째 보호 된 멤버 템플릿 함수는 [ `first` `I` 0,) 간격의에 대 한 각 요소 []를 `I` `last`  -  `first` `do_toupper` ( `first` [ `I` ])로 바꿉니다.

### <a name="example"></a>예제

`do_toupper`를 호출하는 [toupper](#toupper)에 대한 예제를 참조하세요.

## <a name="ctypedo_widen"></a><a name="do_widen"></a> ctype::d o_widen

**`char`** 네이티브 문자 집합에서 형식의 문자를 로캘에서 사용 하는 형식의 해당 문자로 변환 하기 위해 호출 하는 가상 함수입니다 `CharType` .

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>매개 변수

*바이트만*\
**`char`** 변환할 네이티브 문자 집합에 있는 형식의 문자입니다.

*기본*\
변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
변환한 문자 범위를 저장하는 대상 범위 내 `CharType` 형식의 첫 번째 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 보호 된 멤버 함수는 `CharType` 네이티브 형식의 매개 변수 문자에 해당 하는 형식의 문자를 반환 합니다 **`char`** .

두 번째 보호 된 멤버 함수는 `CharType` 형식의 네이티브 문자에서 변환 된 로캘에서 사용 하는 형식 문자의 대상 범위에 대 한 포인터를 반환 합니다 **`char`** .

### <a name="remarks"></a>설명

두 번째 보호된 멤버 템플릿 함수는 [0, `last` - `first`) 간격의 `I`에 대해 `do_widen`( `first`[ `I`]) 값을 `dest`[ `I`]에 저장합니다.

### <a name="example"></a>예제

`do_widen`을 호출하는 [widen](#widen)에 대한 예제를 참조하세요.

## <a name="ctypeis"></a><a name="is"></a> ctype:: is

단일 문자에 특정 특성이 있는지 여부를 테스트하거나 범위에 있는 각 문자의 특성을 분류하고 배열에 저장합니다.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자를 테스트할 마스크 값입니다.

*ch*\
특성을 테스트할 문자입니다.

*기본*\
특성을 분류할 범위 내 첫 번째 문자에 대한 포인터입니다.

*최신*\
특성을 분류할 범위 내 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
각 문자의 특성에 대한 특징을 지정하는 마스크 값을 저장할 배열의 시작 부분에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 **`true`** 테스트 한 문자가 마스크 값에서 설명한 특성을 포함 하는 경우를 반환 하 고, 특성이 없으면를 반환 합니다 **`false`** .

두 번째 멤버 함수는 특성을 분류할 범위의 마지막 문자에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

문자의 특성을 분류하는 마스크 값은 ctype이 파생되는 [ctype_base 클래스](../standard-library/ctype-base-class.md)에서 제공합니다. 첫 번째 멤버 함수에는 논리 비트 연산자(| , & , ^ , ~)를 통해 마스크 값을 조합하여 형성되는 첫 번째 매개 변수(비트 마스크라고도 함)에 대한 식도 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="ctypenarrow"></a><a name="narrow"></a> ctype:: 좁게

`CharType`로캘에서 사용 하는 형식의 문자를 **`char`** 네이티브 문자 집합에 있는 형식의 해당 문자로 변환 합니다.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
로캘에서 변환하는 데 사용하는 `Chartype` 형식의 문자입니다.

*기본*\
멤버 함수에서 `CharType` 형식이 인 해당 문자를 포함 하지 않는 형식의 문자에 할당 되는 기본값입니다 **`char`** .

*기본*\
변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
**`char`** 변환 된 문자 범위를 저장 하는 대상 범위 내 형식의 첫 번째 문자에 대 한 const 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 형식이 **`char`** `CharType default` 지정 되지 않은 경우 형식의 매개 변수 문자에 해당 하는 형식의 네이티브 문자를 반환 합니다.

두 번째 멤버 함수는 `CharType` 형식의 문자에서 변환된 네이티브 문자의 대상 범위에 대한 포인터를 반환합니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [do_narrow](#do_narrow)( `ch` ,)를 반환 합니다 `default` . 두 번째 멤버 함수는 [do_narrow](#do_narrow) ( `first` , `last` , `default` ,)를 반환 합니다 `dest` . 기본 소스 문자만 `narrow` 아래에 고유 역 이미지 `CharType`을 포함하는 것이 보장됩니다. 이러한 기본 소스 문자의 경우 `narrow` ( [widen](#widen) ( **c** ), 0 ) == **c** 와 같이 고정 값을 유지합니다.

### <a name="example"></a>예제

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="ctypescan_is"></a><a name="scan_is"></a> ctype:: scan_is

범위에서 지정된 마스크와 일치하는 첫 번째 문자를 찾습니다.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자로 일치할 마스크 값입니다.

*기본*\
검색할 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
검색할 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

지정된 마스크와 일치하는 범위의 첫 번째 문자에 대한 포인터입니다. 이러한 값이 없으면 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_scan_is](#do_scan_is)( `maskVal` , `first` , `last` )를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="ctypescan_not"></a><a name="scan_not"></a> ctype:: scan_not

범위에서 지정된 마스크와 일치하지 않는 첫 번째 문자를 찾습니다.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*maskVal*\
문자로 일치하지 않을 마스크 값입니다.

*기본*\
검색할 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
검색할 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

지정된 마스크와 일치하지 않은 범위의 첫 번째 문자에 대한 포인터입니다. 이러한 값이 없으면 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_scan_not](#do_scan_not)( `maskVal` , `first` , `last` )를 반환 합니다.

### <a name="example"></a>예제

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="ctypetolower"></a><a name="tolower"></a> ctype:: tolower

문자 또는 문자 범위를 소문자로 변환합니다.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
소문자로 변환할 문자입니다.

*기본*\
대/소문자를 변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
대/소문자를 변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 *ch* 매개 변수의 소문자 형태를 반환 합니다. 소문자 형태가 없는 경우 *ch* 를 반환 합니다.

두 번째 멤버 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [do_tolower](#do_tolower)()을 반환 합니다 `ch` . 두 번째 멤버 함수는 [do_tolower](#do_tolower)( `first` ,)를 반환 합니다 `last` .

### <a name="example"></a>예제

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="ctypetoupper"></a><a name="toupper"></a> ctype:: toupper

문자 또는 문자 범위를 대문자로 변환합니다.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*ch*\
대문자로 변환할 문자입니다.

*기본*\
대/소문자를 변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
대/소문자를 변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 *ch* 매개 변수의 대문자 형태를 반환 합니다. 대문자 양식이 없는 경우 *ch* 를 반환 합니다.

두 번째 멤버 함수는 *last* 를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [do_toupper](#do_toupper)()을 반환 합니다 `ch` . 두 번째 멤버 함수는 [do_toupper](#do_toupper)( `first` ,)를 반환 합니다 `last` .

### <a name="example"></a>예제

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="ctypewiden"></a><a name="widen"></a> ctype:: 넓히기

**`char`** 네이티브 문자 집합에서 형식의 문자를 로캘에서 사용 하는 형식의 해당 문자로 변환 합니다 `CharType` .

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>매개 변수

*바이트만*\
변환할 네이티브 문자 집합 내 char 형식의 문자입니다.

*기본*\
변환할 문자 범위의 첫 번째 문자에 대한 포인터입니다.

*최신*\
변환할 문자 범위의 마지막 문자 바로 다음에 있는 문자에 대한 포인터입니다.

*dest*\
변환한 문자 범위를 저장하는 대상 범위 내 `CharType` 형식의 첫 번째 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 `CharType` 네이티브 형식의 매개 변수 문자에 해당 하는 형식의 문자를 반환 합니다 **`char`** .

두 번째 멤버 함수는 `CharType` 형식의 네이티브 문자에서 변환 된 로캘에서 사용 하는 형식 문자의 대상 범위에 대 한 포인터를 반환 합니다 **`char`** .

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 [do_widen](#do_widen)()을 반환 합니다 `byte` . 두 번째 멤버 함수는 [do_widen](#do_widen)( `first` , `last` ,)를 반환 합니다 `dest` .

### <a name="example"></a>예제

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
