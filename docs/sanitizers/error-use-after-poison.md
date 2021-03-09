---
title: 오류:-포이즌-포이즌 사용
description: 포이즌 오류가 발생 한 후 사용할 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- use-after-poison
helpviewer_keywords:
- use-after-poison error
- AddressSanitizer error use-after-poison
ms.openlocfilehash: 0175b79df493dc60c19d78f045ba1829dc0b6b27
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471214"
---
# <a name="error-use-after-poison"></a>오류: `use-after-poison`

> Address Sanitizer 오류: 포이즌 memory 사용

개발자는 수동으로 메모리를 포이즌 하 여 디버깅을 사용자 지정할 수 있습니다.

## <a name="example"></a>예제

```cpp
// example1.cpp
// use-after-poison error
#include <stdlib.h>

extern "C" void __asan_poison_memory_region(void *, size_t);

int main(int argc, char **argv) {
    char *x = new char[16];
    x[10] = 0;
    __asan_poison_memory_region(x, 16);

    int res = x[argc * 10];              // Boom!
 
    delete [] x;
    return res;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/use-after-poison-example-1.png" alt-text="예 1에서 포이즌 사용 후 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
