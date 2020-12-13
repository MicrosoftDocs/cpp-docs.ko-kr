---
description: '자세한 정보: __func__'
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 6e075d0f566bb8c3eb72e62a30a36ef80528647b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337703"
---
# <a name="__func__"></a>__func__

**(C + + 11)** &#95;&#95;func&#95;&#95; 의 미리 정의 된 식별자는 바깥쪽 함수의 정규화 되지 않은 이름 및 되지 않은 이름이 포함 된 문자열로 암시적으로 정의 됩니다. &#95;&#95;func&#95;&#95; 는 c + + 표준에 의해 위임 되며 Microsoft 확장이 아닙니다.

## <a name="syntax"></a>구문

```cpp
__func__
```

## <a name="return-value"></a>Return Value

함수 이름을 포함 하는 문자의 null로 끝나는 const char 배열을 반환 합니다.

## <a name="example"></a>예제

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>요구 사항

C++11
