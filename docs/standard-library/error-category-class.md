---
description: Error_category 클래스에 대해 자세히 알아보세요.
title: error_category 클래스
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 25ad7f6acfe50cdcc0c4b9df44fb3b8b6244f569
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232657"
---
# <a name="error_category-class"></a>error_category 클래스

오류 코드 범주를 설명하는 개체에 대한 추상, 공통 기본을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>설명

미리 정의된 두 개의 [generic_category](../standard-library/system-error-functions.md#generic_category) 및 [system_category](../standard-library/system-error-functions.md#system_category) 개체가 `error_category`를 구현합니다.

## <a name="members"></a>멤버

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[value_type](#value_type)|저장된 오류 코드 값을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[default_error_condition](#default_error_condition)|오류 조건 개체에 대한 오류 코드 값을 저장합니다.|
|[상응](#equivalent)|오류 개체가 동일한지 여부를 지정하는 값을 반환합니다.|
|[generic_category](#generic)||
|[message](#message)|지정된 오류 코드의 이름을 반환합니다.|
|[name](#name)|범주 이름을 반환합니다.|
|[system_category](#system)||

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 =](#op_as)|대입 연산자입니다.|
|[연산자 = =](#op_eq_eq)|`error_category` 개체가 같은지 테스트합니다.|
|[연산자! =](#op_neq)|`error_category` 개체가 같지 않은지 테스트합니다.|
|[연산자<](#op_lt)|[error_category](../standard-library/error-category-class.md) 개체가 비교를 위해 전달된 `error_category` 개체보다 작은지 테스트합니다.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

오류 조건 개체에 대한 오류 코드 값을 저장합니다.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>매개 변수

`_Errval`\
[error_condition](../standard-library/error-condition-class.md)에 저장할 오류 코드 값입니다.

### <a name="return-value"></a>반환 값

`error_condition(_Errval, *this)`를 반환합니다.

### <a name="remarks"></a>설명

### <a name="equivalent"></a><a name="equivalent"></a> 해당 항목

오류 개체가 동일한지 여부를 지정하는 값을 반환합니다.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>매개 변수

*_Errval*\
비교할 오류 코드 값입니다.

*_Cond*\
비교할 [error_condition](../standard-library/error-condition-class.md) 개체입니다.

*_Code*\
비교할 [error_code](../standard-library/error-code-class.md) 개체입니다.

#### <a name="return-value"></a>반환 값

**`true`** 범주와 값이 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

#### <a name="remarks"></a>설명

첫 번째 멤버 함수는 `*this == _Cond.category() && _Cond.value() == _Errval`을 반환합니다.

두 번째 멤버 함수는 `*this == _Code.category() && _Code.value() == _Errval`를 반환합니다.

### <a name="generic_category"></a><a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a> 메시지

지정된 오류 코드의 이름을 반환합니다.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>매개 변수

*짧은*\
설명할 오류 코드 값입니다.

#### <a name="return-value"></a>반환 값

범주에 대 한 오류 코드 *val* 의 설명이 포함 된 이름을 반환 합니다. 오류 코드를 인식할 수 없는 경우는를 반환 `"unknown error"` 합니다.

#### <a name="remarks"></a>설명

### <a name="name"></a><a name="name"></a> 이름

범주 이름을 반환합니다.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>반환 값

범주 이름을 null 종료 바이트 문자열로 반환합니다.

### <a name="operator"></a><a name="op_as"></a> 연산자 =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

`error_category` 개체가 같은지 테스트합니다.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
같은지 테스트할 개체입니다.

#### <a name="return-value"></a>반환 값

**`true`** 개체가 같으면이 고, 그렇지 않으면입니다. **`false`** 개체가 같지 않으면입니다.

#### <a name="remarks"></a>설명

이 멤버 연산자는 `this == &right`를 반환합니다.

### <a name="operator"></a><a name="op_neq"></a> 연산자! =

`error_category` 개체가 같지 않은지 테스트합니다.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
같지 않은지 테스트할 개체입니다.

#### <a name="return-value"></a>반환 값

**`true`**`error_category`개체가 `error_category` *오른쪽* 에 전달 된 개체와 같지 않으면이 고, 그렇지 않으면 **`false`** 입니다.

#### <a name="remarks"></a>설명

멤버 연산자는 `(!*this == right)`를 반환합니다.

### <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

[error_category](../standard-library/error-category-class.md) 개체가 비교를 위해 전달된 `error_category` 개체보다 작은지 테스트합니다.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 `error_category` 개체입니다.

#### <a name="return-value"></a>반환 값

**`true`**`error_category`개체가 `error_category` 비교를 위해 전달 된 개체 보다 작은 경우 그렇지 않으면 **`false`** 입니다.

#### <a name="remarks"></a>설명

멤버 연산자는 `this < &right`를 반환합니다.

### <a name="system_category"></a><a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a> value_type

저장된 오류 코드 값을 나타내는 형식입니다.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>설명

이 형식 정의는의 동의어입니다 **`int`** .
