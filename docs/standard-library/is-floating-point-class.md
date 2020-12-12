---
description: Is_floating_point 클래스에 대해 자세히 알아보세요.
title: is_floating_point 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_floating_point
helpviewer_keywords:
- is_floating_point class
- is_floating_point
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
ms.openlocfilehash: e1ace01a88c103646e9daa6ece82b9c3c3c2978a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230980"
---
# <a name="is_floating_point-class"></a>is_floating_point 클래스

형식이 부동 소수점인지를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_floating_point;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 부동 소수점 형식 이거나 부동 소수점 형식의 폼인 경우 true이 고 `cv-qualified` 그렇지 않은 경우 false입니다.

부동 소수점 형식은, 또는 중 하나 **`float`** 입니다 **`double`** **`long double`** .

## <a name="example"></a>예제

```cpp
// std__type_traits__is_floating_point.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_floating_point<trivial> == " << std::boolalpha
        << std::is_floating_point<trivial>::value << std::endl;
    std::cout << "is_floating_point<int> == " << std::boolalpha
        << std::is_floating_point<int>::value << std::endl;
    std::cout << "is_floating_point<float> == " << std::boolalpha
        << std::is_floating_point<float>::value << std::endl;

    return (0);
    }
```

```Output
is_floating_point<trivial> == false
is_floating_point<int> == false
is_floating_point<float> == true
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_integral 클래스](../standard-library/is-integral-class.md)
