---
title: 컴파일러 옵션 범주별 목록
description: Microsoft C/c + + 컴파일러 명령줄 옵션 범주별 참조 목록입니다.
ms.date: 07/29/2020
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: bf12948658b5f7e3211c423b5302bc52d1b87729
ms.sourcegitcommit: 48b897797b3132ae934b1d191e3870c3c2466335
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97514564"
---
# <a name="compiler-options-listed-by-category"></a>컴파일러 옵션 범주별 목록

이 문서에는 컴파일러 옵션의 범주별 목록이 포함되어 있습니다. 사전순 목록에 대해서는 [컴파일러 옵션 사전순](compiler-options-listed-alphabetically.md)목록을 참조 하세요.

## <a name="optimization"></a>최적화

| 옵션 | 용도 |
|--|--|
| [`/O1`](o1-o2-minimize-size-maximize-speed.md) | 작은 코드를 만듭니다. |
| [`/O2`](o1-o2-minimize-size-maximize-speed.md) | 빠른 코드를 만듭니다. |
| [`/Ob`](ob-inline-function-expansion.md) | 인라인 확장을 제어합니다. |
| [`/Od`](od-disable-debug.md) | 최적화를 사용하지 않습니다. |
| [`/Og`](og-global-optimizations.md) | 더 이상 사용되지 않습니다. 전역 최적화를 사용합니다. |
| [`/Oi`](oi-generate-intrinsic-functions.md) | 내장 함수를 생성합니다. |
| [`/Os`](os-ot-favor-small-code-favor-fast-code.md) | 코드 크기를 우선으로 합니다. |
| [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) | 코드 속도를 우선으로 합니다. |
| [`/Ox`](ox-full-optimization.md) | /GF 또는/Gy. 포함 하지 않는/O2의 하위 집합입니다. |
| [`/Oy`](oy-frame-pointer-omission.md) | 프레임 포인터를 생략합니다. (x86 전용) |
| [`/favor`](favor-optimize-for-architecture-specifics.md) | 지정된 아키텍처나 아키텍처 범주에 최적화된 코드를 생성합니다. |

## <a name="code-generation"></a>코드 생성

| 옵션 | 용도 |
|--|--|
| [`/arch`](arch-x86.md) | 코드 생성 시 SSE 또는 SSE2 명령을 사용합니다. (x86 전용) |
| [`/clr`](clr-common-language-runtime-compilation.md) | 공용 언어 런타임에 실행할 출력 파일을 생성합니다. |
| [`/EH`](eh-exception-handling-model.md) | 예외 처리 모델을 지정합니다. |
| [`/fp`](fp-specify-floating-point-behavior.md) | 부동 소수점 동작을 지정합니다. |
| [`/GA`](ga-optimize-for-windows-application.md) | Windows 애플리케이션에 맞게 최적화합니다. |
| [`/Gd`](gd-gr-gv-gz-calling-convention.md) | **`__cdecl`** 호출 규칙을 사용 합니다. (x86 전용) |
| [`/Ge`](ge-enable-stack-probes.md) | 더 이상 사용되지 않습니다. 스택 프로브를 활성화합니다. |
| [`/GF`](gf-eliminate-duplicate-strings.md) | 문자열 풀링을 사용합니다. |
| [`/Gh`](gh-enable-penter-hook-function.md) | 후크 함수 `_penter`를 호출합니다. |
| [`/GH`](gh-enable-pexit-hook-function.md) | 후크 함수 `_pexit`를 호출합니다. |
| [`/GL`](gl-whole-program-optimization.md) | 전체 프로그램 최적화를 사용합니다. |
| [`/Gm`](gm-enable-minimal-rebuild.md) | 더 이상 사용되지 않습니다. 최소 재빌드를 사용합니다. |
| [`/GR`](gr-enable-run-time-type-information.md) | RTTI(런타임 형식 정보)를 사용합니다. |
| [`/Gr`](gd-gr-gv-gz-calling-convention.md) | **`__fastcall`** 호출 규칙을 사용 합니다. (x86 전용) |
| [`/GS`](gs-buffer-security-check.md) | 버퍼 보안을 검사합니다. |
| [`/Gs`](gs-control-stack-checking-calls.md) | 스택 프로브를 제어합니다. |
| [`/GT`](gt-support-fiber-safe-thread-local-storage.md) | 정적 스레드 로컬 스토리지를 사용하여 할당한 데이터의 파이버 안전을 지원합니다. |
| [`/guard:cf`](guard-enable-control-flow-guard.md) | 제어 흐름 가드 보안 검사를 추가합니다. |
| [`/guard:ehcont`](guard-enable-eh-continuation-metadata.md) | EH 연속 메타 데이터를 사용 하도록 설정 합니다. |
| [`/Gv`](gd-gr-gv-gz-calling-convention.md) | **`__vectorcall`** 호출 규칙을 사용 합니다. 및 x64에만 해당). |
| [`/Gw`](gw-optimize-global-data.md) | 전체 프로그램 전역 데이터 최적화를 사용하도록 설정합니다. |
| [`/GX`](gx-enable-exception-handling.md) | 더 이상 사용되지 않습니다. 동기 예외 처리를 사용합니다. [`/EH`](eh-exception-handling-model.md)대신를 사용 합니다. |
| [`/Gy`](gy-enable-function-level-linking.md) | 함수 수준 링크를 사용합니다. |
| [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) | 더 이상 사용되지 않습니다. 빠른 검사를 사용하도록 설정합니다. (와 동일 [`/RTC1`](rtc-run-time-error-checks.md) ) |
| [`/Gz`](gd-gr-gv-gz-calling-convention.md) | **`__stdcall`** 호출 규칙을 사용 합니다. (x86 전용) |
| [`/homeparams`](homeparams-copy-register-parameters-to-stack.md) | 레지스터에 전달된 매개 변수를 함수 시작 시 스택의 해당 위치에 기록합니다. 이 컴파일러 옵션은 x64 컴파일러 (네이티브 및 크로스 컴파일)에만 사용할 수 있습니다. |
| [`/hotpatch`](hotpatch-create-hotpatchable-image.md) | 핫 패치할 수 있는 이미지를 만듭니다. |
| [`/Qfast_transcendentals`](qfast-transcendentals-force-fast-transcendentals.md) | 빠른 초월수를 생성합니다. |
| [`/QIfist`](qifist-suppress-ftol.md) | 더 이상 사용되지 않습니다. 부동 소수점 형식에서 정수 계열 형식으로 변환해야 할 때 도우미 함수 `_ftol` 이 호출되지 않도록 합니다. (x86 전용) |
| [`/Qimprecise_fwaits`](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md) | `fwait`블록 내에 있는 명령을 제거 **`try`** 합니다. |
| [`/QIntel-jcc-erratum`](qintel-jcc-erratum.md) | Intel JCC erratum 마이크로코드 업데이트의 성능 영향을 완화 합니다. |
| [`/Qpar`](qpar-auto-parallelizer.md) | 루프 자동 병렬화를 사용하도록 설정합니다. |
| [`/Qpar-report`](qpar-report-auto-parallelizer-reporting-level.md) | 자동 병렬화에 대한 보고 수준을 사용하도록 설정합니다. |
| [`/Qsafe_fp_loads`](qsafe-fp-loads.md) | 부동 소수점 값에 대한 정수 이동 명령을 사용하고 특정 부동 소수점 부하 최적화를 사용하지 않도록 설정합니다. |
| [`/Qspectre`](qspectre.md) | 스펙터 공격의 클래스에 대해 CVE 2017-5753에 대 한 완화를 사용 하도록 설정 합니다. |
| [`/Qspectre-load`](qspectre-load.md) | 모든 로드 명령에 대 한 직렬화 명령을 생성 합니다. |
| [`/Qspectre-load-cf`](qspectre-load-cf.md) | 메모리를 로드 하는 모든 제어 흐름 명령에 대 한 직렬화 명령을 생성 합니다. |
| [`/Qvec-report`](qvec-report-auto-vectorizer-reporting-level.md) | 자동 벡터화에 대한 보고 수준을 사용하도록 설정합니다. |
| [`/RTC`](rtc-run-time-error-checks.md) | 런타임 오류 검사를 사용합니다. |
| [`/volatile`](volatile-volatile-keyword-interpretation.md) | volatile 키워드가 해석되는 방식을 선택합니다. |

## <a name="output-files"></a>출력 파일

| 옵션 | 용도 |
|--|--|
| [`/doc`](doc-process-documentation-comments-c-cpp.md) | XML 파일에 대해 문서 주석을 처리합니다. |
| [`/FA`](fa-fa-listing-file.md) | 어셈블리 목록 파일을 구성합니다. |
| [`/Fa`](fa-fa-listing-file.md) | 어셈블리 목록 파일을 만듭니다. |
| [`/Fd`](fd-program-database-file-name.md) | 프로그램 데이터베이스 파일 이름을 바꿉니다. |
| [`/Fe`](fe-name-exe-file.md) | 실행 파일 이름을 바꿉니다. |
| [`/Fi`](fi-preprocess-output-file-name.md) | 전처리된 출력 파일 이름을 지정합니다. |
| [`/Fm`](fm-name-mapfile.md) | 맵 파일을 만듭니다. |
| [`/Fo`](fo-object-file-name.md) | 개체 파일을 만듭니다. |
| [`/Fp`](fp-name-dot-pch-file.md) | 미리 컴파일된 헤더 파일 이름을 지정합니다. |
| [`/FR`, `/Fr`](fr-fr-create-dot-sbr-file.md) | 생성 된 *`.sbr`* 브라우저 파일의 이름입니다. |

## <a name="preprocessor"></a>전처리기

| 옵션 | 용도 |
|--|--|
| [`/AI`](ai-specify-metadata-directories.md) | [#using](../../preprocessor/hash-using-directive-cpp.md) 지시문에 전달된 파일 참조를 확인하기 위해 검색할 디렉터리를 지정합니다. |
| [`/C`](c-preserve-comments-during-preprocessing.md) | 전처리하는 동안 주석을 유지합니다. |
| [`/D`](d-preprocessor-definitions.md) | 상수와 매크로를 정의합니다. |
| [`/E`](e-preprocess-to-stdout.md) | 전처리기 출력을 표준 출력에 복사합니다. |
| [`/EP`](ep-preprocess-to-stdout-without-hash-line-directives.md) | 전처리기 출력을 표준 출력에 복사합니다. |
| [`/FI`](fi-name-forced-include-file.md) | 지정된 포함 파일을 전처리합니다. |
| [`/FU`](fu-name-forced-hash-using-file.md) | 는 [#using](../../preprocessor/hash-using-directive-cpp.md) 지시문에 전달 된 것 처럼 파일 이름을 사용 하도록 합니다. |
| [`/Fx`](fx-merge-injected-code.md) | 삽입된 코드와 소스 파일을 병합합니다. |
| [`/I`](i-additional-include-directories.md) | 포함 파일의 디렉터리를 검색합니다. |
| [`/P`](p-preprocess-to-a-file.md) | 전처리기 출력을 파일에 씁니다. |
| [`/U`](u-u-undefine-symbols.md) | 미리 정의된 매크로를 제거합니다. |
| [`/u`](u-u-undefine-symbols.md) | 미리 정의된 모든 매크로를 제거합니다. |
| [`/X`](x-ignore-standard-include-paths.md) | 표준 포함 디렉터리를 무시합니다. |

## <a name="language"></a>언어

| 옵션 | 용도 |
|--|--|
| [`/constexpr`](constexpr-control-constexpr-evaluation.md) | **`constexpr`** 컴파일 시간에 컨트롤 평가 |
| [`/openmp`](openmp-enable-openmp-2-0-support.md) | [`#pragma omp`](../../preprocessor/omp.md)소스 코드에서를 사용 하도록 설정 합니다. |
| [`/vd`](vd-disable-construction-displacements.md) | 숨겨진 `vtordisp` 클래스 멤버를 사용하도록 설정하거나 표시하지 않습니다. |
| [`/vmb`](vmb-vmg-representation-method.md) | 멤버의 포인터에 best case를 사용합니다. |
| [`/vmg`](vmb-vmg-representation-method.md) | 멤버의 포인터에 full generality를 사용합니다. |
| [`/vmm`](vmm-vms-vmv-general-purpose-representation.md) | 다중 상속을 선언합니다. |
| [`/vms`](vmm-vms-vmv-general-purpose-representation.md) | 단일 상속을 선언합니다. |
| [`/vmv`](vmm-vms-vmv-general-purpose-representation.md) | 가상 상속을 선언합니다. |
| [`/Z7`](z7-zi-zi-debug-information-format.md) | C 7.0 호환 디버깅 정보를 생성 합니다. |
| [`/Za`](za-ze-disable-language-extensions.md) | C89 언어 확장을 사용 하지 않도록 설정 합니다. |
| [`/Zc`](zc-conformance.md) | 에서 표준 동작을 지정 합니다 [`/Ze`](za-ze-disable-language-extensions.md) . |
| [`/Ze`](za-ze-disable-language-extensions.md) | 더 이상 사용되지 않습니다. C89 언어 확장을 사용 합니다. |
| [`/Zf`](zf.md) | 병렬 빌드에서 PDB 생성 시간을 향상 시킵니다. |
| [`/ZH`](zh.md) | 디버그 정보에서 체크섬에 대해 MD5, SHA-1 또는 SHA-256을 지정 합니다. |
| [`/ZI`](z7-zi-zi-debug-information-format.md) | 편집하며 계속하기와 호환되는 프로그램 데이터베이스에 디버깅 정보를 포함합니다. (x86 전용) |
| [`/Zi`](z7-zi-zi-debug-information-format.md) | 완전한 디버깅 정보를 생성합니다. |
| [`/Zl`](zl-omit-default-library-name.md) | 파일에서 기본 라이브러리 이름을 제거 합니다 *`.obj`* . |
| [`/Zp`](zp-struct-member-alignment.md)*n* | 구조체 멤버를 압축합니다. |
| [`/Zs`](zs-syntax-check-only.md) | 구문만 확인합니다. |
| [`/ZW`](zw-windows-runtime-compilation.md) | Windows 런타임에서 실행할 출력 파일을 생성 합니다. |

## <a name="linking"></a>연결

| 옵션 | 용도 |
|--|--|
| [`/F`](f-set-stack-size.md) | 스택 크기를 설정합니다. |
| [`/LD`](md-mt-ld-use-run-time-library.md) | DLL(동적 연결 라이브러리)을 만듭니다. |
| [`/LDd`](md-mt-ld-use-run-time-library.md) | 디버그 DLL(동적 연결 라이브러리)을 만듭니다. |
| [`/link`](link-pass-options-to-linker.md) | 지정된 옵션을 LINK에 전달합니다. |
| [`/LN`](ln-create-msil-module.md) | MSIL 모듈을 만듭니다. |
| [`/MD`](md-mt-ld-use-run-time-library.md) | *Msvcrt.lib* 를 사용 하 여 다중 스레드 DLL을 만들도록 컴파일합니다. |
| [`/MDd`](md-mt-ld-use-run-time-library.md) | *Msvcrtd.lib* 를 사용 하 여 디버그 다중 스레드 DLL을 만들도록 컴파일합니다. |
| [`/MT`](md-mt-ld-use-run-time-library.md) | *Libcmt.lib* 를 사용 하 여 다중 스레드 실행 파일을 만들기 위해 컴파일합니다. |
| [`/MTd`](md-mt-ld-use-run-time-library.md) | *Libcmtd.lib* 를 사용 하 여 디버그 다중 스레드 실행 파일을 만들기 위해 컴파일합니다. |

## <a name="miscellaneous"></a>기타

| 옵션 | 용도 |
|--|--|
| [`/?`](help-compiler-command-line-help.md) | 컴파일러 옵션을 나열합니다. |
| [`@`](at-specify-a-compiler-response-file.md) | 지시 파일을 지정합니다. |
| [`/analyze`](analyze-code-analysis.md) | 코드 분석을 활성화합니다. |
| [`/bigobj`](bigobj-increase-number-of-sections-in-dot-obj-file.md) | .obj 파일에서 주소 지정 가능한 섹션의 수를 늘립니다. |
| [`/c`](c-compile-without-linking.md) | 링크하지 않고 컴파일합니다. |
| [`/cgthreads`](cgthreads-code-generation-threads.md) | 최적화 및 코드 생성에 사용할 *cl.exe* 스레드 수를 지정 합니다. |
| [`/errorReport`](errorreport-report-internal-compiler-errors.md) | 더 이상 사용되지 않습니다. 오류 보고는 [WER (Windows 오류 보고)](/windows/win32/wer/windows-error-reporting) 설정에 의해 제어 됩니다. |
| [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) | 진단 텍스트에서 *cl.exe* 에 전달 된 소스 코드 파일의 전체 경로를 표시 합니다. |
| [`/FS`](fs-force-synchronous-pdb-writes.md) | *MSPDBSRV.EXE* 를 통해 SERIALIZE 될 PDB 파일에 대 한 쓰기를 강제로 수행 합니다. |
| [`/H`](h-restrict-length-of-external-names.md) | 더 이상 사용되지 않습니다. 외부 공개 이름의 길이를 제한합니다. |
| [`/HELP`](help-compiler-command-line-help.md) | 컴파일러 옵션을 나열합니다. |
| [`/J`](j-default-char-type-is-unsigned.md) | 기본 형식을 변경 **`char`** 합니다. |
| [`/JMC`](jmc.md) | 네이티브 c + + 내 코드만 디버깅을 지원 합니다. |
| [`/kernel`](kernel-create-kernel-mode-binary.md) | 컴파일러와 링커는 Windows 커널에서 실행할 수 있는 이진 파일을 만듭니다. |
| [`/MP`](mp-build-with-multiple-processes.md) | 여러 개의 소스 파일을 동시에 빌드합니다. |
| [`/nologo`](nologo-suppress-startup-banner-c-cpp.md) | 초기 화면 배너를 표시하지 않습니다. |
| [`/sdl`](sdl-enable-additional-security-checks.md) | 추가 보안 기능 및 경고를 사용하도록 설정합니다. |
| [`/showIncludes`](showincludes-list-include-files.md) | 컴파일하는 동안 전체 포함 파일의 목록을 표시합니다. |
| [`/sourceDependencies`](sourcedependencies.md) | 헤더, 모듈 및 기타 소스 종속성을 나열 합니다. |
| [`/Tc`](tc-tp-tc-tp-specify-source-file-type.md) | C 소스 파일을 지정합니다. |
| [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) | 모든 소스 파일을 C로 지정 합니다. |
| [`/Tp`](tc-tp-tc-tp-specify-source-file-type.md) | C++ 소스 파일을 지정합니다. |
| [`/TP`](tc-tp-tc-tp-specify-source-file-type.md) | 모든 소스 파일을 c + +로 지정 합니다. |
| [`/V`](v-version-number.md) | 더 이상 사용되지 않습니다. 버전 문자열을 설정합니다. |
| [`/w`](compiler-option-warning-level.md) | 모든 경고를 사용하지 않습니다. |
| [`/W0`, `/W1`, `/W2`, `/W3`, `/W4`](compiler-option-warning-level.md) | 출력 경고 수준을 설정합니다. |
| [`/w1`, `/w2`, `/w3`, `/w4`](compiler-option-warning-level.md) | 지정된 경고에 대한 경고 수준을 설정합니다. |
| [`/Wall`](compiler-option-warning-level.md) | 기본적으로 비활성화되는 경고를 포함하여 모든 경고를 활성화합니다. |
| [`/wd`](compiler-option-warning-level.md) | 지정된 경고를 사용하지 않습니다. |
| [`/we`](compiler-option-warning-level.md) | 지정된 경고를 오류로 처리합니다. |
| [`/WL`](wl-enable-one-line-diagnostics.md) | 명령줄에서 C++ 소스 코드를 컴파일할 때 오류 및 경고 메시지에 한 줄 진단을 사용합니다. |
| [`/wo`](compiler-option-warning-level.md) | 지정된 경고를 한 번만 표시합니다. |
| [`/Wv`](compiler-option-warning-level.md) | 이후 버전의 컴파일러에서 도입된 경고를 사용하지 않습니다. |
| [`/WX`](compiler-option-warning-level.md) | 경고를 오류로 처리합니다. |
| [`/Yc`](yc-create-precompiled-header-file.md) | *`.PCH`* 파일을 만듭니다. |
| [`/Yd`](yd-place-debug-information-in-object-file.md) | 더 이상 사용되지 않습니다. 모든 개체 파일에 완전한 디버깅 정보를 저장합니다. [`/Zi`](z7-zi-zi-debug-information-format.md)대신를 사용 합니다. |
| [`/Yl`](yl-inject-pch-reference-for-debug-library.md) | 디버그 라이브러리를 만들 때 PCH 참조를 삽입합니다. |
| [`/Yu`](yu-use-precompiled-header-file.md) | 빌드하는 동안 미리 컴파일된 헤더 파일을 사용합니다. |
| [`/Y-`](y-ignore-precompiled-header-options.md) | 현재 빌드에서 미리 컴파일된 다른 모든 헤더 컴파일러 옵션을 무시합니다. |
| [`/Zm`](zm-specify-precompiled-header-memory-allocation-limit.md) | 미리 컴파일된 헤더 메모리의 할당 제한을 지정합니다. |
| [`/await`](await-enable-coroutine-support.md) | 코 루틴 (다시 시작 가능한 함수) 확장을 사용 하도록 설정 합니다. |
| [`/source-charset`](source-charset-set-source-character-set.md) | 원본 문자 집합을 설정 합니다. |
| [`/execution-charset`](execution-charset-set-execution-character-set.md) | 실행 문자 집합을 설정 합니다. |
| [`/utf-8`](utf-8-set-source-and-executable-character-sets-to-utf-8.md) | 원본 및 실행 문자 집합을 u t f-8로 설정 합니다. |
| [`/validate-charset`](validate-charset-validate-for-compatible-characters.md) | 호환 되는 문자만을 위한 UTF-8 파일의 유효성을 검사 합니다. |
| [`/diagnostics`](diagnostics-compiler-diagnostic-options.md) | 진단 메시지의 형식을 제어 합니다. |
| [`/permissive-`](permissive-standards-conformance.md) | 표준 규칙 모드를 설정 합니다. |
| [`/std`](std-specify-language-standard-version.md) | C + + 표준 버전 호환성 선택기입니다. |

## <a name="experimental-options"></a>실험적 옵션

실험적 옵션은 특정 버전의 컴파일러 에서만 지원 될 수 있습니다. 다른 컴파일러 버전에서 다르게 동작할 수도 있습니다. 일반적으로 실험적 옵션에 대 한 설명서는 [Microsoft c + + 팀 블로그](https://devblogs.microsoft.com/cppblog/)에 있습니다.

| 옵션 | 용도 |
|--|--|
| [`/experimental:module`](experimental-module.md) | 실험적 모듈 지원을 사용 하도록 설정 합니다. |
| [`/experimental:preprocessor`](experimental-preprocessor.md) | 더 이상 사용되지 않습니다. 실험적 규격 전처리기 지원을 사용 하도록 설정 합니다. 사용 [`/Zc:preprocessor`](zc-preprocessor.md) |

## <a name="deprecated-and-removed-compiler-options"></a>사용 되지 않고 제거 되는 컴파일러 옵션

| 옵션 | 용도 |
|--|--|
| [`/clr:noAssembly`](clr-common-language-runtime-compilation.md) | 더 이상 사용되지 않습니다. 대신 [ `/LN` (MSIL 모듈 만들기)를](ln-create-msil-module.md) 사용 합니다. |
| [`/errorReport`](errorreport-report-internal-compiler-errors.md) | 더 이상 사용되지 않습니다. 오류 보고는 [WER (Windows 오류 보고)](/windows/win32/wer/windows-error-reporting) 설정에 의해 제어 됩니다. |
| [`/Fr`](fr-fr-create-dot-sbr-file.md) | 더 이상 사용되지 않습니다. 지역 변수 없이 찾아보기 정보 파일을 만듭니다. |
| [`/Ge`](ge-enable-stack-probes.md) | 더 이상 사용되지 않습니다. 스택 프로브를 활성화합니다. 기본적으로 설정되어 있습니다. |
| [`/Gm`](gm-enable-minimal-rebuild.md) | 더 이상 사용되지 않습니다. 최소 재빌드를 사용합니다. |
| [`/GX`](gx-enable-exception-handling.md) | 더 이상 사용되지 않습니다. 동기 예외 처리를 사용합니다. [`/EH`](eh-exception-handling-model.md)대신를 사용 합니다. |
| [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) | 더 이상 사용되지 않습니다. 빠른 검사를 사용하도록 설정합니다. [`/RTC1`](rtc-run-time-error-checks.md)대신를 사용 합니다. |
| [`/H`](h-restrict-length-of-external-names.md) | 더 이상 사용되지 않습니다. 외부 공개 이름의 길이를 제한합니다. |
| [`/Og`](og-global-optimizations.md) | 더 이상 사용되지 않습니다. 전역 최적화를 사용합니다. |
| [`/QIfist`](qifist-suppress-ftol.md) | 더 이상 사용되지 않습니다. 부동 소수점 형식에서 정수 계열 형식으로 변환하는 방법을 지정하는 데 사용되었습니다. |
| [`/V`](v-version-number.md) | 더 이상 사용되지 않습니다. *`.obj`* 파일 버전 문자열을 설정 합니다. |
| [`/Wp64`](wp64-detect-64-bit-portability-issues.md) | 사용되지 않습니다. 64비트 이식성 문제를 검색합니다. |
| [`/Yd`](yd-place-debug-information-in-object-file.md) | 더 이상 사용되지 않습니다. 모든 개체 파일에 완전한 디버깅 정보를 저장합니다. [`/Zi`](z7-zi-zi-debug-information-format.md)대신를 사용 합니다. |
| [`/Zc:forScope-`](zc-forscope-force-conformance-in-for-loop-scope.md) | 더 이상 사용되지 않습니다. for 루프 범위의 규칙을 사용하지 않도록 설정합니다. |
| [`/Ze`](za-ze-disable-language-extensions.md) | 더 이상 사용되지 않습니다. 언어 확장을 사용합니다. |
| [`/Zg`](zg-generate-function-prototypes.md) | Visual Studio 2015에서 제거 되었습니다. 함수 프로토타입을 생성합니다. |

## <a name="see-also"></a>참고 항목

[C/c + + 빌드 참조](c-cpp-building-reference.md)\
[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
