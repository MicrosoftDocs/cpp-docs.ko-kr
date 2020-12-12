---
description: Add_lvalue_reference 클래스에 대해 자세히 알아보세요.
title: add_lvalue_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 07bbfb96241b12c409b8754bdb4854e994c65cc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319911"
---
# <a name="add_lvalue_reference-class"></a>add_lvalue_reference 클래스

형식에서 형식에 대한 참조를 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct add_lvalue_reference;

template <class T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

형식 한정자의 인스턴스는 *t* 가 lvalue 참조 이면 *t* 인 수정 된 형식을 보유 하 고, 그렇지 않으면 `T&` 입니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

using namespace std;
int main()
{
    int val = 0;
    add_lvalue_reference_t<int> p = (int&)val;
    p = p;  // to quiet "unused" warning
    cout << "add_lvalue_reference_t<int> == "
        << typeid(p).name() << endl;

    return (0);
}
```

```Output
add_lvalue_reference_t<int> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[remove_reference 클래스](remove-reference-class.md)
