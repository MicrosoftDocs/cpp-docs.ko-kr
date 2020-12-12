---
description: Is_member_pointer 클래스에 대해 자세히 알아보세요.
title: is_member_pointer 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_pointer
helpviewer_keywords:
- is_member_pointer class
- is_member_pointer
ms.assetid: da07ff4e-9ee0-4baa-ad93-1741f10913d1
ms.openlocfilehash: e1e2e5be39859109dd707f55a368fabe19f477a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323648"
---
# <a name="is_member_pointer-class"></a>is_member_pointer 클래스

형식이 멤버에 대한 포인터인지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_member_pointer;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 멤버 함수에 대 한 포인터 이거나 멤버 개체에 대 한 포인터 이거나 그 중 하나의 폼인 경우 true이 고 `cv-qualified` 그렇지 않은 경우 false입니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_member_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_pointer<trivial *> == false
is_member_pointer<int trivial::*> == true
is_member_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_member_function_pointer 클래스](../standard-library/is-member-function-pointer-class.md)\
[is_member_object_pointer 클래스](../standard-library/is-member-object-pointer-class.md)\
[is_pointer 클래스](../standard-library/is-pointer-class.md)
