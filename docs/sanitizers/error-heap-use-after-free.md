---
title: '오류: 힙 사용-무료'
description: 사용 가능한 오류가 발생 한 후에는 힙에 대 한 소스 예제와 라이브 디버그 스크린샷 사용 합니다.
ms.date: 03/02/2021
f1_keywords:
- heap-use-after-free
helpviewer_keywords:
- heap-use-after-free error
- AddressSanitizer error heap-use-after-free
ms.openlocfilehash: 86e64537d40a86b1867e9ba16781f10b6ea9b417
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471132"
---
# <a name="error-heap-use-after-free"></a>오류: `heap-use-after-free`

> 주소 Sanitizer 오류: 할당 취소 된 메모리 사용

`malloc`, `realloc` (C) 및 `new` (c + +)을 (를) 잘못 사용 하 여 힙의 저장소를 할당할 수 있는 세 가지 예제를 보여 줍니다 `volatile` .

## <a name="example---malloc"></a>예제 - `malloc`

```cpp
// example1.cpp
// heap-use-after-free error
#include <stdlib.h>

int main() {
  char *x = (char*)malloc(10 * sizeof(char));
  free(x);

  // ...

  return x[5];   // Boom!
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/heap-use-after-free-example-1.png" alt-text="예 1에서 힙 사용-사용 가능 후 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example---operator-new"></a>예제 - `operator new`

```cpp
// example2.cpp
// heap-use-after-free error
#include <windows.h>

int main() {
  char *buffer = new char[42];
  delete [] buffer;

  // ...

  buffer[0] = 42;  // Boom!
  return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---operator-new"></a>결과 오류-operator new

:::image type="content" source="media/heap-use-after-free-example-2.png" alt-text="예 2에서 힙 사용-사용 가능 후 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example---realloc"></a>예제 - `realloc`

```cpp
// example3.cpp
// heap-use-after-free error
#include <malloc.h>

int main() {
  char *buffer = (char*)realloc(0, 42);
  free(buffer);

  // ...

  buffer[0] = 42;  // Boom!
  return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe
```

### <a name="resulting-error---realloc"></a>결과 오류-realloc

:::image type="content" source="media/heap-use-after-free-example-3.png" alt-text="예제 3에서 힙 사용-사용 가능 후 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example---volatile"></a>예제-휘발성

```cpp
// example4.cpp
// heap-use-after-free error
#include <stdlib.h>

int main() {

  volatile char *x = (char*)malloc(sizeof(char));
  free((void*)x);

      //...

  *x = 42;        // Boom!
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example4.cpp /fsanitize=address /Zi
devenv /debugexe example4.exe
```

### <a name="resulting-error---volatile"></a>결과 오류-volatile

:::image type="content" source="media/heap-use-after-free-example-4.png" alt-text="예 4에서 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
