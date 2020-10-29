---
title: /openmp (OpenMP 지원 사용)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: 6bd1ffcd9b21bfe22ed9424ee77edf43100abf6c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921232"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (OpenMP 지원 사용)

컴파일러가 [`#pragma omp`](../../preprocessor/omp.md) OpenMP를 지 원하는 지시문을 처리 하도록 합니다.

## <a name="syntax"></a>구문

::: moniker range=">= msvc-160"

> **/openmp** \[ **:**__실험적__ ]

::: moniker-end

::: moniker range="<= msvc-150"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>설명

`#pragma omp` 는 [지시문](../../parallel/openmp/reference/openmp-directives.md) 과 [절](../../parallel/openmp/reference/openmp-clauses.md)을 지정 하는 데 사용 됩니다. 컴파일에 **/openmp** 가 지정 되지 않은 경우 컴파일러는 openmp 절 및 지시문을 무시 합니다. **/Openmp** 가 지정 되지 않은 경우에도 [OpenMP 함수](../../parallel/openmp/reference/openmp-functions.md) 호출은 컴파일러에 의해 처리 됩니다.

::: moniker range=">= msvc-160"

C + + 컴파일러는 현재 OpenMP 2.0 표준을 지원 합니다. 그러나 이제 Visual Studio 2019에서는 SIMD 기능을 제공 합니다. SIMD를 사용 하려면 **/openmp: 실험적** 옵션을 사용 하 여 컴파일합니다. 이 옵션을 사용 하면 일반적인 OpenMP 기능과 **/openmp** 스위치를 사용할 때 사용할 수 없는 추가 openmp SIMD 기능을 모두 사용할 수 있습니다.

::: moniker-end

**/Openmp** 및 **/clr** 을 모두 사용 하 여 컴파일된 응용 프로그램은 단일 응용 프로그램 도메인 프로세스 에서만 실행할 수 있습니다. 여러 응용 프로그램 도메인은 지원 되지 않습니다. 즉, 모듈 생성자 ( `.cctor` )가 실행 되 면 **/openmp** 를 사용 하 여 프로세스가 컴파일되는지 여부와 앱이 기본이 아닌 런타임에 로드 되는지 검색 합니다. 자세한 내용은 [appdomain](../../cpp/appdomain.md), [/Clr (공용 언어 런타임 컴파일)](clr-common-language-runtime-compilation.md)및 [혼합 어셈블리 초기화](../../dotnet/initialization-of-mixed-assemblies.md)를 참조 하세요.

**/Openmp** 와 **/clr** 을 모두 사용 하 여 컴파일된 앱을 기본이 아닌 응용 프로그램 도메인에 로드 하려고 하면 <xref:System.TypeInitializationException> 예외가 디버거 외부에서 throw 되 고 디버거에서 예외가 throw 됩니다 `OpenMPWithMultipleAppdomainsException` .

이러한 예외는 다음과 같은 경우에 발생할 수도 있습니다.

- 응용 프로그램이 **/clr** 을 사용 하 여 컴파일되고 **/openmp** 는 기본이 아닌 응용 프로그램 도메인에 로드 되는 경우,이 프로세스에는 **/openmp** 를 사용 하 여 컴파일된 앱이 포함 됩니다.

- 대상 어셈블리를 기본이 아닌 응용 프로그램 도메인으로 로드 하는 [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)와 같은 **/clr** 앱을 유틸리티에 전달 하는 경우

공용 언어 런타임의 코드 액세스 보안은 OpenMP 지역에서 작동 하지 않습니다. 병렬 영역 외부에 CLR 코드 액세스 보안 특성을 적용 하는 경우 병렬 지역에는 적용 되지 않습니다.

Microsoft는 부분적으로 신뢰할 수 있는 호출자를 허용 하는 **/openmp** apps를 작성 하지 않는 것이 좋습니다. <xref:System.Security.AllowPartiallyTrustedCallersAttribute>또는 CLR 코드 액세스 보안 특성을 사용 하지 마세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **언어** 속성 페이지를 확장 합니다.

1. **OpenMP 지원** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 스레드 풀 시작이 시작 된 후 스레드 풀을 사용 하는 경우의 몇 가지 영향을 보여 줍니다. X64, 단일 코어 이중 프로세서 라고 가정 하면 스레드 풀을 시작 하는 데 약 16 밀리초가 소요 됩니다. 그 후에는 스레드 풀에 대 한 추가 비용이 거의 없습니다.

**/Openmp** 를 사용 하 여 컴파일하는 경우에는 스레드 풀을 시작할 수 없기 때문에 test2에 대 한 두 번째 호출에서 **/hs** 를 사용 하 여 컴파일하는 경우 보다 더 이상 실행 되지 않습니다. 백만 번의 반복에서 **/openmp** 버전은 test2에 대 한 두 번째 호출에 대 한 **/hmpmps** 버전 보다 빠릅니다. 25 번의 반복에서 **/openmp-** 및 **/openmp** 버전은 모두 클록 세분성 보다 낮습니다.

응용 프로그램에 루프가 하나 뿐 이며 15 밀리초 미만으로 실행 되는 경우 (컴퓨터의 대략적인 오버 헤드로 조정 됨) **/openmp** 가 적절 하지 않을 수 있습니다. 더 높은 경우 **/openmp** 를 사용 하는 것이 좋습니다.

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md) \
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md) \
[MSVC의 OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)
