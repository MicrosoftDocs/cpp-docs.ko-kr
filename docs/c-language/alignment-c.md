---
title: 맞춤(C11)
description: Microsoft Visual C 형식 맞춤에 대해 설명합니다.
ms.date: 12/10/2020
helpviewer_keywords:
- _Alignof keyword [C]
- _Alignas keyword [C]
- memory, alignment
ms.openlocfilehash: 051987ae705f84d7d4972398f742143f14b53e2b
ms.sourcegitcommit: be469dd87453255b0e35e333712c8207b09b3dd4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438895"
---
# <a name="alignment-c11"></a>맞춤(C11)

C의 하위 수준 기능 중 하나는 하드웨어 아키텍처를 최대한 활용하기 위해 메모리 내 개체의 정확한 맞춤을 지정하는 기능입니다.

데이터 크기의 배수가 되는 주소에 데이터를 저장하면 CPU가 더 효율적으로 메모리를 읽고 쓸 수 있습니다. 예를 들어 4바이트 정수는 4의 배수가 되는 주소에 저장된 경우 보다 효율적으로 액세스됩니다. 데이터가 맞춰져 있지 않으면 CPU가 더 많은 작업을 수행하여 데이터에 액세스합니다.

기본적으로 컴파일러는 데이터를 크기 기준으로 맞춥니다. 예를 들어 **`char`** 는 1바이트 경계, **`short`** 는 2바이트 경계, **`int`** , **`long`** 및 **`float`** 는 4바이트 경계, **`double`** 은 8바이트 경계 등입니다.

또한 자주 사용하는 데이터를 프로세서의 캐시 라인 크기에 맞추면 캐시 성능을 향상시킬 수 있습니다. 예를 들어 크기가 32바이트 미만인 구조체를 정의하는 경우에는 32바이트 맞춤으로 구조체의 인스턴스가 효율적으로 캐시되도록 할 수 있습니다.

일반적으로는 맞춤에 대해 걱정할 필요가 없습니다. 컴파일러는 일반적으로 대상 프로세서 및 데이터 크기를 기반으로 한 자연 경계에 데이터를 맞춥니다. 32비트 프로세서에서는 최대 4바이트 경계에 데이터를 맞추고 64비트 프로세서에서는 8바이트 경계에 데이터를 맞춥니다. 그러나 데이터 구조에 대해 사용자 지정 맞춤을 지정하여 성능 향상이나 메모리 절약 효과를 얻을 수 있는 경우도 있습니다.

C11 키워드 **`_Alignof`** 를 사용하여 형식 또는 변수의 기본 맞춤을 가져오고, **`_Alignas`** 를 사용하여 변수 또는 사용자 정의 형식에 대한 사용자 지정 맞춤을 지정합니다.

`<stdalign.h>`**`_Alignof`에 정의된 편의 매크로 **`alignof`** 및 **`alignas`** 는 각각** **`_Alignas` 및** 에 직접 매핑됩니다. 이러한 매크로는 C++에서 사용되는 키워드와 일치됩니다. 따라서 C 키워드 대신 매크로를 사용하면 두 언어 간에 공유하는 코드가 있을 경우 코드 이식성에 도움이 될 수 있습니다.

## <a name="alignas-and-_alignas-c11"></a>`alignas` 및 `_Alignas`(C11)

**`alignas`** 또는 **`_Alignas`** 를 사용하여 변수 또는 사용자 정의 형식에 대한 사용자 지정 맞춤을 지정합니다. 구조체, 공용 구조체, 열거형 또는 변수에 적용할 수 있습니다.

### <a name="alignas-syntax"></a>`alignas` 구문

```c
alignas(type)
alignas(constant-expression)
_Alignas(type)
_Alignas(constant-expression)
```

### <a name="remarks"></a>설명

`_Alignas`는 형식 정의, 비트 필드, 함수, 함수 매개 변수, 또는 `register` 지정자를 사용하여 선언된 개체의 선언에 사용할 수 없습니다.

1, 2, 4, 8, 16 등 2의 거듭제곱인 맞춤을 지정합니다. 형식의 크기보다 작은 값을 사용하지 마세요.

구조체와 공용 구조체에는 멤버 중 가장 큰 맞춤과 동일한 맞춤이 있습니다. 개별 멤버 맞춤 요구 사항이 충족되도록 패딩 바이트가 구조체 내에 추가됩니다.

선언에 여러 개의 **`alignas`** 지정자가 있는 경우(예: 구조체에 **`alignas`** 지정자가 다른 여러 멤버가 포함됨) 구조체의 맞춤은 가장 큰 멤버의 값이 됩니다.

### <a name="alignas-example"></a>`alignas` 예제

이 예제에서는 C++로 이식할 수 있으므로 편의 매크로 **`alignof`** 를 사용합니다. `_Alignof`를 사용하는 경우 동작은 동일합니다.

```c
// Compile with /std:c11

#include <stdio.h>
#include <stdalign.h>

typedef struct 
{
    int value; // aligns on a 4-byte boundary. There will be 28 bytes of padding between value and alignas
    alignas(32) char alignedMemory[32]; // assuming a 32 byte friendly cache alignment
} cacheFriendly; // this struct will be 32-byte aligned because alignedMemory is 32-byte alligned and is the largest alignment specified in the struct

int main()
{
    printf("sizeof(cacheFriendly): %d\n", sizeof(cacheFriendly)); // 4 bytes for int value + 32 bytes for alignedMemory[] + padding to ensure  alignment
    printf("alignof(cacheFriendly): %d\n", alignof(cacheFriendly)); // 32 because alignedMemory[] is aligned on a 32-byte boundary

    /* output
        sizeof(cacheFriendly): 64
        alignof(cacheFriendly): 32
    */
}
```

## <a name="alignof-and-_alignof-c11"></a>`alignof` 및 `_Alignof`(C11)

`_Alignof`는 지정된 형식의 맞춤(단위: 바이트)을 반환합니다. `size_t` 형식의 값을 반환합니다.

### <a name="alignof-syntax"></a>`alignof` 구문

```cpp
alignof(type)
_Alignof(type)
```

### <a name="alignof-example"></a>`alignof` 예제

이 예제에서는 C++로 이식할 수 있으므로 편의 매크로 **`alignof`** 를 사용합니다. `_Alignof`를 사용하는 경우 동작은 동일합니다.

```c
// Compile with /std:c11

#include <stdalign.h>
#include <stdio.h>

int main()
{
    size_t alignment = alignof(short);
    printf("alignof(short) = %d\n", alignment); // 2
    printf("alignof(int) = %d\n", alignof(int)); // 4
    printf("alignof(long) = %d\n", alignof(long)); // 4
    printf("alignof(float) = %d\n", alignof(float)); // 4
    printf("alignof(double) = %d\n", alignof(double)); // 8

    typedef struct
    {
        int a;
        double b;
    } test;

    printf("alignof(test) = %d\n", alignof(test)); // 8 because that is the alignment of the largest element in the structure

    /* output
        
       alignof(short) = 2
       alignof(int) = 4
       alignof(long) = 4
       alignof(float) = 4
       alignof(double) = 8
       alignof(test) = 8
    */
}
```

## <a name="requirements"></a>요구 사항

[std:c++11](../build/reference/std-specify-language-standard-version.md) 이상이 필요합니다.

Windows SDK 버전 10.0.20201.0 이상. 이 버전은 현재 참가자 빌드이며 [Windows 참가자 미리 보기 다운로드](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)에서 다운로드할 수 있습니다. 이 SDK를 설치 및 사용하는 방법에 대한 지침은 [C11 및 C17: 시작](https://devblogs.microsoft.com/cppblog/c11-and-c17-standard-support-arriving-in-msvc/#c11-and-c17-getting-started)을 참조하세요.

## <a name="see-also"></a>참조

[`/std`(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)\
[C++ `alignof` 및 `alignas`](../cpp/alignment-cpp-declarations.md#alignof-and-alignas)\
[데이터 맞춤의 컴파일러 처리](../cpp/alignment-cpp-declarations.md#compiler-handling-of-data-alignment)