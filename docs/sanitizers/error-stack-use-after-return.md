---
title: '오류: 반환 후-반환 후'
description: 반환 오류 후 스택 사용에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- stack-use-after-return
helpviewer_keywords:
- stack-use-after-return error
- AddressSanitizer error stack-use-after-return
ms.openlocfilehash: 37d950b0c3b4da880524c0c5825d86d6feec9654
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471215"
---
# <a name="error-stack-use-after-return"></a>오류: `stack-use-after-return`

> 주소 Sanitizer 오류: 반환 후 스택 메모리 사용

이 검사를 수행 하려면 추가 컴파일러 옵션인 및 환경 변수를 설정 하 여 활성화 된 코드를 생성 해야 [`/fsanitize-address-use-after-return`](../build/reference/fsanitize.md) `ASAN_OPTIONS=detect_stack_use_after_return=1` 합니다.

이 검사는 응용 프로그램의 성능을 크게 저하 시킬 수 있습니다. 반환 후 사용을 지 원하는 알고리즘의 [Clang 요약](https://github.com/google/sanitizers/wiki/AddressSanitizerUseAfterReturn) 및 더 큰 성능 비용을 고려 합니다.

> [!IMPORTANT]
> 추가 컴파일러 옵션을 사용 하 여 개체 파일을 만드는 경우 **`/fsanitize-address-use-after-return`** 컴파일러에서 생성 된 코드는 스택 프레임을 할당 하는 방법에 대 한 런타임 결정을 내립니다. 환경 변수가 `ASAN_OPTIONS` 로 설정 되어 있지 않으면 `detect_stack_use_after_return` 해당 코드는를 사용 하는 것 보다 느립니다 [`/fsanitize=address`](../build/reference/fsanitize.md) . 를 사용 하 여 프레임의 일부에 공간을 할당 하는 일부 스택 프레임에서 추가 오버 헤드가 발생 하기 때문에 속도가 느립니다 `alloca()` . 반환 후 오류 처리를 마치면 이러한 개체 파일을 삭제 하는 것이 가장 좋습니다.

## <a name="example---simple-c"></a>예제-단순 C

```cpp
// example1.cpp
// stack-use-after-return error
char* x;

void foo() {
    char stack_buffer[42];
    x = &stack_buffer[13];
}

int main() {

    foo();
    *x = 42; // Boom!

    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /fsanitize-address-use-after-return /Zi
set ASAN_OPTIONS=detect_stack_use_after_return=1
devenv /debugexe example1.exe
```

### <a name="resulting-error---simple-c"></a>결과 오류-단순 C

:::image type="content" source="media/stack-use-after-return-example-1.png" alt-text="예 1에서 반환 후 스택 사용 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example---c-and-templates"></a>예제-c + + 및 템플릿

```cpp
// example2.cpp
// stack-use-after-return error
#include <stdlib.h>

enum ReadOrWrite { Read = 0, Write = 1 };

struct S32 {
    char x[32];
};

template<class T>
T* LeakStack() {
    T t[100];
    static volatile T* x;
    x = &t[0];
    return (T*)x;
}

template<class T>
void StackUseAfterReturn(int Idx, ReadOrWrite w) {
    static T sink;
    T* t = LeakStack<T>();
    if (w)
        t[100 + Idx] = T();
    else
        sink = t[100 + Idx];
}

int main(int argc, char* argv[]) {

    if (argc != 2) return 1;
    int kind = atoi(argv[1]);

    switch (kind) {
    case 1: StackUseAfterReturn<char>(0, Read); break;
    case 2: StackUseAfterReturn<S32>(0, Write); break;
    }
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /fsanitize-address-use-after-return /Zi
set ASAN_OPTIONS=detect_stack_use_after_return=1
devenv /debugexe example2.exe 1
```

### <a name="resulting-error---c-and-templates"></a>결과 오류-c + + 및 템플릿

:::image type="content" source="media/stack-use-after-return-example-2.png" alt-text="예 2에서 스택 사용-반환 후 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
