---
title: AddressSanitizer 오류 예
description: Microsoft C/c + +의 AddressSanitizer 오류 및 예제에 대 한 최상위 수준 설명입니다.
ms.date: 03/01/2021
helpviewer_keywords:
- ASan error examples
- AddressSanitizer error examples
- Address Sanitizer error examples
- Error examples for AddressSanitizer
ms.openlocfilehash: 6f8036139c48b03fb8300f799fbdf05e5006aa4a
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471334"
---
# <a name="addresssanitizer-error-examples"></a>AddressSanitizer 오류 예

이 섹션에서는 Microsoft C/c + + (MSVC)의 AddressSanitizer에서 지 원하는 오류의 하위 집합을 나열 합니다. 이 목록은 완전 한 오류 목록이 아닙니다. AddressSanitizer에 표시 되는 여러 종류의 오류를 보여 주기 위한 것입니다. 각 문서에는 실행 중인 디버거의 빌드 지침과 스크린샷을 포함 하는 예제 코드가 포함 되어 있습니다. MSVC에서 지 원하는 AddressSanitizer 기능을 코드에 사용 하는 방법을 배우는 데 도움이 됩니다. 모든 스크린샷에는를 사용 하 여 생성 되었습니다 **`devenv.exe /debugexe example.exe`** . 이러한 예제 중 일부는 [LLVM 컴파일러-rt 테스트 도구 모음의](https://github.com/llvm/llvm-project/tree/main/compiler-rt/test/asan/TestCases)샘플 코드를 기반으로 합니다.

## <a name="build-the-error-examples"></a>오류 예제 빌드

각 오류 예제에서는 명령줄 빌드에 대 한 소스 코드와 컴파일 명령을 제공 합니다. 각 예제를 빌드하려면 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)를 엽니다. 예제 프로젝트에 대 한 폴더를 만든 다음 현재 디렉터리로 설정 합니다. 그런 다음,와 같이 적절 한 이름을 사용 하 여 예제 코드를 소스 파일에 복사 *`example1.cpp`* 합니다. 빌드 지침에 따라 디버거에서 계측 된 코드를 생성 하 고 실행 합니다.

## <a name="errors-with-examples"></a>예제 관련 오류

- [메시지가 `alloc-dealloc-mismatch`](./error-alloc-dealloc-mismatch.md)

- [메시지가 `allocation-size-too-big`](./error-allocation-size-too-big.md)

- [메시지가 `calloc-overflow`](./error-calloc-overflow.md)

- [메시지가 `double-free`](./error-double-free.md)

- [메시지가 `dynamic-stack-buffer-overflow`](./error-dynamic-stack-buffer-overflow.md)

- [메시지가 `global-overflow`](./error-global-buffer-overflow.md)

- [메시지가 `heap-buffer-overflow`](./error-heap-buffer-overflow.md)

- [메시지가 `heap-use-after-free`](./error-heap-use-after-free.md)

- [메시지가 `invalid-allocation-alignment`](./error-invalid-allocation-alignment.md)

- [메시지가 `memcpy-param-overlap`](./error-memcpy-param-overlap.md)

- [메시지가 `new-delete-type-mismatch`](./error-new-delete-type-mismatch.md)

- [메시지가 `stack-buffer-overflow`](./error-stack-buffer-overflow.md)

- [메시지가 `stack-buffer-underflow`](./error-stack-buffer-underflow.md)

- [메시지가 `stack-use-after-return`](./error-stack-use-after-return.md)

- [메시지가 `stack-use-after-scope`](./error-stack-use-after-scope.md)

- [메시지가 `strncat-param-overlap`](./error-strncat-param-overlap.md)

- [메시지가 `use-after-poison`](./error-use-after-poison.md)

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)
