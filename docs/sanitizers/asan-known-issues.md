---
title: 알려진 문제 AddressSanitizer
description: Microsoft C/c + +의 알려진 문제에 대 한 기술 설명 AddressSanitizer.
ms.date: 03/02/2021
helpviewer_keywords:
- AddressSanitizer known issues
ms.openlocfilehash: 7db8b06a96eababbd6a48e337cff7155f248fb34
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471185"
---
# <a name="addresssanitizer-known-issues"></a>알려진 문제 AddressSanitizer

> [!NOTE]
> 이후 릴리스에서 확인할 내용에 대 한 [피드백](https://aka.ms/vsfeedback/browsecpp) 을 보내고 문제가 발생 하는 경우 [버그를 보고](https://aka.ms/feedback/report?space=62) 하세요.

## <a name="incompatible-options-and-functionality"></a><a name="incompatible-options"></a> 호환 되지 않는 옵션 및 기능

이러한 옵션 및 기능은와 호환 되지 [`/fsanitize=address`](../build/reference/fsanitize.md) 않으며 사용 하지 않도록 설정 하거나 사용 하지 않아야 합니다.

- [`/RTC`](../build/reference/rtc-run-time-error-checks.md)옵션은 AddressSanitizer와 호환 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [증분 링크](../build/reference/incremental-link-incrementally.md) 는 지원 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [편집 하며 계속 하기](/visualstudio/debugger/edit-and-continue-visual-cpp) 는 지원 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [코 루틴](https://devblogs.microsoft.com/cppblog/category/coroutine/) 는 AddressSanitizer와 호환 되지 않으며 다시 시작 가능한 함수는 계측에서 제외 됩니다.
- [OpenMP](../build/reference/openmp-enable-openmp-2-0-support.md) 는 지원 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [Managed c + +](../build/reference/clr-common-language-runtime-compilation.md) 는 지원 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [C++ AMP](../parallel/amp/cpp-amp-overview.md) 지원 되지 않으므로 사용 하지 않도록 설정 해야 합니다.
- [특별 한 경우 목록](https://clang.llvm.org/docs/SanitizerSpecialCaseList.html) 파일은 지원 되지 않습니다.

## <a name="standard-library-support"></a>표준 라이브러리 지원

MSVC 표준 라이브러리 (STL)는 AddressSanitizer를 이해 하는 데 지원 되지 않습니다. STL 코드에서 발생 하는 AddressSanitizer 예외는 진정한 버그를 식별 합니다. 그러나 두 경우는 정확 하지 않습니다.

이 예제에서는 전체 자릿수가 부족 한 것을 보여 줍니다.

```cpp
// Compile with: cl /fsanitize=address /Zi
#include <vector>

int main() {   
    // Create a vector of size 10, but with a capacity of 20.    
    std::vector<int> v(10);
    v.reserve(20);

    // Currently, MSVC ASan does NOT raise an exception here.
    // While this is an out-of-bounds write to 'v', MSVC ASan
    // ensures the write is within the heap allocation size (20).
    v[10] = 1;

    // MSVC ASan DOES raise an exception here, as this write
    // is out of bounds from the heap allocation.
    v[20] = 1;
}
```

## <a name="windows-versions"></a>Windows 버전

특정 Windows 버전에 대 한 종속성이 있으므로 지원은 Windows 10에 초점을 맞추고 있습니다. MSVC AddressSanitizer는 10.0.14393 (RS1) 및 10.0.21323 (시험판 insider build)에서 테스트 되었습니다. 문제가 발생 하 [는 경우 버그를 보고](https://aka.ms/feedback/report?space=62) 합니다.

## <a name="memory-usage"></a>메모리 사용량

AddressSanitizer 런타임은 실행 중에 OS로 메모리를 다시 해제 하지 않습니다. OS 관점에서 볼 때 메모리 누수가 있을 수 있습니다. 이 디자인 결정은 의도적인 것 이므로 필요한 모든 메모리를 앞에 할당 하지 않습니다.

## <a name="addresssanitizer-runtime-dll-locations"></a>AddressSanitizer 런타임 DLL 위치

*`clang_rt.asan*.dll`* 런타임 파일은의 컴파일러 옆에 설치 됩니다 *`%VSINSTALLDIR%\VC\Tools\MSVC\<version>\bin\<host-arch>\<target-arch>\`* . 이러한 위치는 디버깅 세션의 경로와 Visual Studio 개발자 명령 프롬프트에 있습니다. 이러한 파일은 또는에 배치 되지 않습니다 *`C:\Windows\System32`* *`C:\Windows\SysWOW64`* .

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
