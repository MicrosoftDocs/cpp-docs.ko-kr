---
description: Aligned_union 클래스에 대해 자세히 알아보세요.
title: aligned_union 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: acb55501edc1a390064cb943a710f05f2ecea811
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163667"
---
# <a name="aligned_union-class"></a>aligned_union 클래스

공용 구조체 형식 및 필요한 크기를 저장할 수 있도록 적절하게 맞춰지고 충분히 큰 POD 형식을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>매개 변수

*길이가*\
공용 구조체에서 가장 큰 형식의 맞춤 값입니다.

*종류*\
기본 공용 구조체의 고유 형식입니다.

## <a name="remarks"></a>설명

클래스 템플릿을 사용 하 여 초기화 되지 않은 저장소에 공용 구조체를 저장 하는 데 필요한 맞춤 및 크기를 가져옵니다. 멤버 typedef는 `type` *형식* 에 나열 된 모든 형식의 저장소에 적합 한 POD 형식의 이름을, 최소 크기는 *Len* 입니다. 형식의 정적 멤버는 `alignment_value` `std::size_t` *형식* 에 나열 된 모든 형식에 필요한 가장 엄격한 맞춤을 포함 합니다.

## <a name="example"></a>예제

다음 예제에서는 `aligned_union`을 사용하여 공용 구조체 배치를 위한 맞춤화된 스택 버퍼를 할당하는 방법을 보여줍니다.

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[alignment_of 클래스](alignment-of-class.md)
