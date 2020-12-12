---
description: Is_default_constructible 클래스에 대해 자세히 알아보세요.
title: is_default_constructible Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_default_constructible
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
ms.openlocfilehash: 9c5365ee6e2e2b7382b5dd5f17cce2afd0ce8932
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323784"
---
# <a name="is_default_constructible-class"></a>is_default_constructible Class

형식에 기본 생성자가 있는지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 기본 생성자가 있는 클래스 형식인 경우 true이 고 그렇지 않은 경우 false입니다. 이것은 조건자 `is_constructible<T>`에 해당합니다. *T* 형식은 완전 한 형식, **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
