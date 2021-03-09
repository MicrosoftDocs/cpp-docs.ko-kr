---
title: '오류: 할당-dealloc-불일치'
description: 할당-dealloc 불일치 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷
ms.date: 03/02/2021
f1_keywords:
- alloc-dealloc-mismatch
helpviewer_keywords:
- alloc-dealloc-mismatch error
- AddressSanitizer error alloc-dealloc-mismatch
ms.openlocfilehash: 150809d28631d5d194363e3cb5525163bf7a5e88
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471268"
---
# <a name="error-alloc-dealloc-mismatch"></a>오류: `alloc-dealloc-mismatch`

> 주소 Sanitizer 오류: 할당 및 할당 취소 Api가 일치 하지 않습니다.

`alloc` / `dealloc` Windows에서는 AddressSanitizer의 불일치 기능이 기본적으로 해제 되어 있습니다. 이 기능을 사용 하도록 설정 하려면 `set ASAN_OPTIONS=alloc_dealloc_mismatch=1` 프로그램을 실행 하기 전에를 실행 합니다. 이 환경 변수는 런타임에 검사 되어, 및에 대 한 오류를 보고 `malloc` / `delete` `new` / `free` `new` / `delete[]` 합니다.

## <a name="example"></a>예제

```cpp
// example1.cpp
// alloc-dealloc-mismatch error
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {

    if (argc != 2) return -1;

    switch (atoi(argv[1])) {

    case 1:
        delete[](new int[10]);
        break;
    case 2:
        delete (new int[10]);      // Boom!
        break;
    default:
        printf("arguments: 1: no error 2: runtime error\n");
        return -1;
    }

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
set ASAN_OPTIONS=alloc_dealloc_mismatch=1
devenv /debugexe example1.exe 2
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/alloc-dealloc-mismatch-example-1.png" alt-text="예 1에서 할당-dealloc 불일치 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
