---
description: Add_volatile 클래스에 대해 자세히 알아보세요.
title: add_volatile 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: 6f138c9009d127efe2d640124d9af1e114eb0732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319871"
---
# <a name="add_volatile-class"></a>add_volatile 클래스

지정 된 **`volatile`** 형식에서 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

의 인스턴스에는 `add_volatile<T>` **`typedef`** `type` *t* 가 참조, 함수 또는 휘발성 한정 형식인 경우 t이 고, 그렇지  않으면 t 인 멤버가 있습니다 **`volatile`** . 별칭은 `add_volatile_t` 멤버에 액세스 하는 바로 가기입니다 **`typedef`** `type` .

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[remove_volatile 클래스](remove-volatile-class.md)
