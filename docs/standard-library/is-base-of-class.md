---
description: Is_base_of 클래스에 대해 자세히 알아보세요.
title: is_base_of 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: 6cb2b55a6df687fbb7da74ca3c696a8a9b0ffbad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231266"
---
# <a name="is_base_of-class"></a>is_base_of 클래스

한 형식이 다른 형식의 기본 형식인지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>매개 변수

*하단*\
테스트할 기본 클래스입니다.

*가져온*\
테스트할 파생 형식입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 형식 *기준이* *파생* 형식의 기본 클래스 이면 true이 고, 그렇지 않으면 false입니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_convertible 클래스](../standard-library/is-convertible-class.md)
