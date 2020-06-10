---
title: add_pointer 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 8adeffd0352d04fe844b286ea7456c66e907a0a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619257"
---
# <a name="add_pointer-class"></a>add_pointer 클래스

지정된 형식에서 포인터-형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

멤버 **typedef** 는 `type` 와 동일한 형식의 이름을 갖습니다 `remove_reference<T>::type*` . 별칭은 `add_pointer_t` 멤버 **typedef** 에 액세스 하기 위한 바로 가기입니다 `type` .

참조에서 포인터를 만드는 것은 잘못이기 때문에 `add_pointer`가 포인터-형식을 만들기 전에 지정된 형식에서 참조(있는 경우)를 제거합니다. 결과적으로, 형식이 참조인지 걱정하지 않고도 `add_pointer`를 포함하여 형식을 사용할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `add_pointer` 형식이 해당 형식의 포인터와 같은 경우를 보여 줍니다.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[remove_pointer 클래스](remove-pointer-class.md)
