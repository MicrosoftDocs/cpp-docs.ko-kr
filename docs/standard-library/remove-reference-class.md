---
description: Remove_reference 클래스에 대해 자세히 알아보세요.
title: remove_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_reference
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
ms.openlocfilehash: ccde3e2070e38ca06ca519b7c184fce7dcdbb90d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159624"
---
# <a name="remove_reference-class"></a>remove_reference 클래스

형식에서 비참조 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct remove_reference;

template <class T>
using remove_reference_t = typename remove_reference<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

의 인스턴스는 `remove_reference<T>` `T1` *t* 가 형식이 면이 고 `T1&` , 그렇지 않으면 인 수정 된 형식을 보유 합니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_reference_t<int&> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_reference_t<int&> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_reference_t<int&> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[add_lvalue_reference 클래스](../standard-library/add-lvalue-reference-class.md)
