---
description: Is_class 클래스에 대해 자세히 알아보세요.
title: is_class 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_class
helpviewer_keywords:
- is_class class
- is_class
ms.assetid: 96fc34a3-a81b-4ec6-b7fb-baafde1a0f4e
ms.openlocfilehash: 9aa7646ca46aa82176c97d90d42a65ad76bc45eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231253"
---
# <a name="is_class-class"></a>is_class 클래스

형식이 클래스인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_class;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 또는 형식으로 정의 된 형식인 경우 true이 고, **`class`** **`struct`** `cv-qualified` 그렇지 않으면 false입니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_class.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_class<trivial> == " << std::boolalpha
        << std::is_class<trivial>::value << std::endl;
    std::cout << "is_class<int> == " << std::boolalpha
        << std::is_class<int>::value << std::endl;

    return (0);
    }
```

```Output
is_class<trivial> == true
is_class<int> == false
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_compound 클래스](../standard-library/is-compound-class.md)\
[is_union 클래스](../standard-library/is-union-class.md)
