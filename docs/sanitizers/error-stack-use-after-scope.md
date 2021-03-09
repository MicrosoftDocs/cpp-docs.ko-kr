---
title: '오류: 범위 후-범위를 사용 합니다.'
description: 범위 오류 후 스택 사용에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 02/05/2021
f1_keywords:
- stack-use-after-scope
helpviewer_keywords:
- stack-use-after-scope error
- AddressSanitizer error stack-use-after-scope
ms.openlocfilehash: 2b6e3ada1cc5b76b371e8059e045735b16d4b334
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471109"
---
# <a name="error-stack-use-after-scope"></a>오류: `stack-use-after-scope`

> 주소 Sanitizer 오류: 범위를 벗어난 스택 메모리 사용

변수 수명의 어휘 범위 외부에서 스택 주소를 사용 하는 것은 C 또는 c + +에서 여러 가지 방법으로 발생할 수 있습니다.

## <a name="example-1---simple-nested-local"></a>예제 1-단순 중첩 된 로컬

```cpp
// example1.cpp
// stack-use-after-scope error
int *gp;

bool b = true;

int main() {
    if (b) {
        int x[5];
        gp = x+1;
    }
    return *gp;  // Boom!
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error---simple-nested-local"></a>결과 오류-간단한 중첩 된 로컬

:::image type="content" source="media/stack-use-after-scope-example-1.png" alt-text="예 1에 스택 사용-범위를 표시 하는 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example-2---lambda-capture"></a>예제 2-람다 캡처

```cpp
// example2.cpp
// stack-use-after-scope error
#include <functional>

int main() {
    std::function<int()> f;
    {
        int x = 0;
        f = [&x]() {
            return x;  // Boom!
        };
    }
    return f();  // Boom!
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example2.cpp /fsanitize=address /Zi
devenv /debugexe example2.exe
```

### <a name="resulting-error---lambda-capture"></a>결과 오류-람다 캡처

:::image type="content" source="media/stack-use-after-scope-example-2.png" alt-text="예 2에서 스택 사용-범위 내 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example-3---destructor-ordering-with-locals"></a>예제 3-지역으로 소멸자 정렬

```cpp
// example3.cpp
// stack-use-after-scope error
#include <stdio.h>

struct IntHolder {
    explicit IntHolder(int* val = 0) : val_(val) { }
    ~IntHolder() {
        printf("Value: %d\n", *val_);  // Bom!
    }
    void set(int* val) { val_ = val; }
    int* get() { return val_; }

    int* val_;
};

int main(int argc, char* argv[]) {
    // It's incorrect to use "x" inside the IntHolder destructor,
    // because the lifetime of "x" ends earlier. Per the C++ standard,
    // local lifetimes end in reverse order of declaration.
    IntHolder holder;
    int x = argc;
    holder.set(&x);
    return 0;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example3.cpp /fsanitize=address /Zi /O1
devenv /debugexe example3.exe
```

### <a name="resulting-error---destructor-ordering"></a>결과 오류-소멸자 순서 지정

:::image type="content" source="media/stack-use-after-scope-example-3.png" alt-text="예 3에 스택 사용-범위를 표시 하는 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="example-4---temporaries"></a>예 4-임시 개체

```cpp
// example4.cpp
// stack-use-after-scope error
#include <iostream>

struct A {
    A(const int& v) {
        p = &v;
    }
    void print() {
        std::cout << *p;
    }
    const int* p;
};

void explicit_temp() {
    A a(5);     // the temp for 5 is no longer live;
    a.print();
}

void temp_from_conversion() {
    double v = 5;
    A a(v);     // local v is no longer live.
    a.print();
}

void main() {
    explicit_temp();
    temp_from_conversion(); 
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example4.cpp /EHsc /fsanitize=address /Zi
devenv /debugexe example4.exe
```

### <a name="resulting-error---temporaries"></a>결과 오류-임시 개체

:::image type="content" source="media/stack-use-after-scope-example-4.png" alt-text="예 4에서 스택 사용-범위를 표시 하는 오류를 표시 하는 디버거의 스크린샷.":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
