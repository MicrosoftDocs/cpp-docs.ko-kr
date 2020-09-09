---
title: C/c + + 프로젝트 속성 (Visual Studio)
description: Visual Studio Microsoft C/c + + 프로젝트 속성 페이지 속성에 대 한 참조 가이드입니다.
ms.date: 09/03/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: a96400e27b48b734d4002d9cef13fd52f9ccc7a5
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609167"
---
# <a name="cc-property-pages"></a>C/c + + 속성 페이지

**프로젝트**  >  **속성**  >  **구성 속성**  >  **C/c + +** 에서 다음 속성 페이지를 찾을 수 있습니다.

## <a name="cc-general-properties"></a>C/c + + 일반 속성

### <a name="additional-include-directories"></a>추가 포함 디렉터리

포함 경로에 추가할 디렉터리를 하나 이상 지정합니다. 항목이 여러 개인 경우 세미콜론으로 구분합니다. [ `/I` (추가 포함 디렉터리)](i-additional-include-directories.md)를 설정 합니다.

### <a name="additional-using-directories"></a>추가 #using 디렉터리

#Using 지시문에 전달 된 이름을 확인 하기 위해 검색할 하나 이상의 디렉터리 (세미콜론을 포함 하는 별도의 디렉터리 이름)를 지정 합니다. [`/AI`](ai-specify-metadata-directories.md)을 설정 합니다.

### <a name="debug-information-format"></a>디버그 정보 형식

컴파일러에서 생성되는 디버깅 정보 형식을 지정합니다.  이 속성에는 호환 되는 링커 설정이 필요 합니다. [ `/Z7` , `/Zi` , `/ZI` (디버깅 정보 형식)를](z7-zi-zi-debug-information-format.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **없음** - 디버깅 정보를 생성하지 않으므로 컴파일이 더 빨라질 수 있습니다.
- **C7 호환** -프로그램에 대해 생성 되는 디버깅 정보 형식과이 정보를 개체 (.obj) 파일에 유지할지 아니면 프로그램 데이터베이스 (PDB)에 유지할지를 선택 합니다.
- **프로그램 데이터베이스** -디버거와 함께 사용할 형식 정보 및 기호화 된 디버깅 정보를 포함 하는 프로그램 데이터베이스 (PDB)를 생성 합니다. 기호화 된 디버깅 정보에는 변수와 함수의 이름과 형식 및 줄 번호가 포함 됩니다.
- **편집 하며 계속 하기를 위한 프로그램 데이터베이스** -앞에서 설명한 것 처럼 [편집 하며 계속 하기](/visualstudio/debugger/edit-and-continue) 기능을 지 원하는 형식으로 프로그램 데이터베이스를 생성 합니다.

### <a name="support-just-my-code-debugging"></a>내 코드만 디버깅 지원

이 컴파일 단위에서 [내 코드만](/visualstudio/debugger/just-my-code) 디버깅을 사용 하기 위한 지원 코드를 추가 합니다. [`/JMC`](jmc.md)을 설정 합니다.

### <a name="common-language-runtime-support"></a>공용 언어 런타임 지원

.NET 런타임 서비스를 사용 합니다.  이 스위치는 일부 다른 스위치와 호환 되지 않습니다. 자세한 내용은 스위치 패밀리의 설명서를 참조 하세요 [`/clr`](clr-common-language-runtime-compilation.md) .

#### <a name="choices"></a>선택 사항

- **공용 언어 런타임 지원 안 함** -공용 언어 런타임 지원 안 함
- **공용 언어 런타임 지원** -다른 CLR 응용 프로그램에서 사용할 수 있는 응용 프로그램에 대 한 메타 데이터를 만듭니다. 응용 프로그램에서 다른 CLR 구성 요소의 메타 데이터에 있는 형식과 데이터를 사용할 수도 있습니다.
- **순수 Msil 공용 언어 런타임 지원** -msil로 컴파일된 네이티브 형식을 포함할 수 있지만 네이티브 실행 코드가 없는 [msil](/dotnet/standard/managed-code)전용 출력 파일을 생성 합니다.
- **SAFE Msil 공용 언어 런타임 지원** -msil 전용 (네이티브 실행 코드 없음) 및 안정형 출력 파일을 생성 합니다.

### <a name="consume-windows-runtime-extension"></a>Windows 런타임 확장 사용

Windows 런타임 언어 확장을 사용 합니다. [`/ZW`](zw-windows-runtime-compilation.md)을 설정 합니다.

### <a name="suppress-startup-banner"></a>시작 배너 표시 안 함

컴파일러가 시작 될 때 로그온 배너를 표시 하지 않으며 컴파일하는 동안 정보 메시지를 표시 합니다.

### <a name="warning-level"></a>경고 수준

컴파일러가 코드 오류를 처리하는 수준을 선택합니다. [`/W0` - `/W4`](compiler-option-warning-level.md)을 설정 합니다.

#### <a name="choices"></a>선택 사항

- **모든 경고 해제** -수준 0은 모든 경고를 비활성화 합니다.
- **Level1** -수준 1은 심각한 경고를 표시 합니다. 수준 1은 명령줄에서 기본 경고 수준입니다.
- **Level2** 수준 2는 수준 1의 모든 경고와 수준 1 보다 심각 하지 않은 경고를 표시 합니다.
- **Level3** 수준 3은 수준 2의 모든 경고와 프로덕션 용도로 권장 되는 기타 모든 경고를 표시 합니다.
- **Level4** 수준 4는 수준 3의 모든 경고와 정보 경고를 표시 합니다. 대부분의 경우 안전 하 게 무시할 수 있습니다.
- **Enableallwarnings** -기본적으로 사용 하지 않도록 설정 된 경고를 포함 하 여 모든 경고를 사용 하도록 설정 합니다.

### <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

컴파일러 경고를 오류로 처리 합니다. 새 프로젝트의 경우 모든 컴파일에서를 사용 하는 것이 가장 좋을 수 있습니다 [`/WX`](wx-treat-linker-warnings-as-errors.md) . 모든 경고를 해결 하면 찾기 어려운 코드 오류를 최소화할 수 있습니다.

### <a name="warning-version"></a>경고 버전

특정 버전의 컴파일러 이후에 도입 된 경고를 숨깁니다. [`/Wv:xx[.yy[.zzzzz]]`](wx-treat-linker-warnings-as-errors.md)을 설정 합니다.

### <a name="diagnostics-format"></a>진단 형식

진단 메시지의 열 정보 및 소스 컨텍스트를 사용 하 여 다양 한 진단을 사용 하도록 설정 합니다.

#### <a name="choices"></a>선택 사항

- **캐럿** -진단 메시지에 열 정보를 제공 합니다. 및는 잘못 된 열을 나타내는 캐럿을 사용 하 여 소스 코드의 관련 줄을 출력 합니다.
- **열 정보** -해당 하는 경우 진단이 실행 된 줄 내의 열 번호를 추가로 제공 합니다.
- **클래식** -줄 번호를 사용 하 여 이전의 간결한 진단 메시지만 출력 합니다.

### <a name="sdl-checks"></a>SDL 검사

추가 SDL (보안 개발 수명 주기) 권장 검사 에는 추가 보안 코드 생성 기능을 사용 하도록 설정 하 고 추가 보안 관련 경고를 오류로 사용할 수 있습니다. [ `/sdl` 을 `/sdl-` ](sdl-enable-additional-security-checks.md)설정 합니다.

### <a name="multi-processor-compilation"></a>다중 프로세서 컴파일

다중 프로세서 컴파일입니다.

## <a name="cc-optimization-properties"></a>C/c + + 최적화 속성

### <a name="optimization"></a>Optimization

코드 최적화를 위한 옵션을 선택 합니다. 특정 최적화 옵션을 사용 하려면 사용자 지정을 선택 합니다. [`/Od`](od-disable-debug.md), [ `/O1` ,를 `/O2` ](o-options-optimize-code.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **사용자 지정** - 사용자 지정 최적화입니다.
- **사용 안 함** - 최적화를 사용하지 않습니다.
- **최대 최적화 (크기 우선)** -다음에 해당 합니다. **`/Os /Oy /Ob2 /Gs /GF /Gy`**
- **최대 최적화 (속도 우선)** -다음에 해당 합니다. **`/Oi /Ot /Oy /Ob2 /Gs /GF /Gy`**
- **최적화 (속도 우선)** -다음에 해당 합니다. **`/Oi /Ot /Oy /Ob2`**

### <a name="inline-function-expansion"></a>인라인 함수 확장

빌드에 대 한 [인라인 함수](../../cpp/inline-functions-cpp.md) 확장 수준을 선택 합니다. [`/Ob`](ob-inline-function-expansion.md)을 설정 합니다.

#### <a name="choices"></a>선택 사항

- **기본값**
- **Disabled** -기본적으로 켜져 있는 인라인 확장을 사용 하지 않도록 설정 합니다.
- , 또는로 표시 된 함수만 **__inline** 확장 **`inline`** **`__forceinline`** **`__inline`** 합니다. 또는 c + + 멤버 함수에서 클래스 선언 내에 정의 된 또는입니다.
- 또는로 표시 된 **모든 적절** 한 확장 함수와 **`inline`** **`__inline`** 컴파일러에서 선택 하는 다른 함수 확장은 컴파일러의 판단에 따라 발생 하며 (종종 *자동 인라이닝*이라고 함)

### <a name="enable-intrinsic-functions"></a>내장 함수 사용

내장 함수를 사용 합니다.  내장 함수를 사용 하면 더 빠르지만 더 큰 코드가 생성 됩니다. [`/Oi`](oi-generate-intrinsic-functions.md)을 설정 합니다.

### <a name="favor-size-or-speed"></a>크기 또는 속도를 선호 합니다.

코드 크기나 코드 속도를 선호 하는지 여부 ' 전역 최적화 '가 설정 되어 있어야 합니다. [ `/Ot` 을 `/Os` ](os-ot-favor-small-code-favor-fast-code.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **코드** 크기 우선 – 속도 보다 크기를 선호 하도록 컴파일러에 지시 하 여 Exe 및 dll의 크기를 최소화 합니다.
- **빠른 코드 우선** – 크기 보다 빠른 속도를 선호 하도록 컴파일러에 지시 하 여 Exe 및 dll의 속도를 극대화 합니다. 이 값은 기본값입니다.
- **둘 다** 크기 및 속도 최적화가 없습니다.

### <a name="omit-frame-pointers"></a>프레임 포인터 생략

호출 스택에서 프레임 포인터를 생성하지 않습니다.

### <a name="enable-fiber-safe-optimizations"></a>파이버 안전 최적화 사용

파이버 및 스레드 로컬 저장소 액세스를 사용할 때 메모리 공간 최적화를 사용 하도록 설정 합니다. [`/GT`](gt-support-fiber-safe-thread-local-storage.md)을 설정 합니다.

### <a name="whole-program-optimization"></a>전체 프로그램 최적화

코드 생성을 링크 타임으로 지연 시켜 크로스 모듈 최적화를 사용 하도록 설정 합니다. 링커 옵션 **링크 타임 코드를 생성**해야 합니다. [`/GL`](gl-whole-program-optimization.md)을 설정 합니다.

## <a name="cc-preprocessor-properties"></a>C/c + + 전처리기 속성

### <a name="preprocessor-definitions"></a>전처리기 정의

소스 파일에 대한 전처리 기호를 정의합니다.

### <a name="undefine-preprocessor-definitions"></a>전처리기 정의 해제

전처리기 정의 해제를 하나 이상 지정합니다. [`/U`](u-u-undefine-symbols.md)을 설정 합니다.

### <a name="undefine-all-preprocessor-definitions"></a>모든 전처리기 정의 해제

이전에 정의한 모든 전처리기 값을 정의 해제합니다. [`/u`](u-u-undefine-symbols.md)을 설정 합니다.

### <a name="ignore-standard-include-paths"></a>표준 포함 경로 무시

컴파일러가 INCLUDE 환경 변수에 지정 된 디렉터리에서 포함 파일을 검색 하지 않도록 합니다.

### <a name="preprocess-to-a-file"></a>파일로 전처리

C 및 c + + 소스 파일을 전처리 하 고 전처리 된 출력을 파일에 씁니다. 이 옵션은 컴파일을 억제 하 고 파일을 생성 하지 않습니다 *`.obj`* .

### <a name="preprocess-suppress-line-numbers"></a>전처리 줄 번호 표시 안 함

#Line 지시문을 사용 하지 않고 전처리 합니다.

### <a name="keep-comments"></a>의견 유지

소스 코드의 주석 스트립을 표시 하지 않습니다. **전처리** 옵션을 하나 이상 설정 해야 합니다. [`/C`](c-preserve-comments-during-preprocessing.md)을 설정 합니다.

## <a name="cc-code-generation-properties"></a>C/c + + 코드 생성 속성

### <a name="enable-string-pooling"></a>문자열 풀링 사용

컴파일러는 프로그램 이미지에 동일한 문자열의 읽기 전용 복사본을 하나만 만듭니다. 이로 인해 *문자열 풀링*이라는 최적화 인 작은 프로그램을 생성 합니다. [ `/O1` , `/O2` ](o-options-optimize-code.md)및은 [`/ZI`](z7-zi-zi-debug-information-format.md) 자동으로 [`/GF`](gf-eliminate-duplicate-strings.md) 옵션을 설정 합니다.

### <a name="enable-minimal-rebuild"></a>최소 다시 빌드 사용

변경 된 c + + 클래스 정의를 포함 하는 c + + 소스 파일을 다시 컴파일할 것인지 여부를 결정 하는 최소 다시 빌드를 사용 *`.h`* 합니다.

### <a name="enable-c-exceptions"></a>C++ 예외 사용

컴파일러가 사용하는 예외 처리 모델을 지정합니다.

#### <a name="choices"></a>선택 사항

- **SEH 예외를 사용** 하는 예-비동기 (구조적) 및 동기 (c + +) 예외를 catch 하는 예외 처리 모델입니다. [`/EHa`](eh-exception-handling-model.md)을 설정 합니다.
- **예** -c + + 예외만 catch 하 고 컴파일러에 extern c 함수가 c + + 예외를 throw 하지 않는다고 지시 하는 예외 처리 모델입니다. [`/EHsc`](eh-exception-handling-model.md)을 설정 합니다.
- **예, Extern c 함수를 사용** 하면 c + + 예외만 catch 하 고 컴파일러에 Extern c 함수가 예외를 throw 한다고 가정 하는 예외 처리 모델입니다. [`/EHs`](eh-exception-handling-model.md)을 설정 합니다.
- **아니요** -예외 처리를 하지 않습니다.

### <a name="smaller-type-check"></a>더 작은 형식 검사

더 작은 형식으로의 변환을 확인할 수 있도록 하 고, 디버그 이외의 다른 최적화 형식과 호환 되지 않습니다. [`/RTCc`](rtc-run-time-error-checks.md)을 설정 합니다.

### <a name="basic-runtime-checks"></a>기본 런타임 검사

디버그 이외의 다른 최적화 형식과 호환 되지 않는 기본 런타임 오류 검사를 사용 하도록 설정 합니다. [ `/RTCs` , `/RTCu` ,를 `/RTC1` ](rtc-run-time-error-checks.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **스택 프레임** -스택 프레임 런타임 오류 검사를 사용 하도록 설정 합니다.
- **초기화 되지 않은 변수** -초기화 되지 않은 변수를 사용 하는 경우를 보고 합니다.
- **둘 다 (/RTC1, Http-equiv/RTCsu)** -와 동일 **`/RTCsu`** 합니다.
- **기본** -기본 런타임 검사입니다.

### <a name="runtime-library"></a>런타임 라이브러리

링크할 런타임 라이브러리를 지정합니다. [ `/MT` ,, `/MTd` `/MD` , `/MDd` ](md-mt-ld-use-run-time-library.md)를 설정 합니다.

#### <a name="choices"></a>선택 사항

- **다중 스레드** -응용 프로그램이 런타임 라이브러리의 다중 스레드 정적 버전을 사용 하도록 합니다.
- **다중 스레드 디버그** -_DEBUG 및 _MT을 정의 합니다. 이 옵션을 사용 하면 컴파일러가 *LIBCMTD.lib* *`.obj`* *libcmtd.lib* 를 사용 하 여 외부 기호를 확인할 수 있도록 libcmtd.lib 라이브러리 이름이 파일에 저장 됩니다.
- **다중 스레드 dll** -응용 프로그램이 런타임 라이브러리의 다중 스레드 및 DLL 별 버전을 사용 하도록 합니다. `_MT`및를 정의 하 `_DLL` 고 컴파일러에서 라이브러리 이름 *msvcrt.lib* 를 파일에 저장 하도록 합니다 *`.obj`* .
- **다중 스레드 디버그 DLL** -, 및를 정의 하 `_DEBUG` `_MT` `_DLL` 고 응용 프로그램에서 런타임 라이브러리의 디버그 다중 스레드 및 DLL 별 버전을 사용 하도록 합니다. 또한 컴파일러가 라이브러리 이름 *msvcrtd.lib* 를 파일에 저장 합니다. *`.obj`*

### <a name="struct-member-alignment"></a>구조체 멤버 맞춤

구조체 멤버 맞춤에 1, 2, 4, 8 바이트 경계를 지정 합니다. [`/Zp`](zp-struct-member-alignment.md)을 설정 합니다.

#### <a name="choices"></a>선택 사항

- 1 바이트 경계에서 **1 바이트** 의 구조체를 압축 합니다. 와 동일 **`/Zp`** 합니다.
- **2** 바이트-2 바이트 경계에서 구조체를 압축 합니다.
- **4 바이트-4** 바이트 경계에서 구조체를 압축 합니다.
- **8** 바이트-8 바이트 경계에서 구조체를 압축 합니다 (기본값).
- **16 바이트** -16 바이트 경계에서 구조체를 압축 합니다.
- **기본** -기본 맞춤 설정입니다.

### <a name="security-check"></a>보안 검사

보안 검사를 통해 스택 버퍼 오버런, 프로그램의 보안에 대해 일반적으로 시도되는 공격을 검색할 수 있습니다.

#### <a name="choices"></a>선택 사항

- **보안 검사 사용 안 함** - 보안 검사를 사용하지 않도록 설정합니다. [`/GS-`](gs-buffer-security-check.md)을 설정 합니다.
- **보안 검사 사용** - 보안 검사를 사용하도록 설정합니다. [`/GS`](gs-buffer-security-check.md)을 설정 합니다.

### <a name="control-flow-guard"></a>제어 흐름 보호

가드 보안 검사는 잘못 된 코드 블록에 디스패치할 시도를 검색 하는 데 도움이 됩니다.

#### <a name="choices"></a>선택 사항

- **예** -가드 집합을 사용 하 여 보안 검사를 사용 하도록 설정 [`/guard:cf`](guard-enable-control-flow-guard.md) 합니다.
- **아니요**

### <a name="enable-function-level-linking"></a>함수 수준 링크 사용

컴파일러가 개별 함수를 패키지된 함수(COMDAT)의 형태로 패키지할 수 있게 합니다. 편집에 필요하며 계속 작동합니다. [`/Gy`](gy-enable-function-level-linking.md)을 설정 합니다.

### <a name="enable-parallel-code-generation"></a>병렬 코드 생성 사용

컴파일러가 `#pragma loop(hint_parallel[(n)])` 최적화를 사용 하도록 설정 된 경우를 사용 하 여 식별 된 루프에 대해 병렬 코드를 생성할 수 있도록 합니다.

### <a name="enable-enhanced-instruction-set"></a>고급 명령 집합 사용

고급 명령 집합을 지 원하는 프로세서에 있는 지침을 사용 하도록 설정 합니다. 예를 들어 SSE, SSE2, AVX 및 AVX2는 IA-32에 대 한 향상 된 기능입니다. AVX 및 AVX2은 x64의 향상 된 기능입니다. 현재 **`/arch:SSE`** 및 **`/arch:SSE2`** 는 x86 아키텍처용으로 빌드할 때만 사용할 수 있습니다. 옵션을 지정 하지 않을 경우 컴파일러는 SSE2를 지 원하는 프로세서에 있는 명령을 사용 합니다. 에서 향상 된 지침을 사용 하지 않도록 설정할 수 있습니다 **`/arch:IA32`** . 자세한 내용은, 및을 참조 하십시오 [`/arch (x86)`](arch-x86.md) [`/arch (x64)`](arch-x64.md) [`/arch (ARM)`](arch-arm.md) .

#### <a name="choices"></a>선택 사항

- **스트리밍 Simd 확장** -스트리밍 simd 확장. 명령은  **`/arch:SSE`**
- **스트리밍 Simd 확장 2** -스트리밍 simd 확장 2 명령은  **`/arch:SSE2`**
- **고급 벡터 확장** -고급 벡터 확장. 명령은  **`/arch:AVX`**
- **고급 벡터 확장 2** -고급 벡터 확장 2 명령은  **`/arch:AVX2`**
- 향상 된 **지침이 없습니다** . 향상 된 지침은 없습니다. 명령은  **`/arch:IA32`**
- **설정** 되지 않음-설정 되지 않음

### <a name="floating-point-model"></a>부동 소수점 모델

부동 소수점 모델을 설정합니다. [ `/fp:precise` , `/fp:strict` ,를 `/fp:fast` ](fp-specify-floating-point-behavior.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **Precise** -기본값 같음 및 같지 않음에 대 한 부동 소수점 테스트의 일관성을 향상 시킵니다.
- **Strict** -가장 엄격한 부동 소수점 모델입니다. **`/fp:strict`****`fp_contract`** 가 해제 되 고가 설정 됩니다 **`fenv_access`** . **`/fp:except`** 는 암시적 이며를 명시적으로 지정 하 여 사용 하지 않도록 설정할 수 있습니다 **`/fp:except-`** . 과 함께 사용 되는 경우 **`/fp:except-`** **`/fp:strict`** 예외 이벤트를 고려 하지 않고 엄격한 부동 소수점 의미 체계를 적용 합니다.
- **Fast** -대부분의 경우 가장 빠른 코드를 만듭니다.

### <a name="enable-floating-point-exceptions"></a>부동 소수점 예외 사용

신뢰할 수 있는 부동 소수점 예외 모델입니다. 예외가 트리거되는 즉시 발생 합니다. [`/fp:except`](fp-specify-floating-point-behavior.md)을 설정 합니다.

### <a name="create-hotpatchable-image"></a>핫 패치 가능 이미지 만들기

핫 패치를 사용 하는 경우, 컴파일러는 핫 패치를 위해 필요에 따라 각 함수의 첫 번째 명령이 2 바이트 임을 확인 합니다. [`/hotpatch`](hotpatch-create-hotpatchable-image.md)을 설정 합니다.

### <a name="spectre-mitigation"></a>스펙터 완화

CVE 2017-5753에 대 한 스펙터 완화 [`/Qspectre`](qspectre.md)을 설정 합니다.

#### <a name="choices"></a>선택 사항

- **사용** -CVE 2017-5753에 대해 스펙터 완화 기능 사용
- **Disabled** -설정 되지 않았습니다.

## <a name="cc-language-properties"></a>C/c + + 언어 속성

### <a name="disable-language-extensions"></a>언어 확장 사용 안 함

언어 확장을 표시 하거나 숨깁니다. [`/Za`](za-ze-disable-language-extensions.md)을 설정 합니다.

### <a name="conformance-mode"></a>규칙 모드

규칙 모드를 사용 하거나 사용 하지 않습니다. [`/permissive-`](permissive-standards-conformance.md)을 설정 합니다.

### <a name="treat-wchar_t-as-built-in-type"></a>Wchar_t를 기본 제공 형식으로 처리

지정 된 경우 형식은에 **`wchar_t`** **`__wchar_t`** 매핑되는 것과 같은 방식으로에 매핑되는 네이티브 형식이 됩니다 **`short`** **`__int16`** . [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) 는 기본적으로 설정 되어 있습니다.

### <a name="force-conformance-in-for-loop-scope"></a>For 루프 범위 강제 규칙

`for`Microsoft 확장을 사용 하 여 문 루프의 표준 c + + 동작을 구현 합니다. 설정 [ `/Za` , `/Ze` (언어 확장 사용 안 함)](za-ze-disable-language-extensions.md) [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) 는 기본적으로 설정 되어 있습니다.

### <a name="remove-unreferenced-code-and-data"></a>참조 되지 않은 코드 및 데이터 제거

지정 된 경우 컴파일러에서 참조 되지 않은 코드 및 데이터에 대 한 기호 정보를 더 이상 생성 하지 않습니다.

### <a name="enforce-type-conversion-rules"></a>형식 변환 규칙 적용

C + + 11 표준에 따라 캐스트 연산 결과로 rvalue 참조 형식을 식별 하는 데 사용 됩니다.

### <a name="enable-run-time-type-information"></a>런타임 형식 정보 사용

런타임에 c + + 개체 형식 (*런타임 형식 정보*또는 RTTI)을 확인 하는 코드를 추가 합니다. [ `/GR` 을 `/GR-` ](gr-enable-run-time-type-information.md)설정 합니다.

### <a name="open-mp-support"></a>MP 지원 열기

OpenMP 2.0 언어 확장을 사용 합니다. [`/openmp`](openmp-enable-openmp-2-0-support.md)을 설정 합니다.

### <a name="c-language-standard"></a>C++ 언어 표준

컴파일러가 사용 하는 c + + 언어 표준을 결정 합니다. 가능 하면 최신 버전을 사용 합니다. [ `/std:c++14` , `/std:c++17` ,를 `/std:c++latest` ](std-specify-language-standard-version.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **기본값**
- **ISO c + + 14 표준**
- **ISO c + + 17 표준**
- **미리 보기-최신 c + + 작업 초안의 기능**

### <a name="enable-c-modules-experimental"></a>C + + 모듈 사용 (실험적)

C + + 모듈 TS 및 표준 라이브러리 모듈에 대 한 실험적 지원.

## <a name="cc-precompiled-headers-properties"></a>C/c + + 미리 컴파일된 헤더 속성

### <a name="createuse-precompiled-header"></a>미리 컴파일된 헤더 만들기/사용

빌드하는 동안 미리 컴파일된 헤더를 만들거나 사용하도록 설정합니다. [`/Yc`](yc-create-precompiled-header-file.md)을 설정 [`/Yu`](yu-use-precompiled-header-file.md) 합니다.

#### <a name="choices"></a>선택 사항

- **Create** - *`.pch`* 특정 지점에서 컴파일 상태를 나타내는 미리 컴파일된 헤더 () 파일을 만들도록 컴파일러에 지시 합니다.
- **사용** -현재 컴파일에서 미리 컴파일된 헤더 () 파일을 사용 하도록 컴파일러에 지시 *`.pch`* 합니다.
- 미리 컴파일된 헤더를 사용 **하지 않습니다.** 미리 컴파일된 헤더를 사용 하지 않습니다.

### <a name="precompiled-header-file"></a>미리 컴파일된 헤더 파일

미리 컴파일된 헤더 파일을 만들거나 사용할 때 사용할 헤더 파일 이름을 지정 합니다. [`/Yc`](yc-create-precompiled-header-file.md)을 설정 [`/Yu`](yu-use-precompiled-header-file.md) 합니다.

### <a name="precompiled-header-output-file"></a>미리 컴파일된 헤더 출력 파일

생성 된 미리 컴파일된 헤더 파일의 경로 또는 이름을 지정 합니다. [`/Fp`](fp-name-dot-pch-file.md)을 설정 합니다.

## <a name="cc-output-files-properties"></a>C/c + + 출력 파일 속성

### <a name="expand-attributed-source"></a>특성 사용 소스 확장

원본 파일에 확장 된 특성을 삽입 한 목록 파일을 만듭니다. [`/Fx`](fx-merge-injected-code.md)을 설정 합니다.

### <a name="assembler-output"></a>어셈블러 출력

어셈블리 언어 출력 파일의 콘텐츠를 지정합니다. [ `/FA` ,, `/FAc` `/FAs` , `/FAcs` ](fa-fa-listing-file.md)를 설정 합니다.

#### <a name="choices"></a>선택 사항

- **목록 없음-나열** 되지 않습니다.
- **어셈블리 전용 목록** -어셈블리 코드 *`.asm`*
- **컴퓨터 코드와 어셈블리 코드를 사용 하는 어셈블리***`.cod`*
- 소스 코드 소스 및 어셈블리 코드 **를 포함 하는 어셈블리***`.asm`*
- **어셈블리, 기계어 코드 및 소스** -어셈블리, 기계어 코드 및 소스 코드 *`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>어셈블러 목록에 유니코드 사용

출력 파일이 UTF-8 형식으로 생성 되도록 합니다.

### <a name="asm-list-location"></a>ASM 목록 위치

ASM 목록 파일의 상대 경로 또는 이름을 지정 합니다. 파일 또는 디렉터리 이름일 수 있습니다. [`/Fa`](fa-fa-listing-file.md)을 설정 합니다.

### <a name="object-file-name"></a>개체 파일 이름

기본 개체 파일 이름을 재정의할 이름을 지정합니다. 파일 또는 디렉터리 이름일 수 있습니다. [`/Fo`](fo-object-file-name.md)을 설정 합니다.

### <a name="program-database-file-name"></a>프로그램 데이터베이스 파일 이름

컴파일러에서 생성 된 PDB 파일의 이름을 지정 합니다. 또한 컴파일러에서 생성 된 필수 .IDB 파일의 기본 이름을 지정 합니다. 파일 또는 디렉터리 이름일 수 있습니다. [`/Fd`](fd-program-database-file-name.md)을 설정 합니다.

### <a name="generate-xml-documentation-files"></a>XML 문서 파일 생성

컴파일러가 XML 문서 주석 파일 ()을 생성 하도록 지정 합니다. .XDC). [`/doc`](doc-process-documentation-comments-c-cpp.md)을 설정 합니다.

### <a name="xml-documentation-file-name"></a>XML 문서 파일 이름

생성 된 XML 문서 파일의 이름을 지정 합니다. 파일 또는 디렉터리 이름일 수 있습니다. [`/doc:`\<name>](doc-process-documentation-comments-c-cpp.md)을 설정 합니다.

## <a name="cc-browse-information-properties"></a>C/c + + 찾아보기 정보 속성

### <a name="enable-browse-information"></a>찾아보기 정보 사용

파일의 찾아보기 정보 수준을 지정 합니다 *`.bsc`* . [`/FR`](fr-fr-create-dot-sbr-file.md)을 설정 합니다.

### <a name="browse-information-file"></a>찾아보기 정보 파일

브라우저 정보 파일의 선택적 이름을 지정 합니다. [`/FR`\<name>](fr-fr-create-dot-sbr-file.md)을 설정 합니다.

## <a name="cc-advanced-properties"></a>C/c + + 고급 속성

### <a name="calling-convention"></a>호출 규칙

응용 프로그램에 대 한 기본 호출 규칙을 선택 합니다 (함수로 재정의할 수 있음). [ `/Gd` ,, `/Gr` `/Gz` , `/Gv` ](gd-gr-gv-gz-calling-convention.md)를 설정 합니다.

#### <a name="choices"></a>선택 사항

- **`__cdecl`** - **`__cdecl`** C + + 멤버 함수 및 또는로 표시 된 함수를 제외한 모든 함수에 대해 호출 규칙을 지정 합니다 **`__stdcall`** **`__fastcall`** .
- **`__fastcall`** - **`__fastcall`** C + + 멤버 함수 및 또는로 표시 된 함수를 제외한 모든 함수에 대해 호출 규칙을 지정 합니다 **`__cdecl`** **`__stdcall`** . 모든 **`__fastcall`** 함수에는 프로토타입이 있어야 합니다.
- **`__stdcall`** - **`__stdcall`** C + + 멤버 함수 및 또는로 표시 된 함수를 제외한 모든 함수에 대해 호출 규칙을 지정 합니다 **`__cdecl`** **`__fastcall`** . 모든 **`__stdcall`** 함수에는 프로토타입이 있어야 합니다.
- **`__vectorcall`** - **`__vectorcall`** C + + 멤버 함수 및, 또는로 표시 된 함수를 제외한 모든 함수에 대해 호출 규칙을 지정 합니다 **`__cdecl`** **`__fastcall`** **`__stdcall`** . 모든 **`__vectorcall`** 함수에는 프로토타입이 있어야 합니다.

### <a name="compile-as"></a>다음으로 컴파일

및 파일에 대 한 컴파일 언어 옵션을 선택 *`.c`* *`.cpp`* 합니다. [ `/TC` 을 `/TP` ](tc-tp-tc-tp-specify-source-file-type.md)설정 합니다.

#### <a name="choices"></a>선택 사항

- **기본값** - 기본값입니다.
- **C 코드로 컴파일** -c 코드로 컴파일합니다.
- **C++ 코드로 컴파일** - C++ 코드로 컴파일합니다.

### <a name="disable-specific-warnings"></a>특정 경고 사용 안 함

지정 된 경고 번호를 사용 하지 않도록 설정 합니다. 경고 번호를 세미콜론으로 구분 된 목록으로 입력 합니다. [`/wd`\<number>](compiler-option-warning-level.md)을 설정 합니다.

### <a name="forced-include-file"></a>강제 포함 파일

하나 이상의 강제 포함 파일입니다. [`/FI`\<name>](fi-name-forced-include-file.md)을 설정 합니다.

### <a name="forced-using-file"></a>강제 #using 파일

강제 #using 파일을 하나 이상 지정 합니다. [`/FU`\<name>](fu-name-forced-hash-using-file.md)을 설정 합니다.

### <a name="show-includes"></a>포함 표시

컴파일러 출력으로 포함 파일 목록을 생성합니다. [`/showIncludes`](showincludes-list-include-files.md)을 설정 합니다.

### <a name="use-full-paths"></a>전체 경로 사용

진단 메시지에 전체 경로를 사용 합니다. [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md)을 설정 합니다.

### <a name="omit-default-library-name"></a>기본 라이브러리 이름 생략

파일에 기본 라이브러리 이름을 포함 하지 않습니다 *`.obj`* . [`/Zl`](zl-omit-default-library-name.md)을 설정 합니다.

### <a name="internal-compiler-error-reporting"></a>내부 컴파일러 오류 보고

> [!NOTE]
> 이 옵션은 사용되지 않습니다. Windows Vista부터 오류 보고는 [WER (Windows 오류 보고)](/windows/win32/wer/windows-error-reporting) 설정에 의해 제어 됩니다.

### <a name="treat-specific-warnings-as-errors"></a>특정 경고를 오류로 처리

는 특정 컴파일러 경고를 오류로 처리 합니다. 여기서 n은 컴파일러 경고입니다.

### <a name="additional-options"></a>추가 옵션

추가 옵션입니다.
