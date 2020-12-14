---
description: '&lt;System_error 함수에 대해 자세히 알아보세요. &gt;'
title: '&lt;system_error&gt; 함수'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 6d0283ca2a094e6257841569fcf7043b51ba4b1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259437"
---
# <a name="ltsystem_errorgt-functions"></a>&lt;system_error&gt; 함수

## <a name="generic_category"></a><a name="generic_category"></a> generic_category

일반 오류의 범주를 나타냅니다.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>설명

`generic_category`개체는 [error_category](../standard-library/error-category-class.md)의 구현입니다.

## <a name="is_error_code_enum_v"></a><a name="is_error_code_enum_v"></a> is_error_code_enum_v

```cpp
template <class T>
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a><a name="is_error_condition_enum_v"></a> is_error_condition_enum_v

```cpp
template <class T>
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a><a name="make_error_code"></a> make_error_code

오류 코드 개체를 만듭니다.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>매개 변수

*메시지가*\
`std::errc`오류 코드 개체에 저장할 열거형 값입니다.

### <a name="return-value"></a>반환 값

오류 코드 개체입니다.

### <a name="remarks"></a>설명

## <a name="make_error_condition"></a><a name="make_error_condition"></a> make_error_condition

오류 조건 개체를 만듭니다.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>매개 변수

*메시지가*\
`std::errc`오류 코드 개체에 저장할 열거형 값입니다.

### <a name="return-value"></a>반환 값

오류 조건 개체입니다.

### <a name="remarks"></a>설명

## <a name="system_category"></a><a name="system_category"></a> system_category

하위 수준 시스템 오버플로로 인해 발생하는 오류의 범주를 나타냅니다.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>설명

`system_category`개체는 [error_category](../standard-library/error-category-class.md)의 구현입니다.
