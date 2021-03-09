---
title: '오류: 전역 버퍼 오버플로가 발생 했습니다.'
description: 전역 변수 오버플로 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷
ms.date: 03/02/2021
f1_keywords:
- global-buffer-overflow
helpviewer_keywords:
- global-buffer-overflow error
- AddressSanitizer error global-buffer-overflow
ms.openlocfilehash: cdc637318c523d43684f938df51030ec803a754b
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471244"
---
# <a name="error-global-buffer-overflow"></a>오류: `global-buffer-overflow`

> 주소 Sanitizer 오류: 전역 버퍼 오버플로

컴파일러는 또는 섹션의 모든 변수에 대 한 메타 데이터를 생성 합니다 `.data` `.bss` . 이러한 변수는 전역 또는 파일 고정의 언어 범위를 가집니다. 시작 하기 전에 메모리에 할당 됩니다 `main()` . C의 전역 변수는 c + +에서와 매우 다르게 처리 됩니다. 이러한 차이는 C 연결에 대 한 복잡 한 규칙 때문에 발생 합니다.

C에서는 여러 소스 파일에서 전역 변수를 선언할 수 있으며 각 정의는 서로 다른 형식을 가질 수 있습니다. 컴파일러는 가능한 모든 정의를 한 번에 볼 수 없지만 링커는 가능 합니다. C의 경우 링커는 기본적으로 다른 모든 선언에서 가장 큰 크기의 변수를 선택 합니다.

C + +에서 전역은 컴파일러에 의해 할당 됩니다. 하나의 정의만 있을 수 있으므로 컴파일 시간에 각 정의의 크기를 알 수 있습니다.

## <a name="example---globals-in-c-with-multiple-type-definitions"></a>예제-여러 형식 정의가 포함 된 ' C '의 globals

```cpp
// file: a.c
int x;
```

```cpp
// file: b.c
char* x;
```

```cpp
// file: c.c
float* x[3];
```

```cpp
// file: example1-main.c
// global-buffer-overflow error

// AddressSanitizer reports a buffer overflow at the first line
// in function main() in all cases, REGARDLESS of the order in 
// which the object files: a.obj, b.obj, and c.obj are linked.
  
double x[5];
 
int main() { 
    int rc = (int) x[5];  // Boom!
    return rc; 
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl a.c b.c c.c example1-main.c /fsanitize=address /Zi
devenv /debugexe example1-main.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/global-overflow-example-1.png" alt-text="예 1에서 전역 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---simple-function-level-static"></a>예제-단순 함수 수준 정적

```cpp
// example2.cpp
// global-buffer-overflow error
#include <string.h>

int 
main(int argc, char **argv) {

    static char XXX[10];
    static char YYY[10];
    static char ZZZ[10];

    memset(XXX, 0, 10); memset(YYY, 0, 10); memset(ZZZ, 0, 10);

    int res = YYY[argc * 10];  // Boom!

    res += XXX[argc] + ZZZ[argc];
    return res;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---simple-function-level-static"></a>결과 오류-간단한 함수 수준 정적

:::image type="content" source="media/global-overflow-example-2.png" alt-text="예 2에서 전역 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="example---all-global-scopes-in-c"></a>예제-c + +의 모든 전역 범위

```cpp
// example3.cpp
// global-buffer-overflow error

// Run 4 different ways with the choice of one of these options:
//
// -g : Global
// -c : File static
// -f : Function static
// -l : String literal

#include <string.h>

struct C {
    static int array[10];
};

// normal global
int global[10];

// class static
int C::array[10];

int main(int argc, char **argv) {

    int one = argc - 1;

    switch (argv[1][1]) {
    case 'g': return global[one * 11];     //Boom! simple global
    case 'c': return C::array[one * 11];   //Boom! class static
    case 'f':
        static int array[10];
        memset(array, 0, 10);
        return array[one * 11];            //Boom! function static
    case 'l':
        // literal global ptr created by compiler
        const char *str = "0123456789";
        return str[one * 11];              //Boom! .rdata string literal allocated by compiler
    }
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi
devenv /debugexe example3.exe -l
```

### <a name="resulting-error---all-global-scopes-in-c"></a>결과 오류-c + +의 모든 전역 범위

:::image type="content" source="media/global-overflow-example-3.png" alt-text="예 3에서 전역 버퍼 오버플로 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
