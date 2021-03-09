---
title: '오류: 동적 스택 버퍼 오버플로입니다.'
description: Alloca 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- dynamic-stack-buffer-overflow
helpviewer_keywords:
- dynamic-stack-buffer-overflow error
- AddressSanitizer error dynamic-stack-buffer-overflow
ms.openlocfilehash: 4ccf8c9bbab7eb14cac80f0f1d3f9478fc035f8b
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471251"
---
# <a name="error-dynamic-stack-buffer-overflow"></a>오류: `dynamic-stack-buffer-overflow`

> 주소 Sanitizer 오류: 동적 스택 버퍼 오버플로

이 예제에서는 스택 할당 개체의 경계 외부에 있는 버퍼 액세스의 결과로 생성 되는 오류를 보여 줍니다.

## <a name="example---alloca-overflow-right"></a>예- `alloca` 오버플로 (오른쪽)

```cpp
// example1.cpp
// dynamic-stack-buffer-overflow error
#include <malloc.h>

__declspec(noinline)
void foo(int index, int len) {

    volatile char *str = (volatile char *)_alloca(len);

    //    reinterpret_cast<long>(str) & 31L;

    str[index] = '1'; // Boom !
}

int main(int argc, char **argv) {

    foo(33, 10);
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/dynamic-stack-buffer-overflow-example-1.png" alt-text="예 1에서 동적 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---alloca-overflow-left"></a>예제- `alloca` 오버플로 (왼쪽)

```cpp
// example2.cpp
// dynamic-stack-buffer-overflow error
#include <malloc.h>

__declspec(noinline)
void foo(int index, int len) {

    volatile char *str = (volatile char *)_alloca(len);

    str[index] = '1';  // Boom!
}

int main(int argc, char **argv) {
    foo(-1, 10);
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---alloca-overflow-left"></a>결과 오류- `alloca` 오버플로 (왼쪽)

:::image type="content" source="media/dynamic-stack-buffer-overflow-example-2.png" alt-text="예 2에서 동적 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---several-calls-to-alloca"></a>예-에 대 한 여러 호출 `alloca`

```cpp
// example3.cpp
// dynamic-stack-buffer-overflow error
#include <stdio.h>
#include <stdlib.h>
#include <malloc.h>

#define SIZE 7
extern void nothing();
int x=13,*aa,*bb,y=0;
int fail = 0;
int tmp;

int main()
{
    int* cc;
    int i;
    int k = 17;
    __try {
        tmp = k;
        aa = (int*)_alloca(SIZE * sizeof(int));
        if (((int)aa) & 0x3)
            fail = 1;
        for (i = 0; i < SIZE; i++) {
            aa[i] = x + 1 + i;
        }
        bb = (int*)_alloca(x * sizeof(int));
        if (((int)bb) & 0x3)
            fail = 1;

        for (i = 0; i < x; i++) {
            bb[i] = 7;
            bb[i] = bb[i] + i;
        }
        {
            int s = 112728283;
            int ar[8];
            for (i = 0; i < 8; i++)
                ar[i] = s * 17 * i;
        }

        cc = (int*)_alloca(x);
        if (((int)cc) & 0x3)
            fail = 1;

        cc[0] = 0;
        cc[1] = 1;
        cc[2] = 2;
        cc[3] = 3;             // <--- Boom!
        for (i = 0; i < x; i++)
            if (bb[i] != (7 + i))
                fail = 1;
        if (tmp != k)
            fail = 1;
        if (fail) {
            printf("fail\n");
            exit(7);
        }
        printf("%d\n", (*cc) / y);
        printf("fail\n");
        exit(7);
    }
    __except (1)
    {
        for (i = 0; i < SIZE; i++)
            if (aa[i] != (x + i + 1))
                fail = 1;
        if (fail) {
            printf("fail\n");
            exit(7);
        }
        printf("pass\n");
        exit(0);
    }
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe
```

### <a name="resulting-error---several-calls-to-alloca"></a>결과 오류-alloca에 대 한 여러 호출

:::image type="content" source="media/dynamic-stack-buffer-overflow-example-3.png" alt-text="예 3에서 동적 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
