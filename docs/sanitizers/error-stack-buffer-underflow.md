---
title: '오류: 스택-버퍼 언더플로'
description: 스택 버퍼 언더플로 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- stack-buffer-underflow
helpviewer_keywords:
- stack-buffer-underflow error
- AddressSanitizer error stack-buffer-underflow
ms.openlocfilehash: 78705933378d7880057d9b7fd13a933f73129fcb
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471116"
---
# <a name="error-stack-buffer-underflow"></a>오류: `stack-buffer-underflow`

> 주소 Sanitizer 오류: 스택 버퍼 언더플로

이러한 오류 메시지는 스택 변수 시작 전의 어딘가에 메모리 액세스를 의미 합니다.

## <a name="example---local-array-underflow"></a>예제-로컬 배열 언더플로

```cpp
// example1.cpp
// stack-buffer-underflow error
#include <stdio.h>

int main() {

    int subscript = -1;
    char buffer[42];
    buffer[subscript] = 42; // Boom!
   
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/stack-buffer-underflow-example-1.png" alt-text="예 1에서 스택 버퍼 언더플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---stack-underflow-on-thread"></a>예제-스레드의 스택 언더플로

```cpp
// example2.cpp
// stack-buffer-underflow error
#include <windows.h>

DWORD WINAPI thread_proc(void *) {
    int subscript = -1;
    volatile char stack_buffer[42];
    stack_buffer[subscript] = 42;

    return 0;
}

int main() {
    HANDLE thr = CreateThread(NULL, 0, thread_proc, NULL, 0, NULL);

    if (thr == 0) return 0;

    WaitForSingleObject(thr, INFINITE);

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error----stack-underflow-on-thread"></a>스레드에 대 한 결과 오류-스택 언더플로

:::image type="content" source="media/stack-buffer-underflow-example-2.png" alt-text="예 2에서 스택 버퍼 언더플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
