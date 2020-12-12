---
description: Is_compound 클래스에 대해 자세히 알아보세요.
title: is_compound 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: 0bdd1b2f8c7ab827d9bed1025e30140244381c3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323832"
---
# <a name="is_compound-class"></a>is_compound 클래스

지정된 형식이 기본 형식이 아닌지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 **`false`** *Ty* 형식이 기본 형식 ( [is_fundamental](../standard-library/is-fundamental-class.md) 보유 하 고 있는 경우) 인 경우에는이 고 \<Ty> **`true`** , 그렇지 않으면 **`true`** 입니다. 따라서 **`true`** *Ty* 가 배열 형식, 함수 형식, **`void`** 또는 개체 또는 함수에 대 한 포인터, 참조, 클래스, 공용 구조체, 열거형 또는 비정적 클래스 멤버에 대 한 포인터 또는이 중 하나의 *cv 한정* 형식인 경우 조건자가 포함 됩니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[is_class 클래스](../standard-library/is-class-class.md)
