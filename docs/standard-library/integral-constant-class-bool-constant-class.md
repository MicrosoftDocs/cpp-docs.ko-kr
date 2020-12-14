---
description: Integral_constant 클래스, bool_constant 클래스에 대해 자세히 알아보세요.
title: integral_constant 클래스, bool_constant 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: a910581af81742c32f4eb32a1f8f625cbc6cd346
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231539"
---
# <a name="integral_constant-class-bool_constant-class"></a>integral_constant 클래스, bool_constant 클래스

형식 및 값에서 정수 계열 상수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>매개 변수

*트*\
상수의 형식입니다.

*hyper-v*\
상수의 값입니다.

## <a name="remarks"></a>설명

`integral_constant`정수 계열 형식 *T* 와 해당 형식의 값 *v* 를 사용 하 여 특수화 된 경우 클래스 템플릿은 지정 된 값을 사용 하 여 해당 정수 계열 형식의 상수를 보유 하는 개체를 나타냅니다. `type`이라는 멤버는 생성된 템플릿 특수화 형식에 대한 별칭이고, `value` 멤버는 특수화를 만드는 데 사용되는 *v* 값을 포함합니다.

`bool_constant`클래스 템플릿은를 `integral_constant` T 인수로 사용 하는의 명시적 부분 특수화입니다 **`bool`** . 

## <a name="example"></a>예제

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }
```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
