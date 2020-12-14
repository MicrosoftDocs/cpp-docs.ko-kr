---
description: Is_pointer 클래스에 대해 자세히 알아보세요.
title: is_pointer 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pointer
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
ms.openlocfilehash: 003f25a40edd3f4c0b80a8402d38027cd81949cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230642"
---
# <a name="is_pointer-class"></a>is_pointer 클래스

형식이 포인터인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이에 대 한 포인터인 경우 true이 고, 개체에 대 한 포인터 또는 함수에 대 한 포인터 이거나, 함수에 대 **`void`** 한 포인터 이거나 `cv-qualified` , 그렇지 않으면 false입니다. `is_pointer` *Ty* 가 멤버에 대 한 포인터 또는 멤버 함수에 대 한 포인터인 경우는 false입니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }
```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_member_pointer 클래스](../standard-library/is-member-pointer-class.md)\
[is_reference 클래스](../standard-library/is-reference-class.md)
