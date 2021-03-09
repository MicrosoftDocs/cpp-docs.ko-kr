---
title: AddressSanitizer
description: Microsoft C/c + + 용 AddressSanitizer 기능에 대 한 최상위 수준 설명입니다.
ms.date: 03/05/2021
f1_keywords:
- AddressSanitizer
helpviewer_keywords:
- ASan
- AddressSanitizer
- Address Sanitizer
- compiling for AddressSanitizer
ms.openlocfilehash: db1760a37c610493cd3a3d95ab5e77b29bf89400
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471280"
---
# <a name="addresssanitizer"></a>AddressSanitizer

## <a name="overview"></a>개요

C & c + + 언어는 강력 하지만 프로그램 정확성 및 프로그램 보안에 영향을 주는 버그 클래스의 영향을 받을 수 있습니다. Visual Studio 2019 버전 16.9부터 Microsoft C/c + + 컴파일러 (MSVC) 및 IDE는 *AddressSanitizer* 를 지원 합니다. ASan (AddressSanitizer)는 가양성을 **0** 으로 표시 하는 다양 한 검색 버그를 노출 하는 컴파일러 및 런타임 기술입니다.

- [할당/제거 불일치](error-alloc-dealloc-mismatch.md) 및 [ `new` / `delete` 형식 불일치](error-new-delete-type-mismatch.md)
- [힙에 대 한 할당이 너무 큼](error-allocation-size-too-big.md)
- [ `calloc` 오버플로](error-calloc-overflow.md) 및 [ `alloca` 오버플로](error-dynamic-stack-buffer-overflow.md)
- [](error-double-free.md) 무료 후 무료로 [사용](error-heap-use-after-free.md)
- [전역 변수 오버플로](error-global-buffer-overflow.md)
- [힙 버퍼 오버플로](error-heap-buffer-overflow.md)
- [정렬 된 값의 맞춤이 잘못 되었습니다.](error-invalid-allocation-alignment.md)
- [`memcpy`](error-memcpy-param-overlap.md)및 [ `strncat` 매개 변수가 겹칩니다](error-strncat-param-overlap.md) .
- [스택 버퍼 오버플로](error-stack-buffer-overflow.md) 및 [언더플로](error-stack-buffer-underflow.md)
- [다음 이후 `return` 스택 사용](error-stack-use-after-return.md) 및 [범위 이후 사용](error-stack-use-after-scope.md)
- [포이즌 후의 메모리 사용](error-use-after-poison.md)

AddressSanitizer를 사용 하 여 다음에 소요 되는 시간을 줄입니다.

- 기본 정확성
- 플랫폼 간 이식성
- 보안
- 스트레스 테스트
- 새 코드 통합

[Google에서 원래 도입](https://www.usenix.org/conference/atc12/technical-sessions/presentation/serebryany)된 AddressSanitizer는 [ `/RTC` (런타임 오류 검사)](../build/reference/rtc-run-time-error-checks.md) 및 [ `/analyze` (정적 분석)](../build/reference/analyze-code-analysis.md)둘 다에 대 한 강력한 대안입니다. 기존 빌드 시스템 및 기존 테스트 자산을 직접 사용 하는 런타임 버그 찾기 기술을 제공 합니다.

AddressSanitizer는 Visual Studio 프로젝트 시스템, CMake 빌드 시스템 및 IDE와 통합 됩니다. 프로젝트는 프로젝트 속성을 설정 하 여 AddressSanitizer를 사용 하도록 설정 하거나 추가 컴파일러 옵션를 하나 사용 하 여 사용할 수 있습니다 **`/fsanitize=address`** . 새 옵션은 x86 및 x 64의 모든 최적화 및 구성 수준과 호환 됩니다. 그러나이는 [편집 하며 계속 하기](/visualstudio/debugger/edit-and-continue-visual-cpp), [증분 링크](../build/reference/incremental-link-incrementally.md)및와 호환 되지 않습니다 [`/RTC`](../build/reference/rtc-run-time-error-checks.md) .

Visual Studio 2019 버전 16.9부터 Microsoft의 AddressSanitizer 기술을 통해 Visual Studio IDE와 통합할 수 있습니다. 이 기능은 sanitizer에서 런타임에 버그를 찾을 때 선택적으로 크래시 덤프 파일을 만들 수 있습니다. `ASAN_SAVE_DUMPS=MyFileName.dmp`프로그램을 실행 하기 전에 환경 변수를 설정 하는 경우 정확히 진단 된 버그를 효율적으로 [사후 디버깅](#crash-dumps) 하기 위한 추가 메타 데이터를 사용 하 여 크래시 덤프 파일이 생성 됩니다. 이러한 덤프 파일을 사용 하면 보다 쉽게 AddressSanitizer를 확장할 수 있습니다.

- 로컬 컴퓨터 테스트,
- 온-프레미스 분산 테스트 및
- 테스트를 위한 클라우드 기반 워크플로.

### <a name="install-the-addresssanitizer"></a>AddressSanitizer 설치

AddressSanitizer IDE 통합 및 라이브러리는 Visual Studio 설치 관리자에서 c + + 워크 로드와 함께 기본적으로 설치 됩니다. 그러나 이전 버전의 Visual Studio 2019에서 업그레이드 하는 경우에는 설치 관리자를 사용 하 여 업그레이드 후 ASan 지원을 사용 하도록 설정 합니다.

:::image type="content" source="media/asan-installer-option.png" alt-text="C + + AddressSanitizer 구성 요소를 강조 표시 하 Visual Studio 설치 관리자 스크린샷":::

Visual Studio 설치 관리자에서 기존 Visual Studio 설치에 대 한 **수정을** 선택 하 여 위의 화면으로 이동할 수 있습니다.

> [!NOTE]
> 새 업데이트에서 Visual Studio를 실행 하지만 ASan를 설치 하지 않은 경우 코드를 실행할 때 오류가 발생 합니다.
>
> LNK1356: ' clang_rt ' 라이브러리를 찾을 수 없습니다.

### <a name="use-the-addresssanitizer"></a><a name="using-asan"></a> AddressSanitizer 사용

**`/fsanitize=address`** 다음과 같은 일반적인 개발 방법 중 하나를 사용 하 여 컴파일러 옵션을 사용 하 여 실행 파일 빌드를 시작 합니다.

- 명령줄 빌드
- Visual Studio 프로젝트 시스템
- Visual Studio CMake 통합

 다시 컴파일한 후 프로그램을 정상적으로 실행 합니다. 이 코드 생성 [은 여러 형식의 정확한 진단 버그를](#error-types)노출 합니다. 이러한 오류는 디버거 IDE의 세 가지 방법, 즉 명령줄에서 또는 [새 형식의 덤프 파일](#crash-dumps) 에 저장 되어 정확한 오프 라인 처리를 위해 보고 됩니다.

Microsoft는 다음과 같은 세 가지 표준 워크플로에 AddressSanitizer을 사용 하는 것을 권장 합니다.

- **개발자 내부 루프**
  - Visual Studio- [명령줄](#command-prompt)
  - Visual Studio- [프로젝트 시스템](#ide-msbuild)
  - Visual Studio- [Cmake](#ide-cmake)

- **CI/CD** 연속 통합/지속적인 개발
  - 오류 보고- [새 AddressSanitizer 덤프 파일](#crash-dumps)

- **퍼징** - [libFuzzer](https://llvm.org/docs/LibFuzzer.html) 래퍼를 사용 하 여 빌드
  - [Azure OneFuzz](https://www.microsoft.com/security/blog/2020/09/15/microsoft-onefuzz-framework-open-source-developer-tool-fix-bugs/)
  - 로컬 컴퓨터

이 문서에서는 위에 나열 된 세 가지 워크플로를 사용 하도록 설정 하는 데 필요한 정보에 대해 설명 합니다. 이 정보는 **플랫폼에 종속** 된 Windows 10 AddressSanitizer 구현에만 적용 됩니다. 이 설명서에서는 이미 게시 된 [Google, Apple 및 GCC](#external-docs) 의 뛰어난 설명서를 보완 합니다.

> [!NOTE]
> 현재 지원은 Windows 10의 x86 및 x 64로 제한 됩니다. 이후 릴리스에서 보려는 내용에 대 한 [피드백을 보내 주세요](https://aka.ms/vsfeedback/browsecpp) . 사용자 의견은 나중에,,, 또는와 같은 다른 sanitizers의 우선 순위를 지정 하는 데 도움이 됩니다 **`/fsanitize=thread`** **`/fsanitize=leak`** **`/fsanitize=memory`** **`/fsanitize=undefined`** **`/fsanitize=hwaddress`** . 문제가 발생 하는 경우 [여기에서 버그를 보고할](https://aka.ms/feedback/report?space=62) 수 있습니다.

## <a name="use-the-addresssanitizer-from-a-developer-command-prompt"></a><a name="command-prompt"></a> 개발자 명령 프롬프트에서 AddressSanitizer 사용

**`/fsanitize=address`** AddressSanitizer 런타임에 대해 컴파일을 사용 하도록 설정 하려면 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts) 에서 컴파일러 옵션을 사용 합니다. **`/fsanitize=address`** 옵션은 모든 기존 c + + 또는 c 최적화 수준과 호환 됩니다 (예:,,, `/Od` `/O1` `/O2` `/O2 /GL` 및 `PGO` ). 옵션은 정적 및 동적 crts와 함께 작동 합니다 (예: `/MD` ,, `/MDd` `/MT` 및 `/MTd` ). EXE 또는 DLL을 만드는 지 여부에 관계 없이 작동 합니다. 호출 스택의 최적 서식을 지정 하려면 디버그 정보가 필요 합니다. 아래 예제에서 `cl /fsanitize=address /Zi` 는 명령줄에 전달 됩니다.

AddressSanitizer 라이브러리 (.lib 파일)는 자동으로 연결 됩니다. 자세한 내용은 [AddressSanitizer language, build 및 디버깅 참조](asan-building.md)를 참조 하세요.

### <a name="example---basic-global-buffer-overflow"></a>예-기본 글로벌 버퍼 오버플로

```cpp
// basic-global-overflow.cpp
#include <stdio.h>
int x[100];
int main() {
    printf("Hello!\n");
    x[100] = 5; // Boom!
    return 0;
}
```

Visual Studio 2019 용 개발자 명령 프롬프트 사용, 컴파일 *`main.cpp`* 사용 `/fsanitize=address /Zi`

:::image type="content" source="media/asan-command-basic-global-overflow.png" alt-text="AddressSanitizer 옵션을 사용 하 여 컴파일하는 명령을 보여 주는 명령 프롬프트의 스크린샷":::

명령줄에서 결과를 실행 하면 *`main.exe`* 아래에 표시 된 형식 오류 보고서가 만들어집니다.

7 가지 주요 정보를 강조 표시 하는 빨간색 상자를 생각해 보세요.

:::image type="content" source="media/asan-basic-global-overflow.png" alt-text="기본 글로벌 오버플로 오류를 보여 주는 디버거의 스크린샷":::

### <a name="red-highlights-from-top-to-bottom"></a>위쪽에서 아래쪽으로 빨강 강조 표시

1. 메모리 안전 버그는 전역 버퍼 오버플로입니다.
2. 사용자 정의 변수 외부에 **4 바이트** (32 비트)가 **저장** 되었습니다.
3. 저장소는 `main()` 줄 7의 파일에 정의 된 함수에서 발생 `basic-global-overflow.cpp` 했습니다.
4. 이라는 변수는 `x` 열 8에서 시작 하 여 basic-global-overflow에 정의 됩니다.
5. 이 전역 변수의 `x` 크기는 400 바이트입니다.
6. 저장소에서 대상으로 하는 주소를 설명 하는 정확한 [그림자 바이트](./asan-shadow-bytes.md) 의 값은 `0xf9`
7. 그림자 바이트 범례는 `0xf9` 오른쪽의 안쪽 여백 영역입니다. `int x[100]`

> [!NOTE]
> 호출 스택의 함수 이름은 오류 발생 시 런타임에 의해 호출 되는 [LLVM symbolizer](https://llvm.org/docs/CommandGuide/llvm-symbolizer.html) 를 통해 생성 됩니다.

## <a name="use-the-addresssanitizer-in-visual-studio"></a><a name="ide-msbuild"></a> Visual Studio에서 AddressSanitizer 사용

AddressSanitizer는 Visual Studio IDE와 통합 됩니다. MSBuild 프로젝트의 AddressSanitizer을 설정 하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다. **속성 페이지** 대화 상자에서 **구성 속성**  >  **C/c + +**  >  **일반** 을 선택한 다음 **Enable AddressSanitizer** 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

:::image type="content" source="media/asan-project-system-dialog.png" alt-text="Enable AddressSanitizer 속성을 보여 주는 속성 페이지 대화 상자의 스크린샷":::

IDE에서 빌드하려면 [호환 되지 않는 옵션](./asan-known-issues.md#incompatible-options)을 옵트아웃 합니다. (또는 디버그 모드)를 사용 하 여 컴파일된 기존 프로젝트의 경우 **`/Od`** 다음 옵션을 해제 해야 할 수 있습니다.

- [편집 하며 계속 하기](/visualstudio/debugger/how-to-enable-and-disable-edit-and-continue) 해제
- 해제 [ `/RTC1` (런타임 검사)](../build/reference/rtc-run-time-error-checks.md)
- 해제 [ `/INCREMENTAL` (증분 링크)](../build/reference/incremental-link-incrementally.md)

디버거를 빌드하고 실행 하려면 **F5** 키를 누르십시오. Visual Studio에서 다음 창이 표시 됩니다.

:::image type="content" source="media/asan-global-buffer-overflow-F5.png" alt-text="전역 버퍼 오버플로 오류를 보여 주는 디버거의 스크린샷":::

## <a name="using-the-addresssanitizer-from-visual-studio-cmake"></a><a name="ide-cmake"></a> Visual Studio에서 AddressSanitizer 사용: CMake

[Windows를 대상으로 하는 cmake 프로젝트](../build/cmake-projects-in-visual-studio.md)에 대해 AddressSanitizer를 사용 하도록 설정 하려면 다음 단계를 수행 합니다.

1. IDE 맨 위에 있는 도구 모음에서 **구성** 드롭다운을 열고 **구성 관리** 를 선택 합니다.

   :::image type="content" source="media/asan-cmake-configuration-dropdown.png" alt-text="CMake 구성 드롭다운의 스크린샷":::

   이 항목을 선택 하면 CMakeSettings.js파일에 저장 된 CMake 프로젝트 설정 편집기가 열립니다.

1. 편집기에서 **JSON 편집** 링크를 선택 합니다. 이렇게 선택 하면 뷰가 원시 JSON으로 전환 됩니다.

1. **"Addresssanitizerenabled": true** 속성을 추가 합니다.

   이 이미지는 변경 후의 CMakeSettings.js입니다.

   :::image type="content" source="media/asan-cmake-json.png" alt-text="CMakeSettings.js에 대 한 텍스트 편집기 보기의 스크린샷":::

1. 이 JSON 파일을 저장 하려면 **Ctrl + S** 를 입력 한 다음 **F5** 키를 눌러 디버거를 다시 컴파일하고 실행 합니다.

이 스크린샷에서는 CMake 빌드에서 오류를 캡처합니다.

:::image type="content" source="media/asan-cmake-error-f5.png" alt-text="CMake 빌드 오류 메시지의 스크린샷":::

## <a name="addresssanitizer-crash-dumps"></a><a name="crash-dumps"></a> AddressSanitizer 크래시 덤프

클라우드 및 분산 워크플로와 함께 사용 하기 위해 AddressSanitizer에 새로운 기능이 도입 되었습니다. 이 기능을 사용 하면 IDE에서 AddressSanitizer 오류를 오프 라인으로 볼 수 있습니다. 라이브 디버그 세션에서 발생 하는 것 처럼이 오류는 원본 위에 중첩 됩니다.

이러한 새 덤프 파일은 버그를 분석할 때 효율성을 초래할 수 있습니다. 다시 실행 하거나 원격 데이터를 찾거나 오프 라인으로 전환 된 컴퓨터를 찾을 필요가 없습니다.

나중에 다른 컴퓨터의 Visual Studio에서 볼 수 있는 새로운 유형의 덤프 파일을 생성 하려면 다음을 수행 합니다.

```cmd
set ASAN_SAVE_DUMPS=MyFileName.dmp
```

Visual Studio 16.9부터 파일에 저장 된 **정확 하 게 진단 된 오류** 를 *`*.dmp`* 소스 코드 위에 표시할 수 있습니다.

[이 새로운 크래시 덤프 기능](./asan-offline-crash-dumps.md) 을 통해 클라우드 기반 워크플로 또는 분산 테스트를 수행할 수 있습니다. 이를 사용 하 여 모든 시나리오에서 자세한 실행 가능한 버그를 파일에 추가할 수도 있습니다.

## <a name="example-errors"></a><a name="error-types"></a> 예제 오류

AddressSanitizer는 여러 종류의 메모리 오용 오류를 감지할 수 있습니다. AddressSanitizer () 컴파일러 옵션을 사용 하 여 컴파일된 이진 파일을 실행할 때 보고 되는 런타임 오류는 다음과 같습니다 **`/fsanitize=address`** .

- [`alloc-dealloc-mismatch`](error-alloc-dealloc-mismatch.md)
- [`allocation-size-too-big`](error-allocation-size-too-big.md)
- [`calloc-overflow`](error-calloc-overflow.md)
- [`double-free`](error-double-free.md)
- [`dynamic-stack-buffer-overflow`](error-dynamic-stack-buffer-overflow.md)
- [`global-buffer-overflow`](error-global-buffer-overflow.md)
- [`heap-buffer-overflow`](error-heap-buffer-overflow.md)
- [`heap-use-after-free`](error-heap-use-after-free.md)
- [`invalid-allocation-alignment`](error-invalid-allocation-alignment.md)
- [`memcpy-param-overlap`](error-memcpy-param-overlap.md)
- [`new-delete-type-mismatch`](error-new-delete-type-mismatch.md)
- [`stack-buffer-overflow`](error-stack-buffer-overflow.md)
- [`stack-buffer-underflow`](error-stack-buffer-underflow.md)
- [`stack-use-after-return`](error-stack-use-after-return.md)
- [`stack-use-after-scope`](error-stack-use-after-scope.md)
- [`strncat-param-overlap`](error-strncat-param-overlap.md)
- [`use-after-poison`](error-use-after-poison.md)

예제에 대 한 자세한 내용은 [AddressSanitizer 오류 예](./asan-error-examples.md)를 참조 하세요.

## <a name="differences-with-clang-120"></a><a name="differences"></a> Clang 12.0의 차이점

MSVC는 현재 두 가지 기능 영역에서 Clang 12.0과 다릅니다.

- **스택 사용-범위 후** -이 설정은 기본적으로 켜져 있으며 해제할 수 없습니다.
- **스택 사용-반환 후** -이 기능을 사용 하려면 추가 컴파일러 옵션이 필요 하며, 설정 에서만 사용할 수 있습니다 `ASAN_OPTIONS` .

이러한 결정은이 첫 번째 버전을 제공 하는 데 필요한 테스트 매트릭스를 줄이기 위해 작성 되었습니다.

Visual Studio 2019 16.9의 가양성으로 이어질 수 있는 기능이 포함 되지 않았습니다. 이러한 분야는 기존 코드의 수십 년간 interop를 고려할 때 필요한 효과적인 테스트 무결성을 적용 했습니다. 이후 릴리스에서는 더 많은 기능을 고려할 수 있습니다.

- [초기화 순서 Fiasco](https://github.com/google/sanitizers/wiki/AddressSanitizerInitializationOrderFiasco)
- [개체 오버플로 내](https://github.com/google/sanitizers/wiki/AddressSanitizerIntraObjectOverflow)
- [컨테이너 오버플로](https://github.com/google/sanitizers/wiki/AddressSanitizerContainerOverflow)
- [포인터 빼기/비교](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html)

자세한 내용은 [MSVC를 사용 하 여 AddressSanitizer 빌드](./asan-building.md)를 참조 하세요.

## <a name="existing-industry-documentation"></a><a name="external-docs"></a> 기존 업계 설명서

이러한 언어 및 플랫폼에 종속 된 AddressSanitizer 기술의 구현에 대 한 광범위 한 설명서가 이미 있습니다.

- [Google](https://github.com/google/sanitizers/wiki/AddressSanitizer)
- [Apple](https://developer.apple.com/documentation/xcode/diagnosing_memory_thread_and_crash_issues_early)
- [GCC](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html)

[AddressSanitizer](https://www.usenix.org/system/files/conference/atc12/atc12-final39.pdf) 에 대 한이 내용이 필요한 백서에서는 구현을 설명 합니다.

## <a name="see-also"></a>참고 항목

[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
