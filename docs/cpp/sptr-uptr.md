---
description: '자세히 알아보기: __sptr, __uptr'
title: __sptr, __uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: 13e365e0e8258c1860df2f107a3dad0ade76e529
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113729"
---
# <a name="__sptr-__uptr"></a>__sptr, __uptr

**Microsoft 전용**

**`__sptr`** **`__uptr`** 32 비트 포인터 선언에서 또는 한정자를 사용 하 여 컴파일러가 32 비트 포인터를 64 비트 포인터로 변환 하는 방법을 지정 합니다. 예를 들어 32비트 포인터는 64비트 포인터 변수에 할당되거나 64비트 플랫폼에서 역참조될 때 변환됩니다.

64비트 플랫폼 지원에 대한 Microsoft 설명서에서는 경우에 따라 32비트 포인터의 최상위 비트를 부호 비트로 지칭합니다. 기본적으로 컴파일러는 부호 확장을 사용하여 32비트 포인터를 64비트 포인터로 변환합니다. 즉, 64비트 포인터의 최하위 32비트는 32비트 포인터의 값으로 설정되며 최상위 32비트는 32비트 포인터의 부호 비트 값으로 설정됩니다. 이 변환은 부호 비트가 0인 경우 올바른 결과를 생성하지만 부호 비트가 1인 경우에는 올바른 결과를 생성하지 않습니다. 예를 들어 32비트 주소 0x7FFFFFFF는 동일한 64비트 주소 0x000000007FFFFFFF를 생성하지만 32비트 주소 0x80000000은 0xFFFFFFFF80000000으로 올바르지 않게 변경됩니다.

**`__sptr`** 또는 부호 있는 포인터 한정자는 포인터 변환이 64 비트 포인터의 가장 중요 한 비트를 32 비트 포인터의 부호 비트로 설정 하도록 지정 합니다. **`__uptr`** 또는 부호 없는 포인터 한정자는 변환이 가장 중요 한 비트를 0으로 설정 하도록 지정 합니다. 다음 선언에서는 **`__sptr`** **`__uptr`** 두 개의 정규화 되지 않은 포인터, [__ptr32](../cpp/ptr32-ptr64.md) 형식으로 정규화 된 두 개의 포인터 및 함수 매개 변수와 함께 사용 되는 및 한정자를 보여 줍니다.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

**`__sptr`** 포인터 선언에 및 한정자를 사용 **`__uptr`** 합니다. [포인터 형식 한정자](../c-language/pointer-declarations.md)의 위치에 한정자를 사용 합니다. 즉, 한정자가 별표 다음에와 야 합니다. [멤버에 대 한 포인터](../cpp/pointers-to-members.md)에는 한정자를 사용할 수 없습니다. 한정자는 포인터 선언이 아닌 선언에 영향을 주지 않습니다.

이전 버전과의 호환성을 위해 **_sptr** 및 **_uptr** 는에 대 한 동의어 이며, **`__sptr`** **`__uptr`** 컴파일러 옵션 [/za \( 사용 안 함 언어 확장)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 되어 있지 않습니다.

## <a name="example"></a>예제

다음 예제에서는 및 한정자를 사용 하는 32 비트 포인터를 선언 하 고 **`__sptr`** **`__uptr`** 각 32 비트 포인터를 64 비트 포인터 변수에 할당 한 다음 각 64 비트 포인터의 16 진수 값을 표시 합니다. 이 예제는 네이티브 64비트 컴파일러로 컴파일되며 64비트 플랫폼에서 실행됩니다.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)
