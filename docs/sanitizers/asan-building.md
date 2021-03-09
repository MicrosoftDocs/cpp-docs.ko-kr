---
title: AddressSanitizer 언어, 빌드 및 디버깅 참조
description: AddressSanitizer 빌드에 대 한 기술 설명
ms.date: 03/02/2021
f1_keywords:
- __SANITIZE_ADDRESS__
- ASAN_VCASAN_DEBUGGING
helpviewer_keywords:
- ASan reference
- AddressSanitizer reference
- Address Sanitizer reference
ms.openlocfilehash: f2f173da6d39b460098afe123a7537e36cbdf6a7
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471196"
---
# <a name="addresssanitizer-language-build-and-debugging-reference"></a>AddressSanitizer 언어, 빌드 및 디버깅 참조

이 문서의 섹션에서는 AddressSanitizer 언어 사양, 컴파일러 옵션 및 링커 옵션에 대해 설명 합니다. 또한 AddressSanitizer와 관련 된 Visual Studio 디버거 통합을 제어 하는 옵션을 설명 합니다.

AddressSanitizer 런타임에 대 한 자세한 내용 및 함수를 가로채 고 사용자 지정 할당자를 후크 하는 방법에 대 한 자세한 내용은 [런타임 참조](./asan-runtime.md)를 참조 하세요. AddressSanitizer 오류에서 크래시 덤프를 저장 하는 방법에 대 한 자세한 내용은 [크래시 덤프 참조](./asan-offline-crash-dumps.md)를 참조 하세요.

## <a name="language-specification"></a>언어 사양

### `__SANITIZE_ADDRESS__`

`__SANITIZE_ADDRESS__`전처리기 매크로는가 설정 된 경우로 정의 됩니다 `1` [`/fsanitize=address`](../build/reference/fsanitize.md) . 이 매크로는 고급 사용자가 AddressSanitizer 런타임에 대 한 소스 코드를 조건부로 지정 하는 데 유용 합니다.

```cpp
#include <cstdio>

int main() {
    #ifdef __SANITIZE_ADDRESS__
        printf("Address sanitizer enabled");
    #else
        printf("Address sanitizer not enabled");
    #endif
    return 1;
}
```

### `__declspec(no_sanitize_address)`

[`__declspec(no_sanitize_address)`](../cpp/no-sanitize-address.md)지정자를 사용 하 여 함수, 지역 변수 또는 전역 변수에 대해 sanitizer를 선택적으로 사용 하지 않도록 설정할 수 있습니다. 이 `__declspec` 는 _런타임_ 동작이 아닌 _컴파일러_ 동작에 영향을 줍니다.

```cpp
__declspec(no_sanitize_address)
void test1() {
    int x[100];
    x[100] = 5; // ASan exception not caught
}

void test2() {
    __declspec(no_sanitize_address) int x[100];
    x[100] = 5; // ASan exception not caught
}

__declspec(no_sanitize_address) int g[100];
void test3() {
    g[100] = 5; // ASan exception not caught
}
```

## <a name="compiler"></a>컴파일러

### <a name="fsanitizeaddress-compiler-option"></a>`/fsanitize=address` 컴파일러 옵션

[`/fsanitize=address`](../build/reference/fsanitize.md)컴파일러 옵션은 코드에서 메모리 참조를 계측 하 여 런타임에 메모리 안전 오류를 catch 합니다. 계측 후크는 로드, 저장소, 범위, alloca 및 CRT 함수를 로드 합니다. 이 클래스는 범위를 벗어남, 사용이 필요 없는 사용, 범위를 벗어난 경우 등의 숨겨진 버그를 검색할 수 있습니다. 런타임에 검색 된 오류를 포괄 하지 않는 목록은 [AddressSanitizer 오류 예](./asan-error-examples.md)를 참조 하세요.

**`/fsanitize=address`** 는 기존의 모든 c + + 또는 c 최적화 수준과 호환 됩니다 (예: **`/Od`** ,, **`/O1`** **`/O2`** , **`/O2 /GL`** 및 프로필 기반 최적화). 이 옵션을 사용 하 여 생성 된 코드는 정적 및 동적 crts와 함께 작동 합니다 (예: **`/MD`** ,, **`/MDd`** **`/MT`** 및 **`/MTd`** ). 이 컴파일러 옵션을 사용 하 여를 만들 수 있습니다. EXE 또는. X86 또는 x 64를 대상으로 하는 DLL입니다. 호출 스택의 최적 서식을 지정 하려면 디버그 정보가 필요 합니다.

여러 종류의 오류 검색을 보여 주는 코드 예제는 [AddressSanitizer 오류 예](asan-error-examples.md)를 참조 하세요.

### <a name="fsanitize-address-use-after-return-compiler-option-experimental"></a>`/fsanitize-address-use-after-return` 컴파일러 옵션 (실험적)

기본적으로 MSVC 컴파일러 (Clang와 달리)는 힙에서 프레임을 할당 하는 코드를 생성 하 여 반환 후 오류를 catch 합니다. AddressSanitizer를 사용 하 여 이러한 오류를 catch 하려면 다음을 수행 해야 합니다.

1. 옵션을 사용 하 여 컴파일합니다 [`/fsanitize-address-use-after-return`](../build/reference/fsanitize.md) .
2. 프로그램을 실행 하기 전에를 실행 `set ASAN_OPTIONS=detect_stack_use_after_return=1` 하 여 런타임 검사 옵션을 설정 합니다.

**`/fsanitize-address-use-after-return`** 옵션을 사용 하면 로컬에서 "주소를 사용 했습니다."로 간주 될 때 힙에서 이중 스택 프레임을 사용 하는 코드가 생성 됩니다. 이 코드는 단순히만 사용 하는 것 보다 *훨씬 느립니다* **`/fsanitize=address`** . 자세한 내용 및 예제는 [오류: `stack-use-after-return` ](error-stack-use-after-return.md)를 참조 하세요.

힙의 이중 스택 프레임은이를 만든 함수에서 반환 된 후에도 유지 됩니다. 힙의 슬롯에 할당 된 로컬의 주소가 반환 된 후 사용 되는 경우를 예로 들어 보겠습니다. 가짜 힙 프레임과 연결 된 섀도 바이트는 값 0xF9를 포함 합니다. 0xF9는 런타임에서 오류를 보고할 때 반환 후 스택 사용 오류를 의미 합니다.

스택 프레임은 힙에 할당 되며 함수가 반환 된 후에도 유지 됩니다. 런타임은 가비지 수집을 사용 하 여 특정 시간 간격 후에 이러한 가짜 호출 프레임 개체를 비동기적으로 해제 합니다. 로컬의 주소는 힙의 영구 프레임으로 전송 됩니다. 시스템에서 정의 함수가 반환 된 후에 사용 되는 지역에서 사용 되는 경우이를 감지할 수 있습니다. 자세한 내용은 Google에서 설명한 대로 [return 후 stack 사용을 위한 알고리즘](https://github.com/google/sanitizers/wiki/AddressSanitizerUseAfterReturn) 을 참조 하세요.

## <a name="linker"></a><a name="linker"></a> Linker

### <a name="inferasanlibsno-linker-option"></a>`/INFERASANLIBS[:NO]` 링커 옵션

**`/fsanitize=address`** 컴파일러 옵션은 개체를 표시 하 여 실행 파일에 연결할 AddressSanitizer 라이브러리를 지정 합니다. 라이브러리의 이름은로 시작 *`clang_rt.asan*`* 합니다. [`/INFERASANLIBS`](../build/reference/inferasanlibs.md)링커 옵션 (기본적으로 설정)은 이러한 라이브러리를 기본 위치에서 자동으로 연결 합니다. 에서 선택 하 고 자동으로 연결 된 라이브러리는 다음과 같습니다.

| CRT 옵션 | DLL 또는 EXE | 디버그? | AddressSanitizer 런타임 라이브러리 |
|--|--|--|--|
| MT | EXE | 아니요 | *`clang_rt.asan-{arch}`*, *`clang_rt.asan_cxx-{arch}`* |
| MT | DLL | 아니요 | *`clang_rt.asan_dll_thunk-{arch}`* |
| MD | 다음 중 하나 | 아니요 | *`clang_rt.asan_dynamic-{arch}`*, *`clang_rt.asan_dynamic_runtime_thunk-{arch}`* |
| MT | EXE | YES | *`clang_rt.asan_dbg-{arch}`*, *`clang_rt.asan_dbg_cxx-{arch}`* |
| MT | DLL | YES | *`clang_rt.asan_dbg_dll_thunk-{arch}`* |
| MD | 다음 중 하나 | YES | *`clang_rt.asan_dbg_dynamic-{arch}`*, *`clang_rt.asan_dbg_dynamic_runtime_thunk-{arch}`* |

링커 옵션은 [`/INFERASANLIBS:NO`](../build/reference/inferasanlibs.md) 링커가 *`clang_rt.asan*`* 기본 위치의 라이브러리 파일을 연결 하지 못하도록 합니다. 이 옵션을 사용 하는 경우 빌드 스크립트에 라이브러리 경로를 추가 합니다. 그렇지 않으면 링커가 확인 되지 않은 외부 기호 오류를 보고 합니다.

## <a name="visual-studio-integration"></a>Visual Studio 통합

### <a name="fno-sanitize-address-vcasan-lib-compiler-option"></a>`/fno-sanitize-address-vcasan-lib` 컴파일러 옵션

이 **`/fsanitize=address`** 옵션은 AddressSanitizer 예외가 throw 될 때 향상 된 Visual Studio 디버깅 환경을 위해 추가 라이브러리의 링크를 제공 합니다. 이러한 라이브러리를 **Vcasan** 이라고 합니다. 라이브러리를 사용 하 여 Visual Studio에서 소스 코드에 AddressSanitizer 오류를 표시할 수 있습니다. 또한 AddressSanitizer 오류 보고서를 만들 때 실행 파일이 크래시 덤프를 생성할 수 있도록 합니다. 자세한 내용은 [Visual Studio AddressSanitizer extended 기능 라이브러리](./asan-debugger-integration.md)를 참조 하세요.

선택한 라이브러리는 컴파일러 옵션에 따라 다르며에 자동으로 연결 됩니다.

| 런타임 옵션 | VCAsan 버전 |
|--------------|----------------|
| **`/MT`**        | *`libvcasan.lib`*  |
| **`/MD`**        | *`vcasan.lib`*     |
| **`/MTd`**       | *`libvcasand.lib`* |
| **`/MDd`**       | *`vcasand.lib`*    |

그러나를 사용 하 여 컴파일하는 경우 **`/Zl`** (기본 라이브러리 이름 생략) 라이브러리를 수동으로 지정 해야 합니다. 그렇지 않으면 확인할 수 없는 외부 기호 링크 오류가 발생 합니다. 몇 가지 일반적인 예는 다음과 같습니다.

```Output
error LNK2001: unresolved external symbol __you_must_link_with_VCAsan_lib
error LNK2001: unresolved external symbol ___you_must_link_with_VCAsan_lib
```

옵션을 사용 하 여 컴파일 시간에 향상 된 디버깅을 사용 하지 않도록 설정할 수 있습니다 [`/fno-sanitize-address-vcasan-lib`](../build/reference/fsanitize.md) .

### <a name="asan_vcasan_debugging-environment-variable"></a>`ASAN_VCASAN_DEBUGGING`환경 변수

**`/fsanitize=address`** 컴파일러 옵션은 런타임에 메모리 안전 버그를 노출 하는 이진 파일을 생성 합니다. 명령줄에서 이진 파일을 시작 하면 런타임에서 오류를 보고 하 고 오류 세부 정보를 출력 합니다. 그런 다음 프로세스를 종료 합니다. `ASAN_VCASAN_DEBUGGING`런타임에서 오류를 보고할 때 Visual STUDIO IDE를 즉시 시작 하도록 환경 변수를 설정할 수 있습니다. 이 컴파일러 옵션을 사용 하면 오류를 발생 시킨 정확한 줄과 열에서 소스 코드에 대 한 오류를 볼 수 있습니다.

이 동작을 사용 하려면 `set ASAN_VCASAN_DEBUGGING=1` 응용 프로그램을 실행 하기 전에 명령을 실행 합니다. 을 실행 하 여 향상 된 디버깅 환경을 사용 하지 않도록 설정할 수 있습니다 `set ASAN_VCASAN_DEBUGGING=0` .

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
