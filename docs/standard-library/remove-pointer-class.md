---
description: Remove_pointer 클래스에 대해 자세히 알아보세요.
title: remove_pointer 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_pointer
helpviewer_keywords:
- remove_pointer class
- remove_pointer
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
ms.openlocfilehash: 8739fcd197dc59f5163740d1290abd3faee1922a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159663"
---
# <a name="remove_pointer-class"></a>remove_pointer 클래스

포인터부터 형식까지 다양한 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct remove_pointer;

template <class T>
using remove_pointer_t = typename remove_pointer<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

의 인스턴스는 `remove_pointer<T>` `T1` *t* 가,, 또는 형식인 경우 인 수정 된 형식을 보유 합니다 `T1*` `T1* const` `T1* volatile` `T1* const volatile` . 그렇지 않은 경우에는입니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_pointer_t<int *> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_pointer_t<int *> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_pointer_t<int *> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[add_pointer 클래스](../standard-library/add-pointer-class.md)
