---
description: Num_get 클래스에 대해 자세히 알아보세요.
title: num_get 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 0236aac2e7c7859f966430bd276b4dffc42820b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338084"
---
# <a name="num_get-class"></a>num_get 클래스

형식의 시퀀스에서 숫자 값으로의 변환을 제어 하는 로캘 패싯으로 사용할 수 있는 개체를 설명 하는 클래스 템플릿입니다 `CharType` .

## <a name="syntax"></a>구문

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>매개 변수

*CharType*\
로캘의 문자를 인코딩하기 위해 프로그램 내 사용하는 형식입니다.

*InputIterator*\
숫자 get 함수가 입력을 읽어올 반복기의 형식입니다.

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 **id** 에 고유한 양수 값이 저장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[num_get](#num_get)|시퀀스에서 숫자 값을 추출하는 데 사용되는 `num_get` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.|
|[iter_type](#iter_type)|입력 반복기에 대해 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[do_get](#do_get)|문자 시퀀스에서 숫자 또는 부울 값을 추출하기 위해 호출하는 가상 함수입니다.|
|[get](#get)|문자 시퀀스에서 숫자 또는 부울 값을 추출합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="num_getchar_type"></a><a name="char_type"></a> num_get:: char_type

로캘에서 사용하는 문자를 설명하기 위해 사용하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **Chartype** 의 동의어입니다.

## <a name="num_getdo_get"></a><a name="do_get"></a> num_get::d o_get

문자 시퀀스에서 숫자 또는 부울 값을 추출하기 위해 호출하는 가상 함수입니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
숫자를 읽을 문자 범위의 시작 부분입니다.

*최신*\
숫자를 읽을 문자 범위의 끝부분입니다.

*iosbase*\
해당 플래그가 변환에 사용되는 [ios_base](../standard-library/ios-base-class.md)입니다.

*상태일*\
오류 시 failbit가 추가되는 상태([ios_base::iostate](../standard-library/ios-base-class.md#iostate) 참조)입니다.

*짧은*\
읽은 값입니다.

### <a name="return-value"></a>반환 값

값을 읽은 후의 반복기입니다.

### <a name="remarks"></a>설명

첫 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

는  `[first, last)` 비어 있지 않은 완전 한 정수 입력 필드를 인식할 때까지 시퀀스의 처음부터 시작 하는 순차적 요소와 일치 합니다. 성공 하는 경우이 필드를 형식과 동일한 값으로 변환 **`long`** 하 고 결과를 *val* 에 저장 합니다. 이 함수는 숫자 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 *val* 에 아무 것도 저장 하지 않으며 `ios_base::failbit` 에는를 설정 `state` 합니다. 그리고 유효한 정수 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 `last`와 같으면 함수는 `state`에서 `ios_base::eofbit`를 설정합니다.

정수 입력 필드는 파일의 일련의 요소를 일치 및 변환 하기 위해 검색 함수에서 사용 하는 것과 동일한 규칙에 의해 변환 됩니다 **`char`** . 이러한 각 **`char`** 요소는 `Elem` 간단한 일대일 매핑을 통해 형식의 동등한 요소에 매핑되는 것으로 간주 됩니다. 해당 하는 검색 변환 사양은 다음과 같이 결정 됩니다.

`iosbase.` [Ios_base:: flags](../standard-library/ios-base-class.md#flags) `() & ios_base::basefield == ios_base::` 가[oct](../standard-library/ios-functions.md#oct)인 경우 변환 사양은 `lo` 입니다.

`iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)이면 변환 사양은 `lx`입니다.

`iosbase.flags() & ios_base::basefield == 0`이면 변환 사양은 `li`입니다.

그렇지 않으면 변환 사양은 `ld`입니다.

정수 입력 필드의 형식은 [](../standard-library/locale-class.md#facet_class) `fac` 호출 [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#getloc)에 의해 반환 되는 로캘 패싯에 따라 결정 됩니다 `())` . 특히 다음 사항에 주의하세요.

`fac.`[numpunct:: grouping](../standard-library/numpunct-class.md#grouping) `()` 소수점 왼쪽의 숫자를 그룹화 하는 방법을 결정 합니다.

`fac.`[numpunct:: thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` 소수점 왼쪽의 숫자 그룹을 구분 하는 시퀀스를 결정 합니다.

숫자 입력 필드에 `fac.thousands_sep()`의 인스턴스가 없으면 그룹화 제약 조건이 적용되지 않습니다. 그렇지 않으면 `fac.grouping()`에 의해 적용되는 모든 그룹화 제약 조건이 적용되며 스캔 변환이 수행되기 전에 구분 기호가 제거됩니다.

네 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

이 함수는 `ld`의 변환 사양을 `lu`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하면 숫자 입력 필드를 형식의 값으로 변환 하 **`unsigned long`** 고 해당 값을 *val* 에 저장 합니다.

다섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

이 함수는 `ld`의 변환 사양을 `lld`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하면 숫자 입력 필드를 형식의 값으로 변환 하 **`long long`** 고 해당 값을 *val* 에 저장 합니다.

여섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

이 함수는 `ld`의 변환 사양을 `llu`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하면 숫자 입력 필드를 형식의 값으로 변환 하 **`unsigned long long`** 고 해당 값을 *val* 에 저장 합니다.

일곱 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

이 함수는 비어 있지 않은 완전한 부동 소수점 입력 필드와의 일치를 시도한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` 소수 자릿수와 정수 자릿수를 구분 하는 시퀀스를 결정 합니다. 동일한 스캔 변환 지정자는 `lf`입니다.

여덟 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

이 함수는 비어 있지 않은 완전한 부동 소수점 입력 필드와의 일치를 시도한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` 소수 자릿수와 정수 자릿수를 구분 하는 시퀀스를 결정 합니다. 동일한 스캔 변환 지정자는 `lf`입니다.

아홉 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

이 함수는 동일한 스캔 변환 지정자가 `Lf`라는 점을 제외하면 여덟 번째 함수와 동일하게 동작합니다.

10 번째 가상 보호 된 멤버 함수:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

이 함수는 동일한 스캔 변환 지정자가 `p`라는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

마지막(열한 번째) 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

이 함수는 비어 있지 않은 완전한 부울 입력 필드와의 일치를 시도한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하면 부울 입력 필드를 형식의 값으로 변환 하 **`bool`** 고 해당 값을 *val* 에 저장 합니다.

부울 입력 필드는 두 가지 형식 중 하나를 사용합니다. `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha)가 false인 경우 변환된 값이 0(false의 경우) 또는 1(true의 경우)이어야 한다는 점을 제외하면 정수 입력 필드와 동일합니다. 그렇지 않으면 시퀀스는 `fac.` [numpunct:: falsename](../standard-library/numpunct-class.md#falsename) `()` (false의 경우) 또는 `fac.` [numpunct:: truename](../standard-library/numpunct-class.md#truename) `()` (true의 경우)과 일치 해야 합니다.

### <a name="example"></a>예제

`do_get`에 의해 가상 구성원 함수가 호출되는 [get](#get)의 예제를 참조하세요.

## <a name="num_getget"></a><a name="get"></a> num_get:: get

문자 시퀀스에서 숫자 또는 부울 값을 추출합니다.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
숫자를 읽을 문자 범위의 시작 부분입니다.

*최신*\
숫자를 읽을 문자 범위의 끝부분입니다.

*iosbase*\
해당 플래그가 변환에 사용되는 [ios_base](../standard-library/ios-base-class.md)입니다.

*상태일*\
오류 시 failbit가 추가되는 상태([ios_base::iostate](../standard-library/ios-base-class.md#iostate) 참조)입니다.

*짧은*\
읽은 값입니다.

### <a name="return-value"></a>반환 값

값을 읽은 후의 반복기입니다.

### <a name="remarks"></a>설명

모든 멤버 함수는 [do_get](#do_get) `( first, last, iosbase, state, val)` 를 반환 합니다.

첫 번째 보호된 가상 구성원 함수는 비어 있지 않은 완전한 정수 입력 필드를 인식할 때까지 시퀀스 [ `first`, `last`)에서 처음 시작되는 순차 요소 일치를 시도합니다. 성공 하면이 필드를 형식과 동일한 값으로 변환 **`long`** 하 고 결과를 *val* 에 저장 합니다. 이 함수는 숫자 입력 필드를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 그렇지 않으면 함수는 *val* 에 아무 것도 저장 하지 않으며 `ios_base::failbit` *상태* 를 설정 합니다. 그리고 유효한 정수 입력 필드의 접두사를 벗어난 범위에 있는 첫 번째 요소를 지정하는 반복기를 반환합니다. 두 경우 모두 반환 값이 *last* 와 같으면 함수는 `ios_base::eofbit` *상태* 를 설정 합니다.

정수 입력 필드는 파일의 일련의 요소를 일치 및 변환 하기 위해 검색 함수에서 사용 하는 것과 동일한 규칙에 의해 변환 됩니다 **`char`** . 이러한 각 **`char`** 요소는 간단한 일대일 매핑으로 형식의 동등한 요소에 매핑되는 것으로 간주 됩니다 `CharType` . 동일한 스캔 변환 사양은 다음과 같이 결정됩니다.

- `iosbase.` [](../standard-library/ios-base-class.md#flags) `& ios_base::basefield == ios_base::` [10 진수로](../standard-library/ios-functions.md#oct)플래그를 지정 하는 경우 변환 사양은 `lo` 입니다.

- `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)이면 변환 사양은 `lx`입니다.

- `iosbase.flags & ios_base::basefield == 0`이면 변환 사양은 `li`입니다.

- 그렇지 않으면 변환 사양은 `ld`입니다.

정수 입력 필드의 형식은 [](../standard-library/locale-class.md#facet_class) `fac` [use_facet](../standard-library/locale-functions.md#use_facet) `<` [`numpunct`](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [getloc](../standard-library/ios-base-class.md#getloc)호출에서 반환 되는 로캘 패싯에 따라 결정 됩니다 `())` . 특히 다음 사항에 주의하세요.

- `fac.`[그룹화](../standard-library/numpunct-class.md#grouping) 는 소수점이 하 자릿수의 왼쪽으로 숫자를 그룹화 하는 방법을 결정 합니다.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 은 소수점 왼쪽의 숫자 그룹을 구분 하는 시퀀스를 결정 합니다.

숫자 입력 필드에 `fac.thousands_sep`의 인스턴스가 없으면 그룹화 제약 조건이 적용되지 않습니다. 그렇지 않으면에 의해 적용 되는 모든 그룹화 제약 조건이 `fac.grouping` 적용 되며 검색 변환이 수행 되기 전에 구분 기호가 제거 됩니다.

두 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

이 함수는 `ld`의 변환 사양을 `lu`로 대체한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하는 경우 숫자 입력 필드를 형식의 값으로 변환 하 **`unsigned long`** 고 *val* 에 해당 값을 저장 합니다.

세 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

이 함수는 비어 있지 않은 완전한 부동 소수점 입력 필드와의 일치를 시도한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) 소수 자릿수와 정수 자릿수를 구분 하는 시퀀스를 결정 합니다. 동일한 스캔 변환 지정자는 `lf`입니다.

네 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

동일한 검색 변환 지정 자가 라는 점을 제외 하 고 세 번째와 동일한 동작을 수행 합니다 `Lf` .

다섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

이 함수는 동일한 스캔 변환 지정자가 `p`라는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다.

여섯 번째 보호된 가상 구성원 함수는 다음 코드와 같습니다.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

이 함수는 비어 있지 않은 완전한 부울 입력 필드와의 일치를 시도한다는 점을 제외하면 첫 번째 함수와 동일하게 동작합니다. 성공 하면 부울 입력 필드를 형식의 값으로 변환 하 **`bool`** 고 해당 값을 *val* 에 저장 합니다.

부울 입력 필드는 두 가지 형식 중 하나를 사용합니다. `iosbase.flags & ios_base::` [Boolalpha](../standard-library/ios-functions.md#boolalpha) 가 인 경우 **`false`** 변환 된 값이 0 (의 경우 **`false`** ) 또는 1 (의 경우) 이어야 한다는 점을 제외 하면 정수 입력 필드와 동일 합니다 **`true`** . 그렇지 않으면 시퀀스는 `fac.` [falsename](../standard-library/numpunct-class.md#falsename) (의 경우 **`false`** ) 또는 `fac.` [truename](../standard-library/numpunct-class.md#truename) (의 경우)와 일치 해야 합니다 **`true`** .

### <a name="example"></a>예제

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a> num_get:: iter_type

입력 반복기에 대해 설명하는 형식입니다.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `InputIterator`의 동의어입니다.

## <a name="num_getnum_get"></a><a name="num_get"></a> num_get:: num_get

시퀀스에서 숫자 값을 추출하는 데 사용되는 `num_get` 형식의 개체에 대한 생성자입니다.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>매개 변수

*refs*\
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

### <a name="remarks"></a>설명

*Refs* 매개 변수에 사용할 수 있는 값은 다음과 같습니다.

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \> 1: 이러한 값은 정의 되지 않습니다.

소멸자는 보호되므로 직접적인 예제는 확인할 수 없습니다.

생성자는 패싯을 사용 하 여 해당 기준 개체를 초기화 `locale::` [](../standard-library/locale-class.md#facet_class) `(refs)` 합니다.

## <a name="see-also"></a>참고 항목

[\<locale>](../standard-library/locale.md)\
[패싯 클래스](../standard-library/locale-class.md#facet_class)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
