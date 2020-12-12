---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4703'
title: 컴파일러 경고(수준 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 8c31ed9be7dc271f9de4471792ccd6517091cab6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133785"
---
# <a name="compiler-warning-level-4-c4703"></a>컴파일러 경고(수준 4) C4703

초기화되지 않았을 수 있는 로컬 포인터 변수 'name'이(가) 사용되었습니다.

값을 할당 하지 않고 로컬 포인터 변수 *이름을* 사용 했을 수 있습니다. 이로 인해 예기치 않은 결과가 발생할 수 있습니다.

## <a name="example"></a>예제

다음 코드는 C4701 및 C4703을 생성합니다.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

이 경고를 해결하려면 다음 예제에 표시된 것처럼 변수를 초기화합니다.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

int main()
{
    func(9);
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 경고 (수준 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[경고,/sdl 및 초기화 되지 않은 변수 검색 향상](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
