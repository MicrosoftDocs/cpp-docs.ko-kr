---
title: '오류: 힙 버퍼 오버플로입니다.'
description: 힙 변수 오버플로 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷
ms.date: 03/02/2021
f1_keywords:
- heap-buffer-overflow
helpviewer_keywords:
- heap-buffer-overflow error
- AddressSanitizer error heap-buffer-overflow
ms.openlocfilehash: 7eec8d0fa8c7382a5a4ecea9811298aaaba760a2
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471136"
---
# <a name="error-heap-buffer-overflow"></a>오류: `heap-buffer-overflow`

> 주소 Sanitizer 오류: 힙 버퍼 오버플로입니다.

이 예제에서는 메모리 액세스가 힙 할당 개체의 범위 외부에서 발생 하는 경우 발생 하는 오류를 보여 줍니다.

## <a name="example---classic-heap-buffer-overflow"></a>예제-클래식 힙 버퍼 오버플로

```cpp
// example1.cpp
// heap-buffer-overflow error
#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv) {

    char *x = (char*)malloc(10 * sizeof(char));
    memset(x, 0, 10);
    int res = x[argc * 10];  // Boom!

    free(x);
    return res;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/heap-buffer-overflow-example-1.png" alt-text="예 1에서 힙 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---improper-down-cast"></a>예-잘못 된 하향 캐스트

```cpp
// example2.cpp
// heap-buffer-overflow error
class Parent {
public:
    int field;
};

class Child : public Parent {
public:
    int extra_field;
};

int main(void) {
    Parent *p = new Parent;
    Child *c = (Child*)p;  // Intentional error here!
    c->extra_field = 42;

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---improper-down-cast"></a>결과 오류-잘못 된 하향 캐스트

:::image type="content" source="media/heap-buffer-overflow-example-2.png" alt-text="예 2에서 힙 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---strncpy-into-heap"></a>예-strncpy 힙

```cpp
// example3.cpp
// heap-buffer-overflow error
#include <string.h>
#include <stdlib.h>

int main(int argc, char **argv) {

    char *hello = (char*)malloc(6);
    strcpy(hello, "hello");

    char *short_buffer = (char*)malloc(9);
    strncpy(short_buffer, hello, 10);  // Boom!

    return short_buffer[8];
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe
```

### <a name="resulting-error---strncpy-into-heap"></a>결과 오류-strncpy 힙

:::image type="content" source="media/heap-buffer-overflow-example-3.png" alt-text="예제 3에서 힙 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
