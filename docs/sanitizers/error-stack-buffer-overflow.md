---
title: '오류: 스택 버퍼 오버플로입니다.'
description: 스택 버퍼 오버플로 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- stack-buffer-overflow
helpviewer_keywords:
- stack-buffer-overflow error
- AddressSanitizer error stack-buffer-overflow
ms.openlocfilehash: 52b4dcf2caad04703b9fa407f0546e94528849c4
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471226"
---
# <a name="error-stack-buffer-overflow"></a>오류: `stack-buffer-overflow`

> 주소 Sanitizer 오류: 스택 버퍼 오버플로입니다.

스택 버퍼 오버플로는 C 또는 c + +에서 여러 가지 방법으로 발생할 수 있습니다. 간단한 다시 컴파일을 통해 catch 할 수 있는이 범주의 오류에 대 한 몇 가지 예제를 제공 합니다.

## <a name="example---stack-buffer-overflow"></a>예제-스택 버퍼 오버플로

```cpp
// example1.cpp
// stack-buffer-overflow error
#include <string.h>

int main(int argc, char **argv) {
    char x[10];
    memset(x, 0, 10);
    int res = x[argc * 10];  // Boom! Classic stack buffer overflow

    return res;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/stack-buffer-overflow-example-1.png" alt-text="예 1에서 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---stack-buffer-math"></a>예제-스택 버퍼 수학

```cpp
// example2.cpp
// stack-buffer-overflow error
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

int main(int argc, char **argv) {
    assert(argc >= 2);
    int idx = atoi(argv[1]);
    char AAA[10], BBB[10], CCC[10];
    memset(AAA, 0, sizeof(AAA));
    memset(BBB, 0, sizeof(BBB));
    memset(CCC, 0, sizeof(CCC));
    int res = 0;
    char *p = AAA + idx;
    printf("AAA: %p\ny: %p\nz: %p\np: %p\n", AAA, BBB, CCC, p);

    return *(short*)(p) + BBB[argc % 2] + CCC[argc % 2];  // Boom! ... when argument is 9
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe 9
```

### <a name="resulting-error---stack-buffer-math"></a>결과 오류-스택 버퍼 수학

:::image type="content" source="media/stack-buffer-overflow-example-2.png" alt-text="예 2에서 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---improper-down-cast-on-stack"></a>예-스택에서 부적절 한 하향 캐스트

```cpp
// example3.cpp
// stack-buffer-overflow error
class Parent {
public:
    int field;
};

class Child : public Parent {
public:
    int extra_field;
};

int main(void) {

    Parent p;
    Child *c = (Child*)&p;  // Boom !
    c->extra_field = 42;

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe
```

### <a name="resulting-error---improper-down-cast-on-stack"></a>결과 오류-스택에 잘못 된 캐스팅이 있습니다.

:::image type="content" source="media/stack-buffer-overflow-example-3.png" alt-text="예제 3에서 스택 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
