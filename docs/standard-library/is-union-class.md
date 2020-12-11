---
description: Is_union 클래스에 대해 자세히 알아보세요.
title: is_union 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_union
helpviewer_keywords:
- is_union class
- is_union
ms.assetid: 80eda256-40b8-4db5-9ac1-d58bb8032a3e
ms.openlocfilehash: be095053523a0348632d2c81c3a3a7eafe8593d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154307"
---
# <a name="is_union-class"></a>is_union 클래스

형식이 공용 구조체인지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_union;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 공용 구조체 형식 또는 `cv-qualified` 공용 구조체 형식의 형식이 면 true이 고, 그렇지 않으면 false입니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_union.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

union ints
    {
    int in;
    long lo;
    };

int main()
    {
    std::cout << "is_union<trivial> == " << std::boolalpha
        << std::is_union<trivial>::value << std::endl;
    std::cout << "is_union<int> == " << std::boolalpha
        << std::is_union<int>::value << std::endl;
    std::cout << "is_union<ints> == " << std::boolalpha
        << std::is_union<ints>::value << std::endl;

    return (0);
    }
```

```Output
is_union<trivial> == false
is_union<int> == false
is_union<ints> == true
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_class 클래스](../standard-library/is-class-class.md)
