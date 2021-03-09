---
title: '오류: memcpy-겹침'
description: Memcpy 매개 변수에 대 한 소스 예제 및 라이브 디버그 스크린샷은 중복 오류가 발생 합니다.
ms.date: 03/02/2021
f1_keywords:
- memcpy-param-overlap
helpviewer_keywords:
- memcpy-param-overlap error
- AddressSanitizer error memcpy-param-overlap
ms.openlocfilehash: 1df0310ab2abb326cf895a72afbdffa7c239d9da
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471239"
---
# <a name="error-memcpy-param-overlap"></a>오류: `memcpy-param-overlap`

> 주소 Sanitizer 오류: memcpy

CRT 함수는 [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) 겹치는 메모리를 **지원 하지 않습니다** . CRT는 `memcpy` 겹치는 메모리를 지 원하는의 대안을 제공 [`memmove`](../c-runtime-library/reference/memmove-wmemmove.md) 합니다.

일반적인 오류는와 의미상 동등한 것으로 처리 하는 것입니다 `memmove` `memcpy` .

## <a name="example"></a>예제

```cpp
// example1.cpp
// memcpy-param-overlap error
#include <string.h>

__declspec(noinline) void bad_function() {
    char buffer[] = "hello";

    memcpy(buffer, buffer + 1, 5); // BOOM!
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

:::image type="content" source="media/memcpy-param-overlap-example-1.png" alt-text="예 1에서 memcpy-중복 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
