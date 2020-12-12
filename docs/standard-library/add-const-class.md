---
description: Add_const 클래스에 대해 자세히 알아보세요.
title: add_const 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: ce1dd895a5968234feca7905d3b9f8d571336053
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319946"
---
# <a name="add_const-class"></a>add_const 클래스

형식에서 const 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>매개 변수

*Ty*\
수정할 형식입니다.

## <a name="remarks"></a>설명

형식 한정자의 인스턴스는 *ty* 가 참조, 함수 또는 const 한정 형식인 경우 *ty* 인 수정 된 형식을 보유 합니다. 그렇지 않은 경우에는 `const Ty` 입니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[remove_const 클래스](remove-const-class.md)
