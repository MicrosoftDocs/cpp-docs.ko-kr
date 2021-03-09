---
title: '오류: 할당 크기-너무 큼'
description: 할당 크기-너무 큰 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷
ms.date: 03/02/2021
f1_keywords:
- allocation-size-too-big
helpviewer_keywords:
- allocation-size-too-big error
- AddressSanitizer error allocation-size-too-big
ms.openlocfilehash: 3320064f52a4d41ca556b9525760997f52e1385b
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471173"
---
# <a name="error-allocation-size-too-big"></a>오류: `allocation-size-too-big`

> 주소 Sanitizer 오류: 할당 크기-너무 큼

이 예에서는 힙에 대해 할당이 너무 클 때 발견 된 오류를 보여 줍니다. [LLVM 컴파일러-rt 테스트 도구 모음](https://github.com/llvm/llvm-project/tree/main/compiler-rt/test/asan/TestCases)에서 소스인 예제입니다.

## <a name="example"></a>예제

```cpp
// example1.cpp
// allocation-size-too-big error
#include <stdio.h>
#include <malloc.h>
#include <memory.h>

int x = 1000;
int y = 1000;

__declspec(noinline) void bad_function() {

  char* buffer = (char*)malloc(x * y * x * y); //Boom!

  memcpy(buffer, buffer + 8, 8); 
}

int main(int argc, char **argv) {
    bad_function();
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/allocation-size-too-big-example-1.png" alt-text="예 1에서 너무 큰 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
