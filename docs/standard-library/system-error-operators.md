---
title: '&lt;system_error&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d5c8f49c4a38862d62b7fe8212d98c87949fecfc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653373"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt; 연산자

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

연산자의 좌변에 있는 개체가 우변에 있는 개체와 같은지 테스트합니다.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*left*|같은지 테스트할 개체입니다.|
|*right*|같은지 테스트할 개체입니다.|

### <a name="return-value"></a>반환 값

개체가 같으면 **true**이고, 개체가 같지 않으면 **false**입니다.

### <a name="remarks"></a>설명

함수는 `left.category() == right.category() && left.value() == right.value()`를 반환합니다.

## <a name="op_neq"></a>  operator!=

연산자의 좌변에 있는 개체가 우변에 있는 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*left*|같지 않은지 테스트할 개체입니다.|
|*right*|같지 않은지 테스트할 개체입니다.|

### <a name="return-value"></a>반환 값

**true** 에 전달 된 개체가 *왼쪽* 에 전달 된 개체와 같지 않은 *오른쪽*이 고 그렇지 않으면 **false**합니다.

### <a name="remarks"></a>설명

함수는 `!(left == right)`를 반환합니다.

## <a name="op_lt"></a>  operator&lt;

개체가 비교를 위해 전달된 개체보다 작은지 여부를 테스트합니다.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*left*|비교할 개체입니다.|
|*right*|비교할 개체입니다.|

### <a name="return-value"></a>반환 값

**true 이면** 에 전달 된 개체가 *왼쪽* 에 전달 되는 개체 보다 작습니다 *오른쪽*; 그렇지 않으면 **false**합니다.

### <a name="remarks"></a>설명

이 함수는 오류 순서를 테스트합니다.

## <a name="see-also"></a>참고자료

[<system_error>](../standard-library/system-error.md)<br/>
