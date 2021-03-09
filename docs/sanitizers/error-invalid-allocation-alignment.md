---
title: '오류: 잘못 된 할당 맞춤'
description: 잘못 된 _aligned_malloc 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷
ms.date: 03/02/2021
f1_keywords:
- invalid-allocation-alignment
helpviewer_keywords:
- invalid-allocation-alignment error
- AddressSanitizer error invalid-allocation-alignment
ms.openlocfilehash: 99318b068c2908bbe9eee63bef80c5f3f5e37e75
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471120"
---
# <a name="error-invalid-allocation-alignment"></a>오류: `invalid-allocation-alignment`

> 주소 Sanitizer 오류: 잘못 된 할당-맞춤

[`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md)함수는 맞춤을 나타내기 위해 2의 거듭제곱이 필요 합니다. 최적화 되지 않은 전역 변수를 사용 하 여 일부 맞춤 요소의 "외부" 계산을 시뮬레이트합니다.

## <a name="example"></a>예제

```cpp
// example1.cpp
// invalid-allocation-alignment error
#include <Windows.h>

int ExternalAlign = 5;

int main(){

    // this externally calculated alignment of 5 isn't valid.

    void* ptr = _aligned_malloc(8,ExternalAlign); 
    return (ptr == nullptr && errno == EINVAL) ? 0 : -1;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/invalid-allocation-alignment-example-1.png" alt-text="예 1에서 잘못 된 할당 맞춤 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
