---
title: '오류: 이중-무료'
description: 이중 무료 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- double-free
helpviewer_keywords:
- double-free error
- AddressSanitizer error double-free
ms.openlocfilehash: 6fb508e581a8c19474311d0406622e6353208433
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471262"
---
# <a name="error-double-free"></a>오류: `double-free`

> 주소 Sanitizer 오류: 해제 된 메모리의 할당 취소

C에서는 잘못 될 수 있습니다 `free` . C + +에서는 두 번 이상 호출할 수 있습니다 `delete` . 이 예제에서는, 및와 함께 오류를 보여 줍니다 `delete` `free` `HeapCreate` .

## <a name="example-c---double-operator-delete"></a>예제 c + +-double `operator delete`

```cpp
// example1.cpp
// double-free error
int main() {

    int *x = new int[42];
    delete [] x;

    // ... some complex body of code

    delete [] x;
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error---double-operator-delete"></a>결과 오류-double `operator delete`

:::image type="content" source="media/double-free-example-1.png" alt-text="예 1에서 두 번 사용 가능 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example-c---double-free"></a>예제 ' C '-double `free`

```cpp
// example2.cpp
// double-free error
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv) {

    char* x = (char*)malloc(10 * sizeof(char));
    memset(x, 0, 10);
    int res = x[argc];
    free(x);

    // ... some complex body of code

    free(x + argc - 1);  // Boom!
    return res;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---double-free"></a>결과 오류-double `free`

:::image type="content" source="media/double-free-example-2.png" alt-text="예 2에서 두 번 사용 가능 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---windows-heapcreate-double-heapfree"></a>예-Windows `HeapCreate` double `HeapFree`

```cpp
// example3.cpp
// double-free error
#include <Windows.h>
#include <stdio.h>

int main() {
    void* newHeap = HeapCreate(0, 0, 0);
    void* newAlloc = HeapAlloc(newHeap, 0, 100);

    HeapFree(newHeap, 0, newAlloc);
    HeapFree(newHeap, 0, newAlloc);
    printf("failure\n");
    return 1;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe
```

### <a name="resulting-error---windows-heapcreate-double-heapfree"></a>결과 오류-Windows `HeapCreate` double `HeapFree`

:::image type="content" source="media/double-free-example-3.png" alt-text="예 3에서 두 번 사용 가능 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
