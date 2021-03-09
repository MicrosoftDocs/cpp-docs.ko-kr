---
title: '오류: calloc-오버플로'
description: Calloc 오버플로 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- calloc-overflow
helpviewer_keywords:
- calloc-overflow error
- AddressSanitizer error calloc-overflow
ms.openlocfilehash: 63af733061d255924f0b0fbd5f54e4d77359c436
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471140"
---
# <a name="error-calloc-overflow"></a>오류: `calloc-overflow`

> 주소 Sanitizer 오류: calloc

CRT 함수는 [`calloc`](../c-runtime-library/reference/calloc.md) 0으로 초기화 된 요소를 사용 하 여 메모리에 배열을 만듭니다. 인수는 NULL 포인터를 반환 값으로 전달 하는 내부 오류를 만들 수 있습니다.

## <a name="example"></a>예제

```cpp
// example1.cpp
// calloc-overflow error
#include <stdio.h>
#include <stdlib.h>

int number = -1;
int element_size = 1000;

int main() {

    void *p = calloc(number, element_size);      // Boom!

    printf("calloc returned: %zu\n", (size_t)p);

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/calloc-overflow-example-1.png" alt-text="예 1에서 calloc-오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
