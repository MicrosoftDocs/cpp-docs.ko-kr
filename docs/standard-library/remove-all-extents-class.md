---
description: Remove_all_extents 클래스에 대해 자세히 알아보세요.
title: remove_all_extents 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_all_extents
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
ms.openlocfilehash: a6c798e1f128b10ef94061573c93c3bb9e3aa4f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159728"
---
# <a name="remove_all_extents-class"></a>remove_all_extents 클래스

배열 형식에서 배열이 아닌 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct remove_all_extents;

template <class T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

인스턴스는 `remove_all_extents<T>` 모든 배열 차원이 제거 된 배열 형식 *t* 의 요소 형식인 수정 된 형식을 보유 합니다. *t* 가 배열 형식이 아닌 경우에는 *t* 입니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_all_extents<int> == "
        << typeid(std::remove_all_extents_t<int>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5]> == "
        << typeid(std::remove_all_extents_t<int[5]>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5][10]> == "
        << typeid(std::remove_all_extents_t<int[5][10]>).name()
        << std::endl;

    return (0);
    }
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[remove_extent 클래스](../standard-library/remove-extent-class.md)
