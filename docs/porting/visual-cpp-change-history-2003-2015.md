---
title: Microsoft C/c + + 변경 기록 2003-2015
description: Visual Studio 2003에서 visual studio 2015를 통해 Microsoft C/c + +의 주요 변경 사항을 모두 확인 하세요.
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: c444a44a7e32491783502486f1acbda464378e9c
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334109"
---
# <a name="microsoft-cc-change-history-2003---2015"></a>Microsoft C/c + + 변경 기록 2003-2015

이 문서에서는 Visual C++ 2015에서 Visual Studio 2003까지 모든 주요 변경 내용을 설명하며, 이 문서에서 사용된 “새 동작" 또는 “현재"라는 용어는 Visual Studio 2015 이상 버전을 가리킵니다. "이전 동작" 및 "이전"은 Visual Studio 2013 이하 릴리스를 나타냅니다.

최신 버전의 Visual Studio에 대 한 자세한 내용은 visual studio의 [c + +에 대 한 새로운](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) 기능 및 [visual studio의 c + + 규칙 향상](../overview/cpp-conformance-improvements.md)을 참조 하세요.

> [!NOTE]
> Visual Studio 2015 ~ Visual Studio 2017에서 새로운 이진 변경 내용이 없습니다.

새 버전의 Visual Studio로 업그레이드하는 경우 이전에 컴파일하고 올바르게 실행된 코드에서 컴파일 및/또는 런타임 오류가 발생할 수 있습니다. 그러한 문제가 발생하는 새 버전의 변경 사항은 *주요 변경 사항* 이라고 하고 일반적으로 C++ 언어 표준, 함수 서명 또는 메모리의 레이아웃 개체 수정에 필요합니다.

검색하고 진단하기 어려운 런타임 오류를 방지하려면 다양한 버전의 컴파일러를 사용하여 컴파일된 바이너리에 정적으로 연결하지 않는 것이 좋습니다. 또한 EXE 또는 DLL 프로젝트를 업그레이드하는 경우 연결되는 라이브러리를 업그레이드해야 합니다. 다양한 버전의 컴파일러를 사용하여 컴파일된 DLL을 비롯한 바이너리 간에 CRT(C 런타임) 또는 C++ 표준 라이브러리(C++ 표준 라이브러리) 형식을 전달하지 마세요. 자세한 내용은 [DLL 경계를 넘어 CRT 개체를 전달할 때 발생할 수 있는 오류](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)를 참조하세요.

또한 COM 인터페이스 또는 POD 개체가 아닌 개체에서 특정 레이아웃을 사용하는 코드를 작성하지 마세요. 그러한 코드를 작성하는 경우 업그레이드한 후 작동하는지 확인해야 합니다. 자세한 내용은 [ABI 경계의 이식성](../cpp/portability-at-abi-boundaries-modern-cpp.md)을 참조하세요.

또한 컴파일러 규칙 개선 작업이 진행 중이므로 컴파일러에서 기존 소스 코드를 인식하는 방식이 변경될 수 있습니다. 예를 들어 빌드 중에 새로운 오류 또는 다른 오류가 발생하거나, 이전에 빌드되어 올바르게 실행되는 것처럼 보이는 코드가 다르게 동작할 수도 있습니다. 이러한 개선 사항이 이 문서에 설명된 것과 같이 주요 변경 내용은 아니지만, 다음과 같은 문제를 해결하기 위해 소스 코드를 변경해야 할 수도 있습니다.

- [CRT(C 런타임) 라이브러리 주요 변경 내용](#BK_CRT)

- [표준 C++ 및 C++ 표준 라이브러리 주요 변경 내용](#BK_STL)

- [MFC 및 ATL 주요 변경 내용](#BK_MFC)

- [동시성 런타임 주요 변경 내용](#BK_ConcRT)

## <a name="visual-studio-2015-conformance-changes"></a><a name="VC_2015"></a> Visual Studio 2015 규칙 변경 내용

### <a name="c-runtime-library-crt"></a><a name="BK_CRT"></a> CRT (C 런타임 라이브러리)

#### <a name="general-changes"></a>일반 변경 내용

- **리팩터링된 이진 파일**

   CRT 라이브러리는 범용 CRT(ucrtbase)(대부분 표준 기능이 포함됨) 및 VC 런타임 라이브러리(vcruntime)라는 두 개의 이진 파일로 리팩터링되었습니다. vcruntime 라이브러리에는 예외 처리 및 내장 함수와 같은 컴파일러 관련 기능이 포함되어 있습니다. 링커가 자동으로 새로운 기본 라이브러리를 사용하므로 기본 프로젝트 설정을 사용하면 이 변경 내용이 영향을 주지 않습니다. 프로젝트의 **링커** 속성 **모든 기본 라이브러리 무시** 를 **예** 로 설정했거나 명령줄에서 `/NODEFAULTLIB` 링커 옵션을 사용 중이면 새 리팩터링된 라이브러리를 포함하도록 **추가 종속성** 속성에서 라이브러리 목록을 업데이트해야 합니다. 이전 CRT 라이브러리(libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib)를 해당하는 리팩터링된 라이브러리로 바꿉니다. 두 리팩터링된 라이브러리에는 각각 정적(.lib) 및 동적(.dll) 버전과 릴리스(접미사 없음) 및 디버그("d" 접미사 사용) 버전이 있습니다. 동적 버전에는 연결할 가져오기 라이브러리가 포함됩니다. 리팩터링된 두 라이브러리는 유니버설 CRT(구체적으로 ucrtbase.dll 또는 ucrtbase.lib, ucrtbased.dll 또는 ucrtbased.lib)와 VC 런타임 라이브러리(libvcruntime.lib, vcruntime *version*.dll, libvcruntimed.lib 및 vcruntimed *version*.dll)입니다. Visual Studio 2015 및 Visual Studio 2017의 *버전* 은 모두 140입니다. [CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)을 참조하세요.

#### \<locale.h>

- **localeconv**

   locale.h에 선언된 [localeconv](../c-runtime-library/reference/localeconv.md) 함수는 현재 [per-thread locale](../parallel/multithreading-and-locales.md)이 사용될 때 제대로 작동합니다. 이전 버전의 라이브러리에서 이 함수는 스레드 로컬이 아니라 글로벌 로캘에 대해 `lconv` 데이터를 반환합니다.

   스레드 로컬을 사용하는 경우 `localeconv`를 사용하는지 확인해야 합니다. 코드에서 `lconv` 데이터가 글로벌 로캘에 대해 반환되었다고 가정하는 경우 이를 해결해야 합니다.

#### \<math.h>

- **수식 라이브러리 함수의 C++ 오버로드**

   이전 버전에서는 \<math.h> 수학 라이브러리 함수에 대 한 일부 c + + 오버 로드를 정의 했습니다. 나머지 오버 로드는 \<cmath> 헤더에 있습니다. 포함 된 코드에만 \<math.h> 함수 오버 로드 확인에 문제가 있을 수 있습니다. 이제 c + + 오버 로드는에서 제거 되었고 \<math.h> 에서만 찾을 수 있습니다 \<cmath> .

   오류를 해결 하려면를 포함 하 여 \<cmath> 에서 제거 된 함수의 선언을 가져옵니다 \<math.h> . 다음과 같은 함수는 이동되었습니다.

  - `double abs(double)` 및 `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - **`float`** 및 **`long double`** 버전의 부동 소수점 함수,,,, `acos` `acosh` `asin` `asinh` `atan` , `atanh` `atan2` `cbrt` `ceil` `copysign` `cos` `cosh` `erf` `erfc` `exp` `exp2` `expm1` `fabs` `fdim` `floor` `fma` `fmax` `fmin` `fmod` `frexp` `hypot` `ilogb` `ldexp` `lgamma` `llrint` `llround` `log` `log10` `log1p` `log2` `lrint` `lround` `modf` `nearbyint` `nextafter` `nexttoward` `remainder` `remquo` `rint` `round` `scalbln` `scalbn` `sin` `sinh` `sqrt` `tan` `tanh` `tgamma` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `trunc`

  `abs`머리글만 포함 하는 부동 소수점 형식과 함께를 사용 하는 코드가 있는 경우 \<math.h> 부동 소수점 버전을 더 이상 사용할 수 없습니다. 이제 호출은 오류가 생성되는 부동 소수점 인수가 포함되더라도 `abs(int)`로 확인됩니다.

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  이 경고에 대 한 해결 방법은의 호출을 `abs` `abs` double 인수 또는 float 인수와 같은의 부동 소수점 버전으로 바꾸거나 `fabs` `fabsf` 헤더를 포함 하 \<cmath> 고 계속 사용 `abs` 하는 것입니다.

- **부동 소수점 적합성**

   NaN 및 무한대와 같은 특수한 경우 입력과 관련된 IEEE-754 및 C11 Annex F 사양에 대한 적합성을 향상하고자 수식 라이브러리가 많이 변경되었습니다. 예를 들어 이전 라이브러리 버전에서 종종 오류로 처리되었던 자동 NaN 입력은 더 이상 오류로 처리되지 않습니다. [IEEE 754 표준](https://standards.ieee.org/standard/754-2008.html) (영문) 및 [C11 표준](https://www.iso.org/standard/57853.html)(영문)의 부록 F를 참조하세요.

   이 변경 내용 때문에 컴파일 시간 오류가 발생하지 않지만, 프로그램이 표준에 따라 다르고 더 올바르게 동작할 수 있습니다.

- **FLT_ROUNDS**

   Visual Studio 2013에서 FLT_ROUNDS 매크로는 상수 식으로 확장되었고, 이는 반올림 모드가 런타임에 fesetround 호출 등을 통해 구성 가능하기 때문에 올바르지 않았습니다. 현재 FLT_ROUNDS 매크로는 동적이고 현재 반올림 모드를 올바르게 반영합니다.

#### <a name="new-and-newh"></a>\<new> 및 \<new.h>

- **new 및 delete**

   이전 라이브러리 버전에서는 구현 시 정의된 연산자 new 및 delete 함수를 런타임 라이브러리 DLL(예: msvcr120.dll)에서 내보냈습니다. 현재 이들 연산자 함수는 런타임 라이브러리 DLL을 사용할 때라도 항상 정적으로 이진 파일에 연결됩니다.

   이는 네이티브 또는 혼합 코드(`/clr`)에 대한 주요 변경 내용이 아니지만 [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md)로 컴파일된 코드의 경우 이 변경 내용으로 인해 코드가 컴파일되지 않을 수 있습니다. 코드를 `/clr:pure`로 컴파일할 경우 이 변경으로 인한 빌드 오류를 해결하려면 `#include <new>` 또는 `#include <new.h>`를 추가해야 합니다. `/clr:pure` 옵션은 Visual Studio 2015에서 사용되지 않으며 Visual Studio 2017에서 지원되지 않습니다. “순수”해야하는 코드는 C#으로 포팅되어야 합니다.

#### \<process.h>

- **_beginthread 및 _beginthreadex**

   [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 및 [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 함수는 현재 스레드 기간에 대한 스레드 프로시저가 정의된 모듈에 대한 참조를 포함합니다. 이를 통해 스레드 실행이 완료될 때까지 모듈이 언로드되지 않도록 보장할 수 있습니다.

#### \<stdarg.h>

- **va_start 및 참조 형식**

   이제 C++ 코드를 컴파일할 때 [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)는 컴파일 시간에 전달된 인수가 참조 형식이 아닌지 유효성을 검사합니다. 참조 형식 인수는 C++ 표준에 따라 금지됩니다.

#### <a name="stdioh-and-conioh"></a><a name="stdio_and_conio"></a>\<stdio.h>및\<conio.h>

- **printf 및 scanf 함수 패밀리는 현재 인라인으로 정의됩니다.**

   모든 `printf` 및 `scanf` 함수의 정의가 \<stdio.h> , \<conio.h> 및 기타 CRT 헤더로 인라인으로 이동 되었습니다. 이 주요 변경 내용으로 인해 해당하는 CRT 헤더를 포함하지 않고 이러한 함수를 로컬로 선언한 프로그램에 대한 링커 오류(LNK2019, 확인되지 않은 외부 기호)가 발생합니다. 가능하면 코드를 업데이트하여 인라인 함수 및 CRT 헤더를 포함(즉, `#include <stdio.h>` 추가)해야 합니다. 하지만 이러한 헤더 파일을 포함하도록 코드를 수정하지 않으려면 대체 솔루션으로 링커 입력 legacy_stdio_definitions.lib에 라이브러리를 추가합니다.

   이 라이브러리를 IDE의 링커 입력에 추가하려면 프로젝트 노드의 상황에 맞는 메뉴를 열고, **속성** 을 선택한 다음, **프로젝트 속성** 대화 상자에서 **링커** 를 선택하고, **링커 입력** 을 편집하여 `legacy_stdio_definitions.lib`를 세미콜론으로 구분된 목록에 추가합니다.

   프로젝트가 Visual Studio 2015 이전의 릴리스로 컴파일된 고정 라이브러리와 연결되면 링커에서 확인되지 않은 외부 기호가 보고될 수 있습니다. 이러한 오류는 `_iob` `_iob_func` imp 형식의 특정 함수에 대 한, 또는 관련 된 가져오기에 \<stdio.h> _imp_ 대 한 내부 정의를 참조할 수 있습니다 \* . 프로젝트를 업그레이드할 때 C++ 컴파일러 및 라이브러리의 최신 버전으로 모든 고정 라이브러리를 다시 컴파일하는 것이 좋습니다. 라이브러리가 소스를 사용할 수 없는 타사 라이브러리이면 타사로부터 업데이트된 라이브러리를 요청하거나 이전 버전의 컴파일러 및 라이브러리를 사용하여 컴파일하는 별도의 DLL로 해당 라이브러리 사용을 캡슐화해야 합니다.

    > [!WARNING]
    > Windows SDK 8.1 이하와 연결되어 있으면 이러한 확인되지 않은 외부 기호 오류가 발생할 수 있습니다. 이 경우 앞에 설명된 대로 링커 입력에 legacy_stdio_definitions.lib를 추가하여 오류를 해결해야 합니다.

   확인되지 않은 기호 오류를 해결하려면 [dumpbin.exe](../build/reference/dumpbin-reference.md)를 사용하여 이진 파일에 정의된 기호를 검사해 볼 수 있습니다. 다음 명령줄을 실행하여 라이브러리에 정의된 기호를 확인해 보세요.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets 및 _getws**

   [gets](../c-runtime-library/gets-getws.md) 및 [_getws](../c-runtime-library/gets-getws.md) 함수가 제거되었습니다. get 함수는 안전하게 사용할 수 없으므로 C11의 C 표준 라이브러리에서 제거되었습니다. _getws 함수는 gets와 동일한 Microsoft 확장이지만 전각 문자열에 해당했습니다. 이들 함수 대신 [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)및 [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)를 사용하는 것이 좋습니다.

- **_cgets 및 _cgetws**

   [_cgets](../c-runtime-library/cgets-cgetws.md) 및 [_cgetws](../c-runtime-library/cgets-cgetws.md) 함수가 제거되었습니다. 이들 함수 대신 [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) 및 [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)를 사용하는 것이 좋습니다.

- **무한대 및 NaN 서식 지정**

   이전 버전에서 무한대 및 NaN은 일련의 MSVC 관련 센티널 문자열을 사용하여 서식이 지정됩니다.

  - 무한대: 1.#INF

  - 자동 NaN: 1.#QNAN

  - 신호 NaN: 1.#SNAN

  - 무한 NaN: 1.#IND

  이러한 형식은 앞에 기호가 추가될 수 있고, 필드 너비 및 전체 자릿수에 따라 서식이 약간 다르게 지정되었을 수 있습니다. 경우에 따라 비정상적인 효과로 인해 #INF가 2자리 전체 자릿수로 "반올림"되기 때문에 `printf("%.2f\n", INFINITY)`가 1.#J를 인쇄합니다. C99는 무한대 및 NaN 서식을 지정하는 방법에 대한 새로운 요구 사항을 새로 추가했습니다. 현재 MSVC 구현은 이러한 요구 사항을 준수합니다. 새 문자열은 다음과 같습니다.

  - 무한대: inf

  - 자동 NaN: nan

  - 신호 NaN: nan(snan)

  - 무한 NaN: nan(ind)

  이들 문자열 앞에 부호가 추가될 수 있습니다. 대문자 서식 지정자가 사용되면(%f 대신 %F) 문자열은 요구된 대로 대문자로 인쇄됩니다(`inf` 대신 `INF`).

  [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 함수는 이들 새 문자열을 구문 분석하도록 수정되었습니다. 따라서 이제 이러한 문자열은 `printf` 및 `scanf`를 통해 왕복됩니다.

- **부동 소수점 서식 지정 및 구문 분석**

   정확성을 향상하고자 새로운 부동 소수점 서식 지정 및 구문 분석 알고리즘이 새로 추가되었습니다. 이 변경은 함수의 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 및 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 패밀리와 [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 등의 함수에 영향을 미칩니다.

   이전 서식 지정 알고리즘에서는 제한된 자릿수만 생성되고 나머지 소수 자릿수는 0으로 채워집니다. 일반적으로 다시 원래 부동 소수점 값으로 왕복할 문자열을 생성할 수 있지만 정확한 값이나 가장 가까운 10진수 표현을 사용하려는 경우에는 적절하지 않습니다. 새 서식 지정 알고리즘에서는 값을 표현하는 데 필요한 만큼 자릿수가 생성되거나 지정된 정밀도가 채워집니다. 향상의 예로 2의 거듭제곱을 인쇄할 때 결과를 살펴보세요.

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   이전 출력:

    ```Output
    1208925819614629200000000
    ```

   새 출력:

    ```Output
    1208925819614629174706176
    ```

   이전 구문 분석 알고리즘에서는 입력 문자열에서 최대 17자리만 고려되고 나머지 자릿수는 무시됩니다. 이러한 접근 방법은 문자열로 표현되는 값의 가까운 근사치를 생성하기에 충분하고, 결과는 대개 올바르게 반올림됨 결과에 매우 가깝습니다. 새 구현에서는 모든 제공된 자릿수를 고려하고 모든 입력에 대한 올바르게 반올림된 결과를 생성합니다(최대 768자리 길이). 또한 현재 이들 함수는 반올림 모드를 따릅니다(fesetround를 통해 제어 가능).  이러한 함수가 다른 결과를 출력할 수 있으므로 이는 잠재적으로 중요한 동작 변경입니다. 새 결과는 항상 이전 결과보다 더 정확합니다.

- **16진수 및 무한대/NaN 부동 소수점 구문 분석**

   부동 소수점 구문 분석 알고리즘은 이제 위에서 설명한 대로 16진수 부동 소수점 문자열(예: %a 및 %A printf 서식 지정자에서 생성된 항목) 및 `printf` 함수에서 생성된 모든 무한대 및 NaN 문자열을 구문 분석합니다.

- **%A 및 %a 영(0) 채우기**

   %a 및 %A 서식 지정자는 부동 소수점 수의 서식을 16진수 가수 및 이진 지수로 지정합니다. 이전 버전에서 `printf` 함수는 문자열에 0을 잘못 채웠습니다. 예를 들어 `printf("%07.0a\n", 1.0)`은 0x01p+0을 인쇄해야 하는데 00x1p+0을 인쇄합니다. 이러한 결함은 수정되었습니다.

- **%A 및 %a 정밀도**

   이전 라이브러리 버전에서 %A 및 %a 서식 지정자의 기본 정밀도는 6이었습니다. 현재 기본 정밀도는 C 표준에 따라 13입니다.

   이는 %A 또는 %a와 함께 서식 문자열을 사용하는 함수 출력의 런타임 동작 변경입니다. 이전 동작에서 %A 지정자를 사용하는 출력은 "1.1A2B3Cp+111"일 수 있습니다. 현재 같은 값의 출력은 "1.1A2B3C4D5E6F7p+111"입니다. 이전 동작을 가져오려면 정밀도(예: %.6A)를 지정하면 됩니다. [전체 자릿수 사양](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision)을 참조하세요.

- **%F 지정자**

   현재 %F 서식/변환 지정자가 지원됩니다. 무한대 및 NaN이 대문자를 사용하여 서식이 지정된다는 점을 제외하고 %f 서식 지정자와 일치하는 기능입니다.

   이전 버전에서는 F 및 N을 길이 수정자로 구문 분석하는 데 구현이 사용되었습니다. 이 동작은 분할된 주소 공간의 보존 기간부터 계속 존재했습니다. 이들 길이 수정자는 %Fp 또는 %Ns에서와 같이 각각 먼 포인터와 가까운 포인터를 나타내는 데 사용되었습니다. 이 동작이 제거되었습니다. 이제 %F가 나타나면 %F 서식 지정자로 처리되고, %N이 나타나면 잘못된 매개 변수로 처리됩니다.

- **지수 서식 지정**

   %e 및 %E 서식 지정자는 부동 소수점 수의 서식을 10진수 가수 및 지수로 지정합니다. 경우에 따라 %g 및 %G 서식 지정자는 숫자 서식을 이 형식으로 지정합니다. 이전 버전에서 CRT는 항상 3자리 지수가 포함된 문자열을 생성합니다. 예를 들어 `printf("%e\n", 1.0)`는 1.000000e+000을 인쇄하지만 잘못되었습니다. C에서는 지수가 1자리 또는 2자리로만 표현 가능할 경우 2자리만 인쇄되어야 합니다.

   Visual Studio 2005에서 전역 규칙 스위치 [_set_output_format](../c-runtime-library/set-output-format.md)이 추가되었습니다. 프로그램은 _TWO_DIGIT_EXPONENT 인수와 함께 이 함수를 호출하여 규칙 지수 인쇄가 가능하도록 설정합니다. 기본 동작이 표준 준수 지수 인쇄 모드로 변경되었습니다.

- **서식 문자열 유효성 검사**

   이전 버전에서 `printf` 및 `scanf` 함수는 경우에 따라 비정상적인 효과를 가진 잘못된 여러 서식 문자열을 자동으로 허용했습니다. 예를 들어 %hlhlhld가 %d로 처리됩니다. 현재 모든 잘못된 서식 문자열은 잘못된 매개 변수로 처리됩니다.

- **fopen 모드 문자열 유효성 검사**

   이전 버전에서 함수의 `fopen` 계열은 몇몇 잘못된 모드 문자열(예: `r+b+`)을 자동으로 허용했습니다. 현재는 잘못된 모드 문자열을 인식하여 잘못된 매개 변수로 처리됩니다.

- **_O_U8TEXT 모드**

   현재 [_setmode](../c-runtime-library/reference/setmode.md) 함수는 _O_U8TEXT 모드에서 열린 스트림의 모드를 올바르게 보고합니다. 이전 라이브러리 버전에서는 해당 스트림을 _O_WTEXT에서 열린 것으로 보고했습니다.

   이는 코드가 인코딩이 UTF-8인 스트림에 대한 _O_WTEXT 모드를 해석할 경우 주요 변경 내용입니다. 애플리케이션이 UTF_8을 지원하지 않으면 점점 더 일반화되는 이 인코딩에 대한 지원을 추가하는 것이 좋습니다.

- **snprintf 및 vsnprintf**

   현재 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 및 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 함수가 구현됩니다. 이전 코드에서는 이러한 함수의 매크로 버전이 CRT 라이브러리에서 구현되지 않았기 때문에 해당 매크로 버전의 정의를 제공했지만 새 버전에서는 더 이상 필요하지 않습니다. [Snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 또는 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 가를 포함 하기 전에 매크로로 정의 된 경우 \<stdio.h> 이제 컴파일이 실패 하 고 매크로가 정의 된 위치를 나타내는 오류가 표시 됩니다.

   일반적으로 이 문제를 해결하려면 사용자 코드에서 `snprintf` 또는 `vsnprintf`라는 선언을 삭제합니다.

- **tmpnam이 사용 가능한 파일 이름을 생성함**

   이전 버전에서 `tmpnam` 및 `tmpnam_s` 함수는 드라이브 루트(예: \sd3c.)에 파일 이름을 생성했습니다. 현재 이들 함수는 임시 디렉터리에 사용 가능한 파일 이름 경로를 생성합니다.

- **FILE 캡슐화**

   이전 버전에서는 전체 파일 형식이에서 공개적으로 정의 되었으므로 \<stdio.h> 사용자 코드를 파일에 연결 하 고 해당 내부를 수정할 수 있었습니다. 해당 라이브러리가 구현 세부 정보를 숨기도록 변경되었습니다. 이 변경의 일환으로에 정의 된 파일 \<stdio.h> 은 이제 불투명 형식이 며 CRT 자체 외부에서 해당 멤버에 액세스할 수 없습니다.

- **_outp 및 _inp**

   [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md) 및 [_inpd](../c-runtime-library/inp-inpw-inpd.md) 함수가 제거되었습니다.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h>, \<sys/stat.h>

- **strtof 및 wcstof**

   `strtof` 및 `wcstof` 함수는 값이 float로 표현되지 않으면 `errno`를 ERANGE로 설정하지 못했습니다. 이 오류는 이러한 두 개의 함수에만 발생했고, `strtod`, `wcstod`, `strtold` 및 `wcstold` 함수는 영향을 받지 않았습니다. 중요한 런타임 변경 내용으로 이 문제를 해결했습니다.

- **맞춤 할당 함수**

   이전 버전에서 맞춤 할당 함수(`_aligned_malloc`, `_aligned_offset_malloc` 등)는 정렬이 0인 블록에 대한 요청을 자동으로 수락했습니다. 요청된 맞춤은 0이 아닌 2의 거듭제곱이어야 합니다. 요청된 맞춤 0은 이제 잘못된 매개 변수로 처리됩니다. 중요한 런타임 변경 내용으로 이 문제를 해결했습니다.

- **힙 함수**

   `_heapadd`, `_heapset` 및 `_heapused` 함수가 제거되었습니다. Windows 힙을 사용하도록 CRT가 업데이트된 후에는 이들 함수가 작동하지 않았습니다.

- **smallheap**

   `smallheap` 링크 옵션이 제거되었습니다. [링크 옵션](../c-runtime-library/link-options.md)을 참조하세요.

#### \<string.h>

- **wcstok**

   `wcstok` 함수의 시그니처가 C Standard에 필요한 시그니처와 일치하도록 변경되었습니다. 이전 라이브러리 버전에서 이 함수의 서명은 다음과 같았습니다.

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   내부 스레드 단위 컨텍스트를 사용하여 `strtok`의 경우와 마찬가지로 호출 전체에서 상태를 추적했습니다. 이제 이 함수는 `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` 서명을 포함하며, 호출자가 컨텍스트를 세 번째 인수로 함수에 전달해야 합니다.

   쉽게 이식하도록 이전 서명과 함께 새 `_wcstok` 함수가 추가되었습니다. C++ 코드를 컴파일할 때 이전 서명이 포함된 `wcstok`의 인라인 오버로드도 있습니다. 이 오버로드는 deprecated로 선언되었습니다. C 코드에서 _CRT_NON_CONFORMING_WCSTOK를 정의하여 `_wcstok`를 `wcstok` 위치에서 사용하도록 할 수 있습니다.

#### \<time.h>

- **클럭을**

   이전 버전에서 [clock](../c-runtime-library/reference/clock.md) 함수는 Windows API [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime)(영문)을 사용하여 구현되었습니다. 이 구현을 통해 clock 함수는 시스템 시간에 따라 달라지므로 단조일 필요가 없었습니다. clock 함수는 [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) (영문)를 기준으로 다시 구현되었으며 현재는 단조입니다.

- **fstat 및 _utime**

   이전 버전에서 [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 및 [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 함수는 일광 절약 시간제를 잘못 처리합니다. Visual Studio 2013 이전에는 이들 함수가 모두 표준시 시간을 일광 절약 시간인 것처럼 잘못 조정했습니다.

   Visual Studio 2013에서 이 문제는 **_stat** 함수 계열에서 수정되었지만 **fstat** 및 **_utime** 함수 계열에서는 비슷한 문제가 수정되지 않았습니다. 이러한 부분 수정으로 인해 함수가 일치하지 않아서 문제가 발생했습니다. 이제 **fstat** 및 **_utime** 함수 계열이 수정되었으므로 현재 이들 함수는 모두 일광 절약 시간제를 올바르고 일관되게 처리합니다.

- **asctime**

   이전 버전에서 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 함수는 한 자리 일 단위의 앞에 0을 추가했습니다(예: `Fri Jun 06 08:00:00 2014`). 사양에 따라 해당 일 단위의 앞에는 공백이 추가되어야 합니다(예: `Fri Jun  6 08:00:00 2014`). 이 문제가 해결되었습니다.

- **strftime 및 wcsftime**

   `strftime` 및 `wcsftime` 함수는 이제 %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u 및 %V 서식 지정자를 지원합니다. 또한 E 및 O 수정자는 구문 분석되지만 무시됩니다.

   %c 서식 지정자는 현재 로캘에 대한 "적절한 날짜 및 시간 표현"을 생성하도록 지정됩니다. C 로캘에서 이 표현은 `%a %b %e %T %Y`와 같아야 합니다. 동일한 양식이 `asctime`에서도 생성됩니다. 이전 버전에서 %c 서식 지정자는 `MM/DD/YY HH:MM:SS` 표현을 사용하여 시간의 서식을 잘못 지정했습니다. 이 문제가 해결되었습니다.

- **timespec 및 TIME_UTC**

   \<time.h>이제 헤더는 `timespec` `timespec_get` C11 표준에서 형식과 함수를 정의 합니다. 또한 `timespec_get` 함수와 함께 사용할 TIME_UTC 매크로가 이제 정의됩니다. 이 업데이트는 이러한 식별자에서 충돌하는 정의가 있는 코드의 주요 변경 내용입니다.

- **CLOCKS_PER_SEC**

   현재 CLOCKS_PER_SEC 매크로는 C 언어에 필요한 형식 `clock_t`의 정수로 확장됩니다.

#### <a name="c-standard-library"></a><a name="BK_STL"></a> C + + 표준 라이브러리

새로운 최적화 및 디버깅 검사를 사용하려면 C++ 표준 라이브러리의 Visual Studio 구현은 버전별로 바이너리 호환성을 의도적으로 변경합니다. 따라서 C++ 표준 라이브러리가 사용되면 서로 다른 버전을 사용하여 컴파일된 개체 파일 및 정적 라이브러리를 하나의 바이너리(EXE 또는 DLL)에 혼합할 수 없고 C++ 표준 라이브러리 개체는 서로 다른 버전을 사용하여 컴파일된 바이너리 사이에서 전달할 수 없습니다. 그렇게 혼합하면 _MSC_VER 불일치에 대한 링커 오류를 내보냅니다. _MSC_VER은 컴파일러의 주 버전을 포함 하는 매크로입니다. 예를 들어 Visual Studio 2013의 경우 1800입니다. 이 검사에서는 DLL 혼합을 감지할 수 없으며 Visual Studio 2008이 하를 포함 하는 혼합을 감지할 수 없습니다.

- **C++ 표준 라이브러리 포함 파일**

   C++ 표준 라이브러리 헤더의 포함 구조가 일부 변경되었습니다. C++ 표준 라이브러리 헤더는 서로 지정되지 않는 방식으로 포함할 수 있습니다. 일반적으로 C++ 표준에 따라 필요한 모든 헤더를 신중하게 포함하고 다른 C++ 표준 라이브러리 헤더를 포함하는 C++ 표준 라이브러리 헤더를 사용하지 않도록 코드를 작성해야 합니다. 이렇게 하면 버전 및 플랫폼 간에 코드를 이식할 수 있습니다. Visual Studio 2015에서 두 개 이상의 헤더 변경 내용이 사용자 코드에 영향을 줍니다. 첫 번째에는가 \<string> 더 이상 포함 되지 않습니다 \<iterator> . 두 번째는 \<tuple> 이제를 `std::array` 포함 하지 않고 코드를 나눌 수 있는 모든를 포함 하지 않고를 선언 합니다 \<array> . 코드에는 "array" 라는 변수가 있고 using 지시문 "using namespace std;"가 있으며를 포함 하는 c + + 표준 라이브러리 헤더 (예:)를 포함 하 여 \<functional> \<tuple> 이제가 선언 `std::array` 됩니다.

- **steady_clock**

   \<chrono>조성에 및 단 조성에에 대 한 c + + 표준 요구 사항을 충족 하기 위해 [steady_clock](../standard-library/steady-clock-struct.md) 의 구현이 변경 되었습니다. 이제 `steady_clock`은 [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter)를 기반으로 하며 `high_resolution_clock`은 `steady_clock`에 대한 typedef입니다. 따라서 이제 Visual Studio에서 `steady_clock::time_point`는 `chrono::time_point<steady_clock>`에 대한 typedef이지만, 다른 구현에 이를 반드시 적용할 필요는 없습니다.

- **allocators 및 const**

   현재 양쪽에서 const 인수를 수락하려면 allocator 같음/같지 않음 비교가 필요합니다. allocator가 이러한 연산자를 다음과 같이 정의하면,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   이러한 연산자를 업데이트하여 const 멤버로 선언해야 합니다.

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **const 요소**

   C + + 표준에는 항상 vector 또는 set 같은 const 요소의 컨테이너를 사용할 수 \<const T> \<const T> 없습니다. Visual Studio 2013 이하에서는 해당 컨테이너를 허용했습니다. 현재 버전에서는 해당 컨테이너가 컴파일되지 않습니다.

- **std::allocator::deallocate**

   Visual Studio 2013 및 이전 버전에서 `std::allocator::deallocate(p, n)`는 *n* 에 대해 전달된 인수를 무시했습니다.  C++ 표준에서 *n* 은 항상 *p* 를 반환한 `allocate` 호출에 첫 번째 인수로 전달된 값과 같아야 합니다. 그러나 현재 버전에서는 *n* 값이 검사됩니다. 표준에 필요한 값과 다른 *n* 에 대한 인수를 전달하는 코드는 런타임에 충돌을 가져올 수 있습니다.

- **hash_map 및 hash_set**

   비표준 헤더 파일 \<hash_map> 및 \<hash_set> 은 Visual Studio 2015에서 더 이상 사용 되지 않으며 이후 릴리스에서 제거 될 예정입니다. 대신 \<unordered_map> 및 \<unordered_set>을 사용하세요.

- **비교 연산자 및 operator()**

   이제 결합형 컨테이너 ( \<map> 패밀리)가 const 호출 가능 함수 호출 연산자를 비교 연산자 해야 합니다. 현재 비교 연산자 클래스 선언에서 다음 코드는 컴파일되지 않습니다.

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   이 오류를 해결하려면 함수 선언을 다음으로 변경합니다.

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **형식 특성**

   C++ 초안 표준의 이전 버전에서 형식 특성의 이전 이름이 제거되었습니다. 이 이름은 C++11에서 변경되었고 Visual Studio 2015에서 C++11 값으로 업데이트되었습니다. 다음 표에서는 이전 이름과 새 이름을 보여 줍니다.

   |이전 이름|새 이름|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **launch::any 및 launch::sync 정책**

   비표준 `launch::any` 및 `launch::sync` 정책이 제거되었습니다. 대신 `launch::any`의 경우 `launch:async | launch:deferred`를 사용합니다. `launch::sync`의 경우 `launch::deferred`을 사용합니다. [launch 열거형](../standard-library/future-enums.md#launch)을 참조하세요.

#### <a name="mfc-and-atl"></a><a name="BK_MFC"></a> MFC 및 ATL

- **MFC(Microsoft Foundation Class)**

   큰 크기로 인해 더 이상 Visual Studio의 “일반” 설치에 포함되지 않습니다. MFC를 설치하려면 Visual Studio 2015 설치 프로그램에서 **사용자 지정** 설치 옵션을 선택합니다. Visual Studio 2015가 이미 설치된 경우 다시 **Visual Studio** 설정을 실행하여 MFC를 설치할 수 있습니다. **사용자 지정** 설치 옵션을 선택한 다음, **Microsoft Foundation Classes** 를 선택합니다. **제어판** 컨트롤 **프로그램 및 기능** 또는 설치 미디어에서 **Visual Studio** 설치 프로그램을 실행할 수 있습니다.

   Visual C++ 재배포 가능 패키지에는 이 라이브러리가 계속 포함됩니다.

#### <a name="concurrency-runtime"></a><a name="BK_ConcRT"></a> 동시성 런타임

- **concurrency::Context::Yield와 충돌하는 Windows.h의 Yield 매크로**

   이전 동시성 런타임은 Windows.h h에 정의된 Yield 매크로와 `concurrency::Context::Yield` 함수의 충돌을 피하려고 `#undef`를 사용하여 Yield 매크로의 정의를 해제했습니다. 이 `#undef`는 제거되었고 새로운 충돌하지 않는 동등한 API 호출 [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution)이 추가되었습니다. Yield에서 발생하는 충돌을 해결하려면 코드를 업데이트하여 대신 `YieldExecution` 함수를 호출하거나, 다음 예제와 같이 호출 쪽에서 `Yield` 함수 이름을 괄호로 묶습니다.

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015의 컴파일러 규칙 향상

이전 버전에서 코드를 업그레이드하는 경우 Visual Studio 2015의 규칙 향상으로 인한 컴파일러 오류가 발생할 수도 있습니다. 이러한 향상된 기능 때문에 이전 버전의 Visual Studio에서 이진 호환성이 중단되지는 않지만 이전에는 발생하지 않았던 컴파일러 오류가 생성될 수 있습니다. 자세한 내용은 [Visual C++ 2003 ~ 2015의 새로운 기능](../porting/visual-cpp-what-s-new-2003-through-2015.md)을 참조하세요.

Visual Studio 2015에서 컴파일러 규칙 향상 작업이 진행 중이므로 컴파일러에서 기존 소스 코드를 인식하는 방식이 변경될 수 있습니다. 결과적으로, 빌드 중 새로운 오류 또는 다른 오류가 발생하거나, 이전에 빌드되어 올바르게 실행되는 것처럼 보이는 코드가 다르게 동작할 수도 있습니다.

다행스럽게도, 이러한 차이점은 대부분의 소스 코드에 거의 또는 전혀 영향을 주지 않습니다. 이러한 차이점을 해결하기 위해 소스 코드 또는 다른 변경 내용이 필요하면 보통 적은 내용을 간단히 수정하게 됩니다. 이전에는 허용되는 소스 코드였지만 변경해야 할 수 있는 코드 *(이전)* 및 수정 코드 *(이후)* 의 예제가 많이 포함되어 있습니다.

이러한 차이가 소스 코드나 다른 빌드 아티팩트에 영향을 줄 수도 있지만 Visual Studio 버전 업데이트 간의 이진 호환성에는 영향을 주지 않습니다. *주요 변경 내용* 이 보다 심각하면 이진 호환성에 영향을 줄 수 있지만 이러한 종류의 이진 호환성 중단은 주 버전의 Visual Studio 사이에서만 발생합니다(예: Visual Studio 2013과 Visual Studio 2015 사이). Visual Studio 2013과 Visual Studio 2015 사이에 발생한 주요 변경 내용에 대한 자세한 내용은 [Visual Studio 2015 규칙 변경 내용](#VC_2015)을 참조하세요.

- [Visual Studio 2015의 규칙 향상](#VS_RTM)

- [업데이트 1의 규칙 향상](#VS_Update1)

- [업데이트 2의 규칙 향상](#VS_Update2)

- [업데이트 3의 규칙 향상](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a> Visual Studio 2015의 규칙 향상

- /Zc:forScope- 옵션

   `/Zc:forScope-` 컴파일러 옵션은 더 이상 사용되지 않으므로 이후 릴리스에서 제거될 예정입니다.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   이 옵션은 대개 표준에 따라 범위를 벗어나야 하는 지점 뒤에서 루프 변수를 사용하는 비표준 코드를 허용하기 위해 사용되었습니다. `/Za`를 사용하지 않으면 루프 끝에 for 루프 변수를 항상 사용할 수 있으므로 `/Za` 옵션으로 컴파일할 경우에만 필요했습니다. 표준 준수가 중요하지 않으면(예: 코드가 다른 컴파일러에 이식 가능하지 않은 경우) `/Za` 옵션을 해제하거나 **언어 확장 사용 안 함** 속성을 **아니요** 로 설정할 수 있습니다. 이식 가능한 표준 규격 코드를 작성해야 하면 변수의 선언을 루프 외부 지점으로 이동하여 표준을 따르도록 코드를 다시 작성해야 합니다.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` 컴파일러 옵션

   `/Zg` 컴파일러 옵션(함수 프로토타입 생성)은 더 이상 사용할 수 없습니다. 이 컴파일러 옵션은 이미 사용되지 않습니다.

- mstest.exe를 사용하여 명령줄의 C++/CLI에서 단위 테스트를 더 이상 실행할 수 없습니다. 대신에 vstest.console.exe를 사용하세요. [VSTest.Console.exe 명령줄 옵션](/visualstudio/test/vstest-console-options)을 참조하세요.

- **mutable 키워드**

   **`mutable`** 이전에 오류 없이 컴파일된 위치에서는 저장소 클래스 지정 자가 더 이상 허용 되지 않습니다. 현재 컴파일러에서는 오류 C2071(스토리지 클래스가 잘못되었습니다.)을 표시합니다. 표준에 따라 **`mutable`** 지정자는 클래스 데이터 멤버의 이름에만 적용할 수 있으며 const 또는 static으로 선언 된 이름과 참조 멤버에는 적용할 수 없습니다.

   예를 들어, 다음 코드를 고려하세요.

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   이전 버전의 컴파일러에서는 이를 허용했으나 현재 컴파일러에서는 다음 오류를 표시합니다.

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   오류를 해결 하려면 중복 키워드를 제거 합니다 **`mutable`** .

- **char_16_t 및 char32_t**

   **`char16_t`** **`char32_t`** **`typedef`** 이러한 형식은 이제 기본 제공으로 처리 되기 때문에 더 이상에서 또는 별칭으로 사용할 수 없습니다. 일반적으로 사용자와 라이브러리 작성자는 **`char16_t`** 및 **`char32_t`** `uint16_t` 를 각각 및의 별칭으로 정의 하는 것이 일반적 이었습니다 `uint32_t` .

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   코드를 업데이트 하려면 선언을 제거 하 **`typedef`** 고 이러한 이름과 충돌 하는 다른 식별자의 이름을 바꿉니다.

- **비형식 템플릿 매개 변수**

   이제는 비형식 템플릿 매개 변수가 포함된 특정 코드에 명시적 템플릿 인수를 제공하면 형식 호환성 검사가 정확하게 수행됩니다. 예를 들어 다음 코드는 이전 버전의 Visual Studio에서는 오류 없이 컴파일되었습니다.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   템플릿 매개 변수 형식이 템플릿 인수와 일치하지 않기 때문에 현재 컴파일러에서 제대로 오류를 표시합니다. 매개 변수는 const 멤버의 포인터이나 f 함수는 비const입니다.

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   코드에서 이 오류를 해결하려면 사용하는 템플릿 인수 형식이 템플릿 매개 변수의 선언된 형식과 일치해야 합니다.

- **`__declspec(align)`**

   컴파일러가 함수에서 `__declspec(align)` 을 더 이상 허용하지 않습니다. 이 구문은 항상 무시되었지만 이제 컴파일러 오류를 생성합니다.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   이 문제를 수정하려면 함수 선언에서 `__declspec(align)` 을 제거합니다. 아무런 영향이 없으므로 제거해도 아무것도 변경되지 않습니다.

- **예외 처리**

   예외 처리에 대한 몇 가지 변경 내용이 있습니다. 먼저 예외 개체는 복사 가능하거나 이동 가능해야 합니다. 다음 코드는 Visual Studio 2013에서 컴파일되었지만, Visual Studio 2015에서는 컴파일되지 않습니다.

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   문제는 복사 생성자가 비공개라는 점입니다. 따라서 일반적인 예외 처리 과정에서처럼 개체를 복사할 수 없습니다. 복사 생성자가 선언 된 경우에도 마찬가지 **`explicit`** 입니다.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   코드를 업데이트 하려면 예외 개체에 대 한 복사 생성자가이 **`public`** 고로 표시 되지 않아야 **`explicit`** 합니다.

   값으로 예외를 catch하려면 예외 개체가 복사 가능해야 합니다. 다음 코드는 Visual Studio 2013에서 컴파일되었지만, Visual Studio 2015에서는 컴파일되지 않습니다.

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   에 대 한 매개 변수 형식을 참조로 변경 하면이 문제를 해결할 수 있습니다 **`catch`** .

    ```cpp
    catch (D& d)
    {
    }
    ```

- **매크로 뒤의 문자열 리터럴**

   이제 컴파일러는 사용자 정의 리터럴을 지원합니다. 따라서 중간 공백 없이 매크로 뒤의 문자열 리터럴은 오류나 예기치 않은 결과를 생성할 수 있는 사용자 정의 리터럴로 해석됩니다. 예를 들어 이전 컴파일러에서는 다음 코드가 성공적으로 컴파일되었습니다.

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   컴파일러에서는 이 코드를 매크로("there"로 확장됨) 뒤의 문자열 리터럴 "hello"로 해석한 다음, 두 문자열 리터럴이 하나로 연결되었습니다. Visual Studio 2015에서 컴파일러는 이 시퀀스를 사용자 정의 리터럴로 해석하지만 일치하는 사용자 정의 리터럴 `_x`가 정의되지 않았으므로 오류가 발생합니다.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   이 문제를 수정하려면 문자열 리터럴과 매크로 사이에 공백을 추가합니다.

- **인접 문자열 리터럴**

   이전과 비슷하게 문자열 구문 분석의 관련 변경 내용 때문에 공백이 없는 인접 문자열 리터럴(전각 또는 반각 문자 문자열 리터럴)은 이전 Visual C++ 릴리스에서 하나의 연결된 문자열로 해석되었습니다. Visual Studio 2015에서는 현재 두 문자열 사이에 공백을 추가해야 합니다. 예를 들어 다음 코드를 변경해야 합니다.

    ```cpp
    char * str = "abc""def";
    ```

   이 문제를 해결하려면 두 문자열 사이에 공백을 추가하세요.

    ```cpp
    char * str = "abc" "def";
    ```

- **Placement new 및 delete**

   **`delete`** 연산자가 c + + 14 표준을 준수 하도록 변경 되었습니다. 표준 변경에 대한 자세한 내용은 [C++ 크기 지정된 할당 해제](https://isocpp.org/files/papers/n3778.html)(영문)를 참조하세요. 변경 내용에는 **`delete`** 크기 매개 변수를 사용 하는 전역 연산자의 폼이 추가 됩니다. 주요 변경 내용은 이전에 배치 new 연산자와 일치 하는 것과 같은 서명을 사용 하 여 이전에 배치 new 연산자를 사용 하는 경우 컴파일러 **`delete`** 오류 (C2956)를 받게 됩니다 .이는 컴파일러가 적절 한 일치 연산자를 식별 하는 코드의 위치 이기 때문입니다 **placement new** **`delete`** .

   `void operator delete(void *, size_t)` 함수는 C++11의 **placement new** 함수 `void * operator new(size_t, size_t)`에 해당하는 **placement delete** 연산자였습니다. C + + 14 크기 할당 해제를 사용 하면이 delete 함수는 이제 *일반적인 할당 취소 함수* (global **`delete`** 연산자)입니다. 표준에 따르면 placement new를 사용하여 해당하는 delete 함수를 조회하고 usual deallocation 함수를 찾으면 프로그램에 잘못된 형식이 사용됩니다.

   예를 들어 코드에서 **placement new** 및 **placement delete** 를 둘 다 정의한다고 가정합니다.

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   사용자가 정의한 **배치 delete** 연산자와 새 전역 크기 연산자 사이에 함수 서명이 일치 하기 때문에 문제가 발생 합니다 **`delete`** . `size_t` **배치 new** 및 연산자에 대해 이외의 다른 형식을 사용할 수 있는지 여부를 고려 **`delete`** 합니다. 의 형식은 컴파일러에 `size_t` **`typedef`** 따라 다르며, **`typedef`** MSVC의에 대 한입니다 **`unsigned int`** . 이 문제를 해결하려면 다음과 같은 열거된 형식을 사용하는 것이 좋습니다.

    ```cpp
    enum class my_type : size_t {};
    ```

   그런 다음 **배치 new** 의 정의를 변경 하 고 **`delete`** 이 유형을 대신 두 번째 인수로 사용 `size_t` 합니다. 새 형식 (예:를 사용 하 여 `static_cast<my_type>` 정수 값에서 변환)을 전달 하 고, 및의 정의를 업데이트 하 여 **`new`** **`delete`** 다시 정수 형식으로 캐스팅 하는 경우에는 placement new에 대 한 호출도 업데이트 해야 합니다. 이를 위해를 사용할 필요는 없습니다. **`enum`** 멤버를 포함 하는 클래스 형식 `size_t` 도 작동 합니다.

   또 다른 솔루션은 **placement new** 를 함께 제거하는 것입니다. 코드에서 placement **new** 를 사용 하 여 배치 인수가 할당 되거나 삭제 되는 개체의 크기인 메모리 풀을 구현 하는 경우 크기가 지정 된 할당 해제 기능이 사용자 지정 메모리 풀 코드를 대체 하는 데 적합할 수 있으며 배치 함수를 제거 하 고 배치 함수 대신 고유한 두 인수 연산자를 사용할 수 있습니다 **`delete`** .

   코드를 바로 업데이트하지 않으려면 컴파일러 옵션 `/Zc:sizedDealloc-`를 사용하여 이전 동작으로 되돌릴 수 있습니다. 이 옵션을 사용 하면 인수가 두 개인 delete 함수가 존재 하지 않으며 **placement delete** 연산자와 충돌 하지 않습니다.

- **공용 구조체 데이터 멤버**

   공용 구조체의 데이터 멤버는 더 이상 참조 형식을 포함할 수 없습니다. 다음 코드는 Visual Studio 2013에서 성공적으로 컴파일되지만 Visual Studio 2015에서는 오류를 생성합니다.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   앞의 코드에서 발생하는 오류는 다음과 같습니다.

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   이 문제를 해결하려면 참조 형식을 포인터 또는 값으로 변경합니다. 형식을 포인터로 변경하려면 공용 구조체 필드를 사용하는 코드를 변경해야 합니다. 코드를 값으로 변경하면 공용 구조체에 저장된 데이터가 변경되며, union 형식의 필드는 같은 메모리를 공유하므로 이 변경이 다른 필드에 영향을 미칩니다. 값 크기에 따라 공용 구조체 크기도 변경할 수 있습니다.

- 현재 익명 공용 구조체는 표준을 더 준수합니다. 이전 컴파일러 버전에서는 익명 공용 구조체에 대한 명시적 생성자 및 소멸자를 생성했습니다. 이러한 컴파일러 생성 함수는 Visual Studio 2015에서 삭제되었습니다.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   앞의 코드는 Visual Studio 2015에서 다음 오류를 생성합니다.

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   이 문제를 해결하려면 생성자 및/또는 소멸자의 정의를 제공하세요.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **익명 구조체가 있는 공용 구조체**

   공용 구조체에서 익명 구조체 멤버의 런타임 동작이 표준을 준수하도록 변경되었습니다. 해당 공용 구조체가 생성될 때 공용 구조체의 익명 구조체 멤버에 대한 생성자가 더 이상 암시적으로 호출되지 않습니다. 또한 공용 구조체가 범위를 벗어날 때 공용 구조체의 익명 구조체 멤버에 대한 소멸자가 더 이상 암시적으로 호출되지 않습니다. 소멸자가 있는 명명된 멤버 구조체 S가 포함된 익명 구조체가 공용 구조체 U에 들어 있는 다음 코드를 고려하세요.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Visual Studio 2013에서 S에 대한 생성자는 공용 구조체가 생성될 때 호출되고 S에 대한 소멸자는 f 함수의 스택이 정리될 때 호출됩니다. 그러나 Visual Studio 2015에서는 생성자와 소멸자가 호출되지 않습니다. 컴파일러에서 이 동작 변경에 대해 경고를 표시합니다.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   원래 동작을 복원하려면 익명 구조체에 이름을 지정합니다. 익명이 아닌 구조체의 런타임 동작은 컴파일러 버전과 관계없이 동일합니다.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   또는 생성자 및 소멸자 코드를 새 함수로 이동하고 공용 구조체에 대한 생성자 및 소멸자에서 이들 함수에 호출을 추가하세요.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **템플릿 확인**

   템플릿의 이름 확인에 대한 변경 내용이 있습니다. C++에서 이름을 확인할 후보를 고려할 때 잠재적인 일치 항목으로 고려 중인 하나 이상의 이름에서 잘못된 템플릿 인스턴스화가 생성될 수 있습니다. 일반적으로 이러한 잘못된 인스턴스화로 인해 컴파일러 오류가 발생하지는 않습니다. 이 원칙을 SFINAE(Substitution Failure Is Not An Error)라고 합니다.

   현재 SFINAE에 따라 컴파일러가 클래스 템플릿의 특수화를 인스턴스화해야 하면 이 프로세스 중에 발생하는 오류는 컴파일러 오류입니다. 이전 버전에서는 컴파일러가 해당 오류를 무시합니다. 예를 들어, 다음 코드를 고려하세요.

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   현재 컴파일러로 컴파일할 경우 다음 오류가 발생합니다.

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   이는 is_base_of의 첫 번째 호출 지점에서 `D` 클래스가 아직 정의되지 않았기 때문입니다.

   이 경우에 문제를 해결하려면 클래스가 정의될 때까지 이러한 형식 특성을 사용하지 마세요. `B` 및 `D`의 정의를 코드 파일의 시작 부분으로 이동하면 오류가 해결됩니다. 정의가 헤더 파일에 있으면 헤더 파일의 include 문 순서를 확인하여 문제가 있는 템플릿이 사용되기 전에 클래스 정의가 컴파일되는지 확인합니다.

- **복사 생성자**

   Visual Studio 2013 및 Visual Studio 2015에서 클래스에 사용자 정의 이동 생성자가 있지만 사용자 정의 복사 생성자가 없는 경우 컴파일러는 해당 클래스에 대한 복사 생성자를 생성합니다. Dev14에서는 생성된 복사 생성자가 "= delete"로 표시됩니다.

<!--From here to VS_Update1 added 04/21/2017-->

- **extern “C”로 선언된 main에는 이제 반환 형식이 필요합니다.**

   다음 코드는 C4430을 생성합니다.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   오류를 해결하려면 반환 형식을 추가합니다.

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **typename이 멤버 이니셜라이저에서 허용되지 않음**

   다음 코드는 C2059를 생성합니다.

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   오류를 해결 하려면 이니셜라이저에서를 제거 **`typename`** 합니다.

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **명시적 특수화의 스토리지 클래스가 무시됩니다.**

   다음 코드에서 정적 스토리지 클래스 지정자가 무시됩니다.

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **클래스 템플릿 내부 static_assert에서 사용되는 상수가 항상 실패합니다.**

   다음 코드를 실행 하면이 **`static_assert`** 항상 실패 합니다.

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   이 문제를 해결 하려면 다음과 같이 값을 래핑합니다 **`struct`** .

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **전방 선언에 적용 되는 규칙입니다. C에만 적용 됩니다.**

   다음 코드는 C2065를 생성합니다.

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   이 문제를 해결하려면 적절한 정방향 선언을 추가하세요.

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **함수 포인터 형식의 더 일관된 적용**

   다음 코드는 C2197을 생성합니다.

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **오버로드된 함수에 대한 모호한 호출**

   다음 코드는 C266을 생성합니다. ‘N::bind’: 오버로드된 함수에 대한 모호한 호출

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   오류를 해결하려면 `bind: N::bind(...)`에 대한 호출을 정규화하면 됩니다. 그러나이 변경 내용이 선언 되지 않은 식별자 (C2065)를 통해 매니페스트 되는 경우 대신 선언으로이를 수정 하는 것이 적합할 수 있습니다 **`using`** .

   이 패턴은 ComPtr 및 `Microsoft::WRL` 네임스페이스의 기타 형식에서 자주 발생합니다.

- **잘못된 주소 수정**

   다음 코드는 C2440을 생성합니다. ‘=’: ‘type *’에서 ‘type’으로 변환할 수 없습니다. 오류를 해결하려면 &(type)를 (type)로 변경하고 (&f())를 (f())로 변경합니다.

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **문자열 리터럴이 상수 배열임**

   다음 코드는 C2664를 생성합니다. ‘void f(void *)’: 인수 1을 ‘const char (* )[2]’에서 ‘void *’로 변환할 수 없습니다.

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   오류를 해결하려면 함수 매개 변수 형식을 `const void*`로 변경하거나 `h`의 본문을 다음 예제와 같이 변경합니다.

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C++11 UDL 문자열**

   다음 코드는 오류 C3688을 생성합니다. 잘못된 리터럴 접미사 ‘L’; 리터럴 연산자 또는 리터럴 연산자 템플릿 ‘operator ""L’을 찾을 수 없습니다.

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   오류를 해결하려면 코드를 변경하여 공백을 추가하세요.

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   위의 예제에서 `MACRO`는 더 이상 두 개의 토큰으로 구문 분석되지 않습니다(문자열 뒤에 매크로가 나옴). 이제 단일 토큰 UDL로 구문 분석됩니다. L""L""에도 동일하게 적용됩니다. 이전에는 L"" 및 L""로 구문 분석되었고 지금은 L""L 및 ""로 구문 분석됩니다.

   문자열 연결 규칙도 L“a” “b”가 L“ab”와 같음을 의미하는 표준 준수에 추가되었습니다. 이전 버전의 Visual Studio에서는 문자 너비가 다른 문자열의 연결을 허용하지 않았습니다.

- **C++11 빈 문자가 제거됨**

   다음 코드는 오류 C2137을 생성합니다. 빈 문자 상수

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   오류를 해결하려면 코드를 변경하여 null을 명시적으로 만들어야 합니다.

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **MFC 예외는 복사할 수 없으므로 값으로 catch할 수 없음**

   이제 MFC 애플리케이션의 다음 코드는 오류 C2316을 발생시킵니다. ‘D’: 소멸자 및(또는) 복사 생성자가 액세스할 수 없는 상태이거나 삭제되었으므로 catch될 수 없습니다.

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   코드를 수정하려면 catch 블록을 `catch (const D &)`로 변경할 수 있지만 대개 MFC TRY/CATCH 매크로를 사용하는 것이 더 좋은 해결 방법입니다.

- **`alignof` 이제 키워드**

   다음 코드는 오류 C2332를 생성합니다. ‘class’: 태그 이름이 누락되었습니다. 코드를 수정 하려면 클래스의 이름을 변경 하거나 클래스에서와 동일한 작업을 수행 하는 경우 **`alignof`** 클래스를 new 키워드로 바꿉니다.

    ```cpp
    class alignof{}
    ```

- **`constexpr` 이제 키워드**

   다음 코드는 이제 오류 C2059를 생성합니다. 구문 오류: ‘)’. 코드를 수정 하려면 호출 되는 모든 함수 또는 변수 이름을 바꾸어야 합니다 **`constexpr`** .

    ```cpp
    int constexpr() {return 1;}
    ```

- **이동 가능한 형식은 const일 수 없음**

   함수가 이동할 형식을 반환 하는 경우 해당 반환 형식은이 아니어야 합니다 **`const`** .

- **삭제된 복사 생성자**

   다음 코드는 C2280을 반환합니다. ‘S::S(S &&)’: 삭제된 함수를 참조하려고 합니다.

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   오류를 해결하려면 `S2`에 대한 직접 초기화를 사용합니다.

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **람다 캡처가 없을 경우에만 생성되는 함수 포인터로의 변환**

   다음 코드는 Visual Studio 2015에서 C2664를 생성합니다.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   오류를 해결하려면 캡처 목록에서 `=`을 제거합니다.

- **변환 연산자가 포함된 모호한 호출**

   다음 코드는 오류 C2440을 생성합니다. ‘type cast’: ‘S2’에서 ‘S1’으로 변환할 수 없습니다.

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   오류를 해결하려면 변환 연산자를 명시적으로 호출합니다.

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   다음 코드는 오류 C2593을 생성합니다. ‘operator =’이 모호합니다.

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   오류를 해결하려면 변환 연산자를 명시적으로 호출합니다.

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **NSDMI(비정적 데이터 멤버 초기화)에서 잘못된 복사 초기화 수정**

   다음 코드는 오류 C2664를 생성합니다. ‘S1::S1(S1 &&)’: 인수 1을 ‘bool’에서 ‘const S1 &’로 변환할 수 없습니다.

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   오류를 해결하려면 직접 초기화를 사용합니다.

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **decltype 문의 내부에서 생성자 액세스**

   다음 코드는 C2248을 생성합니다. ‘S::S’: 클래스 ‘S’에서 선언된 전용 멤버에 액세스할 수 없습니다.

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   오류를 해결하려면 `S2`에 대한 friend 선언을 `S`에 추가합니다.

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **람다의 기본 ctor가 암시적으로 삭제됨**

   다음 코드는 오류 C3497을 생성합니다. 람다의 인스턴스를 생성할 수 없습니다.

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   오류를 해결하려면 기본 생성자를 호출할 필요성을 제거합니다. 람다가 아무것도 캡처하지 않으면 함수 포인터로 캐스트될 수 있습니다.

- **삭제된 대입 연산자가 있는 람다**

   다음 코드는 오류 C2280을 생성합니다.

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   오류를 해결하려면 람다를 functor 클래스로 바꾸거나 대입 연산자를 사용할 필요성을 제거합니다.

- **삭제된 복사 생성자가 포함된 개체를 이동하려고 함**

   다음 코드는 오류 C2280을 생성합니다. ‘moveable::moveable(const moveable &)’: 삭제된 함수를 참조하려고 합니다.

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   오류를 해결하려면 `std::move`를 대신 사용합니다.

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **로컬 클래스가 나중에 같은 함수에서 정의된 다른 로컬 클래스를 참조할 수 없음**

   다음 코드는 오류 C2079를 생성합니다. ‘s’가 정의되지 않은 구조체 ‘main::S2’를 사용합니다.

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   오류를 해결하려면 `S2`의 정의로 이동합니다.

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **파생된 ctor의 본문에서 보호된 기본 ctor를 호출할 수 없습니다.**

   다음 코드는 오류 C2248을 생성합니다. ‘S1::S1’: 클래스 ‘S1’에서 선언된 보호된 멤버에 액세스할 수 없습니다.

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   오류를 해결하려면 `S2`에서 `S1()`에 대한 호출을 생성자로부터 제거하고 필요한 경우 다른 함수에 삽입합니다.

- **{} 포인터로의 변환을 방지 합니다.**

   다음 코드는 C2439를 생성합니다. ‘S::p’: 멤버를 초기화할 수 없습니다.

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   오류를 해결 하려면 `0` 다음 예제와 같이에서 중괄호를 제거 하거나 **`nullptr`** 대신을 사용 합니다.

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **괄호가 있는 잘못된 매크로 정의 및 사용**

   다음 예제는 오류 C2008을 생성합니다. ‘;’: 매크로 정의에 사용할 수 없습니다.

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   문제를 해결하려면 맨 위 줄을 `#define A();`로 변경하세요.

   다음 코드는 오류 C2059를 생성합니다. 구문 오류: ‘)’.

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   코드를 수정하려면 A와 () 사이에서 공백을 제거하세요.

   다음 코드는 오류 C2091을 생성합니다. 함수가 함수를 반환합니다.

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   오류를 해결하려면 S에서 DECLARE 뒤의 괄호를 제거합니다. `DECLARE;`.

   다음 코드는 오류 C2062를 생성합니다. 형식 ‘int’를 사용할 수 없습니다.

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   문제를 해결하려면 다음과 같이 `A`를 정의합니다.

    ```cpp
    #define A int
    ```

- **선언의 추가 괄호**

   다음 코드는 오류 C2062를 생성합니다. 형식 ‘int’를 사용할 수 없습니다.

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   오류를 해결하려면 `j` 앞뒤에서 괄호를 제거하세요. 명확성을 위해 괄호가 필요한 경우를 사용 **`typedef`** 합니다.

- **컴파일러에서 생성되는 생성자 및 __declspec(novtable)**

   Visual Studio 2015에서는 가상 기본 클래스가 포함된 추상 클래스의 컴파일러 생성 인라인 생성자가 `__declspec(dllimport)`과 함께 사용될 경우 부적절한 `__declspec(novtable)` 사용을 노출할 가능성이 큽니다.

- **auto에는 direct-list-initialization에서 단일 식 필요**

   다음 코드는 오류 C3518을 생성합니다. 'testPositions': direct-list-initialization 컨텍스트에서 'auto'에 대한 형식은 하나의 이니셜라이저 식에서만 추론할 수 있습니다.

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   오류를 해결하기 위해 `testPositions`를 다음과 같이 초기화할 수 있습니다.

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **is_convertible에 대한 형식 및 형식 포인터 확인**

   다음 코드에서는 정적 어설션이 실패합니다.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   오류를 해결 하려면 **`static_assert`** 및에 대 한 포인터를 비교 하도록를 변경 합니다 `D` `B2` .

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **novtable (__declspec) 선언은 일치 해야 합니다.**

   **`__declspec`** 모든 라이브러리에서 선언이 일치 해야 합니다. 다음 코드는 ODR(단일 정의 규칙) 위반을 생성합니다.

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

### <a name="conformance-improvements-in-update-1"></a><a name="VS_Update1"></a> 업데이트 1의 규칙 향상

- **개인 가상 기본 클래스 및 간접 상속**

   이전 버전의 컴파일러에서는 파생 클래스가 간접적으로 파생된 `private virtual` 기본 클래스의 멤버 함수를 호출하도록 허용했습니다. 이 이전 동작은 올바르지 않으며, C++ 표준을 준수하지 않습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 결과적으로 컴파일러 오류 C2280이 발생합니다.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   예제(이전)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   예제(이후)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \- 또는 -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **오버로드된 operator new 및 operator delete**

   이전 버전의 컴파일러는 비멤버 **operator new** 및 비멤버 **operator delete** 를 정적으로 선언하고 글로벌 네임스페이스 이외의 네임스페이스에서 선언할 수 있었습니다.  이 이전 동작은 프로그램에서 **`new`** 프로그래머가 의도 한 또는 연산자 구현을 호출 하지 않아서 잘못 된 자동 런타임 동작이 발생 하는 위험을 생성 **`delete`** 했습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C2323이 발생합니다.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   예제(이전)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   예제(이후)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   또한 컴파일러가 특정 진단을 제공 하지는 않지만 인라인 연산자 **`new`** 는 형식이 잘못 된 것으로 간주 됩니다.

- ***비클래스 형식에서 'operator* type** ()'(사용자 정의 변환) 호출

   이전 버전의 컴파일러에서는 'operator *type* ()'을 자동으로 무시하면서 비클래스 형식에서 호출할 수 있었습니다. 이 이전 동작으로 잘못된 코드가 자동으로 생성되어 예기치 않은 런타임 동작이 발생하는 위험이 초래되었습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C2228이 발생합니다.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   예제(이전)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   예제(이후)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **상세 형식 지정자의 중복 typename**

   이전 버전의 컴파일러에서는 **`typename`** 상세 형식 지정자를 사용할 수 있지만 이러한 방식으로 작성 된 코드는 의미 체계가 잘못 되었습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C3406이 발생합니다.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   예제(이전)

    ```cpp
    template <typename class T>
    class container;
    ```

   예제(이후)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **이니셜라이저 목록에서 배열의 형식 추론**

   이전 버전의 컴파일러는 이니셜라이저 목록에서 배열의 형식 추론을 지원하지 않았습니다. 이제 컴파일러가 이러한 형태의 형식 추론을 지원합니다. 결과적으로 이니셜라이저 목록을 사용한 함수 템플릿 호출은 이제 모호하거나 이전 버전의 컴파일러와 다른 오버로드가 선택될 수 있습니다. 이러한 문제를 해결하려면 이제 프로그램에서 프로그래머가 의도한 오버로드를 명시적으로 지정해야 합니다.

   이 새로운 동작으로 인해 오버로드 확인에서 기록 후보와 똑같이 우수한 추가 후보를 사용하게 되면 호출이 모호해지며 결과적으로 컴파일러에서 컴파일러 오류 C2668이 발생합니다.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   예제 1: 오버로드된 함수에 대한 호출이 모호합니다(이전).

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   예제 1: 오버로드된 함수에 대한 호출이 모호합니다(이후).

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   이 새로운 동작으로 오버로드 확인에서 기록 후보보다 더 일치하는 추가 후보를 사용하게 되면 호출이 새 후보로 명확하게 결정되므로 프로그래머가 의도한 것과 다른 프로그램 동작 변경을 초래하게 됩니다.

   예제 2: 오버로드 확인의 변경(이전)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   예제 2: 오버로드 확인의 변경(이후)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **switch 문 경고의 복원**

   이전 버전의 컴파일러에서는 문과 관련 된 일부 경고를 제거 했습니다. **`switch`** 이제 이러한 경고가 복원 되었습니다. 이제 컴파일러에서 복원된 경고가 발생합니다. 이제 특정 사례(기본 사례 포함)와 관련된 경고가 switch 문의 마지막 줄 대신, 잘못된 사례가 포함된 줄에서 발생합니다. 이제 과거와는 다른 줄에서 해당 경고가 발생하므로 이전에 `#pragma warning(disable:####)` 을 사용하면 표시되지 않았던 경고가 더 이상 의도한 대로 숨겨지지 않을 수 있습니다. 이러한 경고를 의도한 대로 표시하지 않으려면 `#pragma warning(disable:####)` 지시문을 잘못된 첫 번째 사례 위의 줄로 이동해야 합니다. 복원된 경고는 다음과 같습니다.

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   C4063의 예제(이전)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   C4063의 예제(이후)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   복원된 다른 경고의 예는 해당 설명서에 제공됩니다.

- **#include: 경로 이름에 부모 디렉터리 지정자 '..' 사용** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 `#include` 지시문의 경로 이름에서 부모 디렉터리 지정자('..')의 사용을 검색하지 못했습니다. 이러한 방식으로 작성된 코드는 일반적으로 프로젝트 상대 경로를 부정확하게 사용하여 프로젝트의 외부에 존재하는 헤더를 포함합니다. 이 이전 동작은 프로그램이 프로그래머가 의도한 것과 다른 소스 파일을 포함하여 컴파일되거나 이러한 상대 경로가 다른 빌드 환경으로 이식되지 않는 위험을 초래했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 선택적으로 컴파일러 경고 C4464가 발생합니다.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   예제(이전)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   예제(이후)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   또한 컴파일러가 특정 진단을 제공하지는 않지만, 프로젝트의 Include 디렉터리를 지정하는 데 부모 디렉터리 지정자("..")를 사용하지 않는 것이 좋습니다.

- **#pragma optimize()에서 헤더 파일의 끝을 넘어 확장** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 변환 단위 내에 포함된 헤더 파일을 이스케이프하는 최적화 플래그 설정에 대한 변경 내용을 검색하지 못했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 잘못된 `#include`의 위치에서 선택적으로 컴파일러 경고 C4426이 발생합니다. 이 경고는 변경 내용이 명령줄 인수에 의해 컴파일러에 설정된 최적화 플래그와 충돌하는 경우에만 발생합니다.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   예제(이전)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   예제(이후)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **#pragma warning(push)** 및 **#pragma warning(pop)** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러는 다른 소스 파일에서 `#pragma warning(push)` 상태 변경이 `#pragma warning(pop)` 상태 변경과 쌍을 이루는 것(의도되는 경우가 드묾)을 검색하지 못했습니다. 이 이전 동작으로 프로그램이 프로그래머가 의도한 것과 다르게 설정된 경고 집합으로 컴파일되어 잘못된 자동 런타임 동작이 발생하는 위험이 초래됩니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 일치하는 `#pragma warning(pop)`의 위치에서 선택적으로 컴파일러 경고 C5031이 발생합니다. 이 경고에는 해당 #pragma warning(push)의 위치를 참조하는 참고가 포함되어 있습니다.

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   예제(이전)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   예제(이후)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   드물긴 하지만 의도적으로 이러한 코드를 작성하는 경우가 있습니다. 이러한 방식으로 작성된 코드는 `#include` 순서의 변경에 민감합니다. 가능한 경우 소스 코드 파일에서 자동으로 포함된 방식으로 경고 상태를 관리하는 것이 좋습니다.

- **#pragma warning(push) 불일치** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러는 변환 단위의 끝에서 `#pragma warning(push)` 상태 변경 불일치를 검색하지 못했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 일치하지 않는 `#pragma warning(push)`의 위치에서 선택적으로 컴파일러 경고 C5032가 발생합니다. 이 경고는 변환 단위에 컴파일 오류가 없는 경우에만 발생합니다.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   예제(이전)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   예제(이후)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **개선된 #pragma warning 상태 추적의 결과로 추가 경고가 발생할 수 있습니다.**

   이전 버전의 컴파일러는 의도된 모든 경고를 발생시키기에는 불충분한 수준으로 #pragma warning 상태 변경을 추적했습니다. 이 동작으로 프로그래머가 의도한 것과 다른 상황에서 특정 경고가 효과적으로 표시되지 않는 위험이 초래됩니다. 이제 컴파일러는 `#pragma warning` 상태(특히 템플릿 내부의 `#pragma warning` 상태 변경과 관련된 내용)를 더욱 강력하게 추적하며, 선택적으로 새로운 경고 C5031 및 C5032가 발생합니다. 이러한 경고는 프로그래머가 의도하지 않게 사용된 `#pragma warning(push)` 및 `#pragma warning(pop)`을 찾는 데 도움이 됩니다.

   개선된 `#pragma warning` 상태 변경 추적의 결과로, 이전에 제대로 표시되지 않은 경고 또는 이전에 잘못 진단된 문제와 관련된 경고가 이제 발생할 수 있습니다.

- **접근할 수 없는 코드의 개선된 ID**

   C++ 표준 라이브러리의 변경 및 이전 버전의 컴파일러에 비해 향상된 인라인 함수 호출 기능을 통해 컴파일러가 이제 특정 코드에 접근할 수 없음을 증명할 수 있습니다. 이 새로운 동작으로 경고 C4720의 인스턴스가 새로 그리고 더욱 자주 발생할 수 있습니다.

    ```Output
    warning C4720: unreachable code
    ```

   최적화 프로세스에서 더 많은 함수 호출을 인라인하거나 중복 코드를 제거하거나 특정 코드에 접근할 수 없는지 확인할 수 있도록 하므로, 이 경고는 대개 최적화를 사용하면서 컴파일할 경우에만 발생할 수 있습니다. 경고 C4720의 새 인스턴스가 특히 [std::find](../standard-library/algorithm-functions.md#find)의 사용과 관련하여 **try/catch** 블록에서 자주 발생했음을 관찰했습니다.

   예제(이전)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   예제(이후)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

### <a name="conformance-improvements-in-update-2"></a><a name="VS_Update2"></a> 업데이트 2의 규칙 향상

- **SFINAE 식에 대한 부분 지원으로 인해 추가 경고 및 오류가 발생할 수 있습니다.**

   이전 버전의 컴파일러는 **`decltype`** SFINAE 식에 대 한 지원 부족으로 지정자 내의 특정 식 종류를 구문 분석 하지 않았습니다. 이 이전 동작은 올바르지 않으며, C++ 표준을 준수하지 않습니다. 지속적인 규칙 향상으로 인해 이제 컴파일러는 이러한 식을 구문 분석하고 SFINAE 식에 대한 부분 지원을 합니다. 결과적으로 이제 컴파일러는 이전 버전의 컴파일러가 구문 분석하지 않았던 식에서 경고 및 오류를 발생합니다.

   이 새로운 동작이 **`decltype`** 아직 선언 되지 않은 형식을 포함 하는 식을 구문 분석할 때 컴파일러에서 컴파일러 오류 C2039 발생 합니다.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   예제 1: 선언되지 않은 형식 사용(이전)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   예제 1(이후)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   이 새 동작에서 키워드를 **`decltype`** 사용 하는 데 필요한 식의 구문 분석 **`typename`** 을 통해 종속 이름이 형식이 되도록 지정 하는 경우 컴파일러에서 컴파일러 경고를 C4346 컴파일러 오류 C2923을 발생 시킵니다.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   예제 2: 종속 이름이 형식이 아님(이전)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   예제 2(이후)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- **`volatile`****멤버 변수가 암시적으로 정의 된 생성자 및 대입 연산자를 방지** 합니다.

   이전 버전의 컴파일러에서는 **`volatile`** 멤버 변수가 있는 클래스가 기본 복사/이동 생성자 및 기본 복사/이동 할당 연산자를 자동으로 생성 하도록 허용 했습니다. 이 이전 동작은 올바르지 않으며, C++ 표준을 준수하지 않습니다. 이제 컴파일러는 멤버 변수가 있는 클래스에 **`volatile`** trivial 생성 및 대입 연산자가 있는 것으로 간주 하 여 이러한 연산자의 기본 구현이 자동으로 생성 되는 것을 방지 합니다. 이러한 클래스가 공용 구조체(또는 클래스 내의 익명 공용 구조체)의 멤버이면 공용 구조체(또는 익명 공용 구조체를 포함하는 클래스)의 복사/이동 생성자 및 복사/이동 대입 연산자는 삭제된 것으로 암시적으로 정의됩니다. 명시적으로 정의하지 않고 공용 구조체(또는 익명 공용 구조체를 포함하는 클래스)를 만들거나 복사하려 하면 오류가 발생하며 컴파일러에서 결과적으로 컴파일러 오류 C2280을 발생합니다.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   예제(이전)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   예제(이후)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **정적 멤버 함수는 cv 한정자를 지원하지 않습니다.**

   이전 버전의 Visual Studio 2015는 고정 멤버 함수에 cv 한정자가 포함되는 것을 허용했습니다. 이 동작은 Visual Studio 2015 및 Visual Studio 2015 업데이트 1에서의 문제 재발로 인한 것입니다. Visual Studio 2013 및 이전 버전의 컴파일러는 이런 방식으로 작성된 코드를 거부합니다. Visual Studio 2015 및 Visual Studio 2015 업데이트 1의 동작은 잘못되었으며 C++ 표준을 준수하지 않습니다.  Visual Studio 2015 업데이트 2는 이런 식으로 작성된 코드를 거부하며 대신 컴파일러 오류 C2511을 발생합니다.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   예제(이전)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   예제(이후)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **열거형의 정방향 선언은 WinRT 코드에서 허용되지 않음** (`/ZW`에만 영향을 줌)

   Windows 런타임 (WinRT)에 대해 컴파일된 코드는 **`enum`** 관리 되는 c + + 코드가 컴파일러 스위치를 사용 하 여 .Net Framework에 대해 컴파일되는 경우와 마찬가지로 형식을 전방으로 선언할 수 없습니다 `/clr` . 이 동작을 통해 열거형의 크기를 항상 알 수 있으며 WinRT 형식 시스템에 올바르게 프로젝션될 수 있음을 확인합니다. 컴파일러는 이러한 방식으로 작성된 코드를 거부하고 컴파일러 오류 C3197과 함께 컴파일러 오류 C2599를 발생합니다.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   예제(이전)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   예제(이후)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **오버로드된 멤버가 아닌 연산자 new 및 연산자 delete는 인라인으로 선언할 수 없습니다** (수준 1(`/W1`)이 기본적으로 설정되어 있음).

   이전 버전의 컴파일러는 멤버가 아닌 연산자 new 및 연산자 delete 함수가 인라인으로 선언될 때 경고를 발생하지 않습니다. 이 방식으로 작성된 코드는 형식이 잘못되었으며(진단이 필요하지 않음) 진단하기 힘들 수 있는 일치하지 않는 new 및 delete 연산자로 인해 특히 크기가 지정된 할당 해제와 함께 사용 시 메모리 문제를 일으킬 수 있습니다. 이제 컴파일러는 이런 식으로 작성된 코드를 식별하기 위해 경고 C4595를 발생합니다.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   예제(이전)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   예제(이후)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   이러한 방식으로 작성된 코드를 수정하려면 연산자 정의를 헤더 파일에서 해당하는 소스 파일로 이동해야 합니다.

### <a name="conformance-improvements-in-update-3"></a><a name="VS_Update3"></a> 업데이트 3의 규칙 향상

- **이제 std::is_convertable이 자체 할당을 검색함** (표준 라이브러리)

   이전 버전의 `std::is_convertable` 형식 특성은 복사 생성자가 삭제되거나 private인 경우 클래스 형식의 자체 할당을 제대로 검색하지 못했습니다. 이제 `std::is_convertable<>::value` 는 **`false`** 삭제 된 또는 전용 복사 생성자를 사용 하 여 클래스 형식에 적용 될 때로 올바르게 설정 됩니다.

   이 변경과 관련된 컴파일러 진단은 없습니다.

   예제

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   이전 버전의 컴파일러에서는가로 잘못 설정 되었기 때문에이 예제의 맨 아래에 있는 정적 어설션이 전달 `std::is_convertable<>::value` **`true`** 됩니다. 이제 `std::is_convertable<>::value` 이로 올바르게 설정 되어 **`false`** 정적 어설션이 실패 합니다.

- **기본값으로 설정되었거나 삭제된 trivial 복사 및 이동 생성자가 액세스 지정자를 따름**

   이전 버전의 컴파일러에서는 호출을 허용하기 전에 기본값으로 설정되었거나 삭제된 trivial 복사 및 이동 생성자의 액세스 지정자를 확인하지 않았습니다. 이 이전 동작은 올바르지 않으며, C++ 표준을 준수하지 않습니다. 경우에 따라 이 이전 동작으로 잘못된 코드가 자동으로 생성되어 예기치 않은 런타임 동작이 발생하는 위험이 초래되었습니다. 이제 컴파일러에서 기본값으로 설정되었거나 삭제된 trivial 복사 및 이동 생성자의 액세스 지정자를 검사하여 호출 가능 여부를 확인하고, 호출할 수 없는 경우 결과로 컴파일러 경고 C2248을 실행합니다.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   예제(이전)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   예제(이후)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **특성 사용 ATL 코드 지원 중단** (수준 1(`/W1`)이 기본적으로 설정되어 있음)

   이전 버전의 컴파일러에서는 특성 사용 ATL 코드를 지원했습니다. [Visual Studio 2008부터 시작](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008)된 특성 사용 ATL 코드 지원 제거의 다음 단계로 특성 사용 ATL 코드가 더 이상 사용되지 않습니다. 이제 컴파일러에서 사용되지 않는 이러한 종류의 코드를 식별하기 위해 컴파일러 경고 C4467을 실행합니다.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   컴파일러에서 지원이 제거될 때까지 ATL 특성 코드를 계속 사용하려는 경우 `/Wv:18` 또는 `/wd:4467` 명령줄 인수를 컴파일러에 전달하거나 소스 코드에 `#pragma warning(disable:4467)`을 추가하여 이 경고를 해제할 수 있습니다.

   예제 1(이전)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   예제 1(이후)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   사용되지 않는 ATL 특성의 사용을 방지하기 위해 아래 예제 코드와 같이 IDL 파일을 만들 수 있습니다.

   예제 2(이전)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   먼저 *.idl 파일을 만듭니다. 생성된 vc140.idl 파일을 사용하여 인터페이스와 주석이 포함된 \*.idl 파일을 가져올 수 있습니다.

   그런 다음 빌드에 MIDL 단계를 추가하여 C++ 인터페이스 정의가 생성되었는지 확인합니다.

   예제 2 IDL(이후)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   아래 예제 코드와 같이 구현 파일에서 직접 ATL을 사용합니다.

   예제 2 구현(이후)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **미리 컴파일된 헤더(PCH) 파일 및 일치하지 않는 #include 지시문** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 미리 컴파일된 헤더(PCH) 파일을 사용할 때 `-Yc` 및 `-Yu` 컴파일 간에 일치하지 않는 소스 파일의 `#include` 지시문을 허용했습니다. 이런 방식으로 작성된 코드는 컴파일러에서 더 이상 허용되지 않습니다.   PCH 파일 사용 시 일치하지 않는 `#include` 지시문을 식별하기 위해 이제 컴파일러에서 컴파일러 경고 CC4598을 실행합니다.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   예제(이전):

   X.cpp(-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp(-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   예제(이후)

   X.cpp(-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp(-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **미리 컴파일된 헤더(PCH) 파일 및 일치하지 않는 include 디렉터리** (`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 미리 컴파일된 헤더(PCH) 파일을 사용할 때 `-Yc`와 `-Yu` 컴파일 간의 컴파일러에 대해 일치하지 않는 include 디렉터리(`-I`) 명령줄 인수를 허용했습니다. 이런 방식으로 작성된 코드는 컴파일러에서 더 이상 허용되지 않습니다. PCH 파일 사용 시 일치하지 않는 include 디렉터리(`-I`) 명령줄 인수를 식별하기 위해 이제 컴파일러에서 컴파일러 경고 CC4599를 실행합니다.

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   예제(이전)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   예제(이후)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 규칙 변경 내용

### <a name="compiler"></a>컴파일러

- **final** 키워드는 이제 이전에 컴파일되었을 수 있는 경우 확인되지 않은 기호 오류를 생성합니다.

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   이전 버전에서는 호출이 호출 되기 때문에 오류가 발생 하지 않았지만 **`virtual`** 프로그램이 런타임에 충돌 합니다. 이제는 클래스가 final인 것으로 알려지기 때문에 링커 오류가 발생합니다. 이 예제에서 오류를 해결하려면 `S2::f`의 정의가 포함된 obj에 대해 링크합니다.

- 네임스페이스의 friend 함수를 사용하는 경우 friend 함수를 참조하기 전에 다시 선언해야 합니다. 그렇지 않으면 이제 컴파일러가 ISO C++ 표준을 준수하므로 오류가 발생합니다. 예를 들어 이 예제는 더 이상 컴파일되지 않습니다.

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   이 코드를 수정 하려면 함수를 선언 합니다 **`friend`** .

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- C++ 표준은 클래스에서 명시적 특수화를 허용하지 않습니다. Microsoft C++ 컴파일러는 어떤 경우에는 명시적 특수화를 허용하지만, 다음 예제와 같은 경우에는 컴파일러가 두 번째 함수를 첫 번째 함수의 특수화로 간주하지 않기 때문에 이제 오류가 생성됩니다.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   이 코드를 수정하려면 두 번째 함수를 수정합니다.

    ```cpp
    template <> void f(char& val);
    ```

- 다음 예제에서 컴파일러는 더 이상 두 함수를 구분하려고 시도하지 않으며 이제 오류가 발생합니다.

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   이 코드를 수정하려면 호출을 명확히 지정합니다.

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- 컴파일러가 ISO c + + 11을 준수 하도록 하기 전에 다음 코드는를 컴파일하여 `x` 형식으로 확인 됩니다 **`int`** .

    ```cpp
    auto x = {0};
    int y = x;
    ```

   이 코드는 이제 `x` 형식으로 확인 `std::initializer_list<int>` 되 고, 형식에 할당 하려고 하는 다음 줄에서 오류를 발생 시킵니다 `x` **`int`** . 기본적으로 변환 되지 않습니다. 이 코드를 수정 하려면를 사용 하 여를 **`int`** 바꿉니다 **`auto`** .

    ```cpp
    int x = {0};
    int y = x;
    ```

- 오른쪽 값의 형식이 초기화되고 있는 왼쪽 값의 형식과 일치하지 않는 경우 집계 초기화는 더 이상 허용되지 않고, ISO C++11 표준이 축소 전환 없이 작업하려면 균일 초기화가 필요하기 때문에 오류가 발생합니다. 이전에는 축소 변환을 사용할 수 있는 경우 [컴파일러 경고(수준 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) 경고가 오류 대신 발생했을 것입니다.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   이 코드를 수정하려면 명시적 축소 변환을 추가합니다.

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- 다음과 같은 초기화는 더 이상 허용되지 않습니다.

    ```cpp
    void *p = {{0}};
    ```

   이 코드를 수정하려면 다음 형태 중 하나를 사용합니다.

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- 이름 조회가 변경되었습니다. 다음 코드는 Visual Studio 2012 및 Visual Studio 2013의 C++ 컴파일러에서 다르게 결정됩니다.

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   Visual Studio 2012에서 `E1` 식의 `E1::b`는 글로벌 범위에서 `::E1`로 확인되었습니다. Visual Studio 2013에서 `E1` 식의 `E1::b`는 `main()`의 `typedef E2` 정의로 확인되며 `::E2` 형식을 갖습니다.

- 개체 레이아웃이 변경되었습니다. x64에서 클래스의 개체 레이아웃은 이전 릴리스에서 변경될 수 있습니다. 함수가 있지만 함수를 **`virtual`** 포함 하는 기본 클래스가 없는 경우 **`virtual`** 컴파일러의 개체 모델은 **`virtual`** 데이터 멤버 레이아웃 뒤의 함수 테이블에 포인터를 삽입 합니다. 즉, 레이아웃이 최적의 상태가 아닌 경우도 있습니다. 이전 릴리스에서 x64 최적화를 하면 레이아웃 향상을 시도하지만 복잡한 코드 상황에서는 올바르게 작동하지 않기 때문에 Visual Studio 2013에서 제거되었습니다. 다음 코드를 예로 들 수 있습니다.

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- Visual Studio 2013에서 x64의 `sizeof(S2)` 결과는 48이지만 이전 릴리스에서는 32로 계산됩니다. X 64 용 Visual Studio 2013 c + + 컴파일러에서이를 32으로 계산 하려면 함수가 포함 된 더미 기본 클래스를 추가 합니다 **`virtual`** .

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   코드에서 이전 릴리스가 최적화 하려고 했던 위치를 찾으려면 해당 릴리스의 컴파일러를 컴파일러 옵션과 함께 사용 하 `/W3` 고 경고 C4370를 설정 합니다. 예를 들면 다음과 같습니다.

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Visual Studio 2013 이전에 이 코드는 다음 메시지를 출력합니다. "경고 C4370: 'S2': 압축 기능이 향상되어 이전 버전의 컴파일러에서 클래스 레이아웃이 변경되었습니다."

   x86 컴파일러에는 모든 버전의 컴파일러에서 동일한 차선의 레이아웃 문제가 발생합니다. 예를 들어 이 코드가 x86에 대해 컴파일되면

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   `sizeof(S)`의 결과는 24입니다. 그러나 x64에서 언급된 해결 방법을 사용하는 경우 16으로 줄어들 수 있습니다.

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>표준 라이브러리

Visual Studio 2013의 C++ 컴파일러는 Visual Studio 2010에서 구현된 _ITERATOR_DEBUG_LEVEL의 불일치와 RuntimeLibrary 불일치를 감지합니다. 컴파일러 옵션 `/MT`(정적 릴리스), `/MTd`(정적 디버그), `/MD`(동적 릴리스) 및 `/MDd`(동적 디버그)가 혼합되면 이러한 불일치가 발생합니다.

- 코드에서 이전 릴리스의 시뮬레이트된 별칭 템플릿을 승인하는 경우 이를 변경해야 합니다. 예를 들어 `allocator_traits<A>::rebind_alloc<U>::other` 대신에 이제는 `allocator_traits<A>::rebind_alloc<U>`로 지정해야 합니다. `ratio_add<R1, R2>::type`이 더 이상 필요하지 않고 `ratio_add<R1, R2>`로 지정하는 것이 좋지만 감소된 비율에 대한 "type" typedef가 있으려면(이미 감소된 경우 같은 형식) `ratio<N, D>`가 필요하기 때문에 전자가 계속 컴파일됩니다.

- `#include <algorithm>` 또는 `std::min()`를 호출하는 경우 `std::max()`을 사용해야 합니다.

- 기존 코드에서 이전 릴리스의 시뮬레이션 된 범위가 지정 된 열거형을 사용 하는 경우 (네임 스페이스로 래핑된 기존의 범위가 지정 되지 않은 열거형) 변경 해야 합니다. 예를 들어 `std::future_status::future_status` 형식을 참조한 경우 이제는 `std::future_status`로 지정해야 합니다. 그러나 대부분의 코드는 영향을 받지 않습니다. 예를 들어 `std::future_status::ready`는 계속 컴파일됩니다.

- `explicit operator bool()`이 operator unspecified-bool-type()보다 더 엄격합니다. `explicit operator bool()`은 bool로의 명시적 변환(예: `shared_ptr<X> sp`의 경우 `static_cast<bool>(sp)` 및 `bool b(sp)`가 유효함)을 허용할 뿐만 아니라 bool로의 부울 테스트 가능한 "컨텍스트 변환"(예: `if (sp)`, `!sp`, `sp &&`)도 허용합니다. 그러나 `explicit operator bool()`은 bool로의 암시적 변환을 금지하므로 `bool b = sp;`로 지정할 수 없으며 bool 반환 형식의 경우 `return sp`로 지정할 수 없습니다.

- 실제 variadic 템플릿이 구현되었으므로 _VARIADIC_MAX 및 관련 매크로는 영향을 주지 않습니다. _VARIADIC_MAX를 계속 정의하더라도 무시됩니다. 다른 방식으로 시뮬레이션된 variadic 템플릿을 지원하기 위한 매크로 체계를 승인한 경우 코드를 변경해야 합니다.

- 일반적인 키워드 외에도 C++ 표준 라이브러리 헤더에서는 이제 상황에 맞는 키워드 **override** 및 **final** 에 대한 매크로 교체를 금지합니다.

- `reference_wrapper`, `ref()` 및 `cref()`는 이제 임시 개체에 대한 바인딩을 금지합니다.

- \<random> 은 이제 컴파일 타임 사전 조건을 엄격 하 게 적용 합니다.

- 다양한 C++ 표준 라이브러리 형식 특성에는 "T가 완전한 형식이어야 함"이라는 사전 조건이 있습니다. 이제 컴파일러에서 이 사전 조건을 더욱 엄격하게 적용하지만 모든 상황에서 적용할 수 있는 것은 아닙니다. C++ 표준 라이브러리 사전 조건을 위반하면 정의되지 않은 동작이 발생하기 때문에 표준에서는 적용이 보장되지 않습니다.

- C++ 표준 라이브러리는 `/clr:oldSyntax`를 지원하지 않습니다.

- Common_type<> 에 대 한 c + + 11 사양에 예기치 않은 결과가 발생 했습니다. 특히 common_type \<int, int> :: type은 int&&을 반환 합니다. 따라서 컴파일러는 라이브러리 작업 그룹 문제 2141에 대 한 제안 된 해결 방법을 구현 합니다. 그러면 common_type \<int, int=""> :: type에서 int를 반환 합니다.

   이러한 변경의 부작용으로 id 대/소문자가 더 이상 작동 하지 않습니다 (common_type \<T> 항상 형식 t가 되지 않음). 이 동작은 제안된 해결 방법을 준수하지만 이전 동작을 사용하는 모든 코드가 중단됩니다.

   ID 형식 특성이 필요한 경우 `std::identity` 에 정의된 비표준 \<type_traits> 는 \<void>에 대해 작동하지 않으므로 사용하지 마세요. 대신 필요에 따라 고유한 ID 형식 특성을 구현합니다. 예를 들면 다음과 같습니다.

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC 및 ATL

- **Visual Studio 2013에만** 해당: 유니코드가 널리 사용 되 고 MBCS의 사용이 크게 거부 되었기 때문에 MFC MBCS 라이브러리는 Visual Studio에 포함 되지 않습니다. 여러 새로운 컨트롤과 메시지가 유니코드 전용이기 때문에 이 변경으로 인해 MFC는 Windows SDK 자체와 보다 밀접한 관계로 유지됩니다. 그러나 MFC MBCS 라이브러리를 계속 사용 해야 하는 경우 [에는 Visual Studio 2013 용 멀티 바이트 Mfc 라이브러리](https://www.microsoft.com/download/details.aspx?id=40770)의 Microsoft 다운로드 센터에서 다운로드할 수 있습니다. Visual C++ 재배포 가능 패키지에는 이 라이브러리가 계속 포함됩니다.  (참고: MBCS DLL은 Visual Studio 2015 이상의 C++ 설치 구성 요소에 포함됩니다).

- MFC 리본에 대한 접근성이 변경되었습니다.  한 수준의 아키텍처 대신 이제 계층적 아키텍처가 있습니다. `CRibbonBar::EnableSingleLevelAccessibilityMode()`를 호출하여 기존 동작을 계속 사용할 수 있습니다.

- `CDatabase::GetConnect` 메서드가 제거되었습니다. 보안을 강화하기 위해 이제 연결 문자열이 암호화되어 저장되고, 필요할 경우에만 해독됩니다. 연결 문자열은 일반 텍스트로 반환될 수 없습니다.  `CDatabase::Dump` 메서드를 사용하여 문자열을 가져올 수 있습니다.

- `CWnd::OnPowerBroadcast`의 서명이 변경되었습니다. 이 메시지 처리기의 서명은 LPARAM을 두 번째 매개 변수로 사용하도록 변경되었습니다.

- 서명이 메시지 처리기를 수용하도록 변경되었습니다. 새로 추가된 ON_WM_* 메시지 처리기를 사용하기 위해 다음과 같은 함수의 매개 변수 목록이 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_DISPLAYCHANGE 매크로를 사용할 수 있도록 `CWnd::OnDisplayChange`가 (WPARAM, LPARAM) 대신 (UINT, int, int)로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_DDE_INITIATE 매크로를 사용할 수 있도록 `CFrameWnd::OnDDEInitiate`가 (WPARAM, LPARAM) 대신 (CWnd*, UINT, UNIT)로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_DDE_EXECUTE 매크로를 사용할 수 있도록 `CFrameWnd::OnDDEExecute`가 (WPARAM, LPARAM) 대신 (CWnd*, HANDLE)로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_DDE_TERMINATE 매크로를 사용할 수 있도록 `CFrameWnd::OnDDETerminate`가 (WPARAM, LPARAM) 대신 (CWnd*)로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_CUT 매크로를 사용할 수 있도록 `CMFCMaskedEdit::OnCut`이 (WPARAM, LPARAM) 대신 매개 변수를 사용하지 않는 함수로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_CLEAR 매크로를 사용할 수 있도록 `CMFCMaskedEdit::OnClear`이 (WPARAM, LPARAM) 대신 매개 변수를 사용하지 않는 함수로 변경되었습니다.

  - 메시지 맵에서 새로운 ON_WM_PASTE 매크로를 사용할 수 있도록 `CMFCMaskedEdit::OnPaste`이 (WPARAM, LPARAM) 대신 매개 변수를 사용하지 않는 함수로 변경되었습니다.

- `#ifdef` 지시문이 MFC 헤더 파일에서 제거되었습니다. 지원되지 않는 Windows 버전(WINVER &lt; 0x0501)과 관련된 여러 `#ifdef` 지시문이 MFC 헤더 파일에서 제거되었습니다.

- ATL DLL(atl120.dll)이 제거되었습니다. 이제 ATL은 헤더와 정적 라이브러리(atls.lib)로 제공됩니다.

- atlsd.lib, atlsn.lib 및 atlsnd.lib가 제거되었습니다. atls.lib에 debug/release와 관련된 문자 집합 종속성이 더 이상 없습니다. atls.lib는 유니코드/ANSI 및 debug/release에 대해 동일하게 작동하기 때문에 한 버전의 라이브러리만 필요합니다.

- ATL DLL과 함께 ATL/MFC 추적 도구가 제거되고 추적 메커니즘이 간소화되었습니다. `CTraceCategory` 생성자는 이제 하나의 매개 변수(범주 이름)를 사용하며, TRACE매크로는 CRT 디버그 보고 함수를 호출합니다.

## <a name="visual-studio-2012-breaking-changes"></a>Visual Studio 2012 호환성이 손상되는 변경

### <a name="compiler"></a>컴파일러

- `/Yl` 컴파일러 옵션이 변경되었습니다. 기본적으로 컴파일러는 이 옵션을 사용하며, 특정 조건에서 LNK2011 오류가 발생할 수 있습니다. 자세한 내용은 [/Yl(디버그 라이브러리에 대한 PCH 참조 삽입)](../build/reference/yl-inject-pch-reference-for-debug-library.md)를 참조하세요.

- 를 사용 하 여 컴파일된 코드에서 `/clr` **`enum`** class 키워드는 CLR (공용 언어 런타임) 열거형이 아닌 c + + 11 열거형을 정의 합니다. CLR 열거형을 정의하려면 해당 접근성에 대해 명시적이어야 합니다.

- 템플릿 키워드를 사용하여 종속 이름(c + + 언어 표준 준수)을 명시적으로 구분할 수 있습니다. 다음 예제에서 강조 표시된 템플릿 키워드는 모호성을 해결하는 데 필요합니다. 자세한 내용은 [종속 형식의 이름 확인](../cpp/name-resolution-for-dependent-types.md)을 참조하세요.

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- 다음 예제와 같이 부동 소수점 형식의 상수 식은 더 이상 템플릿 인수로 허용되지 않습니다.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- 다음 의사 코드 예제와 같이 `/GS` 명령줄 옵션을 사용하여 컴파일되고 off-by-one 취약성이 있는 코드로 인해 런타임 시 프로세스가 종료될 수 있습니다.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- x86 빌드의 기본 아키텍처가 SSE2로 변경되었으므로 컴파일러에서 SSE 명령을 내보낼 수 있으며, XMM 레지스터를 사용하여 부동 소수점 계산을 수행합니다. 이전 동작으로 되돌리려면 `/arch:IA32` 컴파일러 플래그를 사용하여 아키텍처를 IA32로 지정합니다.

- 컴파일러에서 [컴파일러 경고(수준 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) 및 C4701 경고를 실행할 수도 있습니다(이전에 실행하지 않은 경우). 컴파일러는 포인터 형식의 초기화되지 않은 지역 변수 사용에 대해 보다 강력한 검사를 적용합니다.

- 새 링커 플래그 `/HIGHENTROPYVA`가 지정된 경우 Windows 8에서는 일반적으로 메모리 할당 시 64비트 주소가 반환됩니다. Windows 8 이전에는 이러한 할당으로 2gb 미만의 주소가 반환 되는 경우가 많습니다. 이렇게 변경 하면 기존 코드에서 포인터 잘림 버그가 노출 될 수 있습니다. 이 스위치는 기본적으로 켜져 있습니다. 이 동작을 사용하지 않으려면 `/HIGHENTROPYVA:NO`를 지정합니다.

- 관리되는 컴파일러(Visual Basic/C#)는 관리 빌드에 대해서도 `/HIGHENTROPYVA`를 지원합니다.  그러나 이 경우에는 `/HIGHENTROPYVAswitch`가 기본적으로 꺼져 있습니다.

### <a name="ide"></a>IDE

- C++/CLI에서 Windows Forms 애플리케이션을 만들지 않는 것이 좋지만 기존 C++/CLI UI 애플리케이션의 유지 관리는 지원됩니다. Windows Forms 애플리케이션이나 다른 .NET UI 애플리케이션을 만들어야 하는 경우 C# 또는 Visual Basic을 사용합니다. 상호 운용성 목적으로만 C++/CLI를 사용합니다.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>병렬 패턴 라이브러리 및 동시성 런타임 라이브러리

`UmsThreadDefault`의 `SchedulerType` 열거형은 사용되지 않습니다. `UmsThreadDefault`의 사양은 사용되지 않음 경고를 생성하며, 내부적으로 `ThreadScheduler`에 다시 매핑됩니다.

### <a name="standard-library"></a>표준 라이브러리

- C++98/03 및 C++11 표준 간의 주요 변경 내용에 따라 명시적 템플릿 인수를 사용하여 `make_pair()`를 호출하는 경우(예: `make_pair<int, int>(x, y)`) 일반적으로 Visual Studio 2012의 Visual C++에서 컴파일되지 않습니다. 솔루션은 `make_pair()` 에서와 같이 명시적 템플릿 인수 없이 항상를 호출 하는 것입니다 `make_pair(x, y)` . 명시적 템플릿 인수를 제공하면 이 함수의 목적에서 벗어납니다. 결과 형식을 정밀하게 제어해야 하는 경우 `pair<short, short>(int1, int2)`와 같이 `make_pair` 대신 `pair`를 사용합니다.

- C + + 98/03과 c + + 11 표준 간의 또 다른 주요 변경 내용: A가 B로 암시적으로 변환 되 고 B가 암시적으로 C로 변환 될 수 있지만, A는 C, c + + 98/03 및 Visual Studio 2010로 암시적으로 변환할 수 없습니다 `pair<A, X>` (암시적 또는 명시적으로) `pair<C, X>` . 다른 형식 X는 여기에 관심이 없으며 쌍의 첫 번째 형식과 관련이 없습니다. Visual Studio 2012의 c + + 컴파일러는가 C로 암시적으로 변환할 수 없음을 감지 하 고 오버 로드 확인에서 쌍 변환을 제거 합니다. 이 변경은 다양한 시나리오에서 유용합니다. 예를 들어 `func(const pair<int, int>&)` 및 `func(const pair<string, string>&)`을 오버로드하고 `pair<const char *, const char *>`에서 `func()`을 호출하면 이 변경 내용으로 컴파일합니다. 그러나 이 변경으로 인해 적극적인 쌍 변환을 사용한 코드가 손상됩니다. 일반적으로 이러한 코드는 `pair<C, X>`가 필요한 함수에 `make_pair(static_cast<B>(a), x)` 전달 등의 방법으로 변환의 일부를 명시적으로 수행하여 수정할 수 있습니다.

- Visual Studio 2010에서는 전처리기 머신으로 오버로드와 특수화를 제거하여 variadic 템플릿(예: `make_shared<T>(arg1, arg2, argN)`)을 10개 인수 제한까지 시뮬레이트했습니다. Visual Studio 2012에서 이 제한은 5개 인수로 축소되어 대부분의 사용자에 대한 컴파일 시간과 컴파일러 메모리 소비를 개선합니다. 그러나 프로젝트 수준에서 _VARIADIC_MAX를 10으로 명시적으로 정의하여 이전 제한을 설정할 수 있습니다.

- C++11 17.6.4.3.1 [macro.names]/2에서는 C++ 표준 라이브러리 헤더가 포함된 경우 키워드를 매크로로 대체하는 것을 금지합니다. 이제 헤더가 매크로로 대체된 키워드를 검색하면 컴파일러 오류를 내보냅니다. _ALLOW_KEYWORD_MACROS를 정의 하면 이러한 코드를 컴파일할 수 있지만이를 사용 하지 않는 것이 좋습니다. 단, `new` 헤더는를 사용 하 여 자체적으로 스스로 방어 하므로의 매크로 폼은 기본적으로 허용 됩니다 `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")` . _ENFORCE_BAN_OF_MACRO_NEW 정의는 이름이 암시하는 작업을 정확히 수행합니다.

- 다양한 최적화 및 디버깅 검사를 구현하기 위해 C++ 표준 라이브러리는 Visual Studio 버전(2005, 2008, 2010, 2012) 간에 이진 호환성을 의도적으로 중단합니다. C++ 표준 라이브러리가 사용되는 경우 서로 다른 버전을 사용하여 컴파일된 개체 파일 및 정적 라이브러리를 하나의 이진 파일(EXE 또는 DLL)에 혼합할 수 없고, 서로 다른 버전을 사용하여 컴파일된 이진 파일 간에 C++ 표준 라이브러리 개체를 전달할 수 없습니다. 개체 파일과 고정 라이브러리를 혼합(Visual Studio 2010으로 컴파일된 C++ 표준 라이브러리와 Visual Studio 2012의 C++ 컴파일러로 컴파일된 C++ 표준 라이브러리를 함께 사용)하면 _MSC_VER 불일치에 대한 링커 오류가 내보내집니다. 여기서 _MSC_VER은 컴파일러의 주 버전(Visual Studio 2012의 Visual C++의 경우 1700)을 포함하는 매크로입니다. 이 검사에서는 DLL 혼합을 비롯하여 Visual Studio 2008 이전 버전과 관련된 혼합을 검색할 수 없습니다.

- Visual Studio 2012의 C++ 컴파일러는 Visual Studio 2010에서 구현된 _ITERATOR_DEBUG_LEVEL 불일치 검색 외에도 런타임 라이브러리 불일치를 검색합니다. 컴파일러 옵션 `/MT`(정적 릴리스), `/MTd`(정적 디버그), `/MD`(동적 릴리스) 및 `/MDd`(동적 디버그)가 혼합되면 이러한 불일치가 발생합니다.

- `operator<()`, `operator>()`, `operator<=()` 및 `operator>=()`는 이전에 컨테이너의 `std::unordered_map` 및 `stdext::hash_map` 계열에 사용할 수 있었지만 해당 구현이 실제로 유용하지는 않았습니다. Visual Studio 2012의 Visual C++에서는 이러한 비표준 연산자가 제거되었습니다. 또한 `std::unordered_map` 계열에 대한 `operator==()` 및 `operator!=()`의 구현은 `stdext::hash_map` 계열을 포함하도록 확장되었습니다. 새 코드에서는 `stdext::hash_map` 계열을 사용하지 않는 것이 좋습니다.

- C++11 22.4.1.4 [locale.codecvt]는 `codecvt::length()` 및 `codecvt::do_length()`가 수정 가능한 `stateT&` 매개 변수를 사용해야 한다고 지정하지만 Visual Studio 2010는 `const stateT&`를 사용했습니다. Visual Studio 2012의 C++ 컴파일러에서는 표준에 따라 `stateT&`를 사용합니다. 이러한 차이는 가상 함수 `do_length()`를 재정의하려는 사용자에게 중요합니다.

### <a name="crt"></a>CRT

- new 및 malloc()에 사용되는 C 런타임(CRT) 힙은 더 이상 private가 아닙니다. 이제 CRT에서 프로세스 힙을 사용합니다. 즉, DLL이 언로드될 때 힙이 소멸 되지 않으므로 CRT에 정적으로 연결 되는 Dll은 DLL 코드에 의해 할당 된 메모리가 언로드되기 전에 정리 되었는지 확인 해야 합니다.

- `iscsymf()` 함수는 음수 값으로 어설션됩니다.

- `threadlocaleinfostruct` 구조체가 로캘 함수의 변경 내용에 맞게 변경되었습니다.

- 해당하는 내부 형식이 있는 `memxxx()`, `strxxx()` 등의 CRT 함수가 intrin.h에서 제거되었습니다. 이러한 함수 전용으로 intrin.h를 포함한 경우 이제 해당 CRT 헤더를 포함해야 합니다.

### <a name="mfc-and-atl"></a>MFC 및 ATL

- Fusion 지원 (afxcomctl32.h)을 제거 했습니다. 따라서에 정의 된 모든 메서드가 \<afxcomctl32.h> 제거 되었습니다. 헤더 파일 \<afxcomctl32.h> 및 \<afxcomctl32.inl> 가 삭제 되었습니다.

- `CDockablePane::RemoveFromDefaultPaneDividier` 이름이 `CDockablePane::RemoveFromDefaultPaneDivider`로 변경되었습니다.

- `CFileDialog::SetDefExt`의 서명이 LPCTSTR을 사용하도록 변경되었으므로 유니코드 빌드가 영향을 받습니다.

- 사용되지 않는 ATL 추적 범주가 제거되었습니다.

- `CBasePane::MoveWindow`의 서명이 `const CRect`를 사용하도록 변경되었습니다.

- `CMFCEditBrowseCtrl::EnableBrowseButton`의 서명이 변경되었습니다.

- `CMFCBaseTabCtrl`에서 `m_fntTabs` 및 `m_fntTabsBold`가 제거되었습니다.

- 매개 변수를 `CMFCRibbonStatusBarPane` 생성자에 추가했습니다. 기본 매개 변수이므로 소스가 중단되지는 않습니다.

- 매개 변수를 `CMFCRibbonCommandsListBox` 생성자에 추가했습니다. 기본 매개 변수이므로 소스가 중단되지는 않습니다.

- `AFXTrackMouse` API(및 관련 타이머 프로시저)가 제거되었습니다. 대신 Win32 `TrackMouseEvent` API를 사용합니다.

- 매개 변수를 `CFolderPickerDialog` 생성자에 추가했습니다. 기본 매개 변수이므로 소스가 중단되지는 않습니다.

- `CFileStatus` 구조체 크기가 변경됨: `m_attribute` 멤버가 `GetFileAttributes`에서 반환된 값과 일치하도록 BYTE에서 DWORD로 변경되었습니다.

- `CRichEditCtrl` 및 `CRichEditView`가 유니코드 빌드에 RICHEDIT_CLASS(RichEdit 3.0 컨트롤) 대신 MSFTEDIT_CLASS(RichEdit 4.1 컨트롤)를 사용합니다.

- Windows Vista, Windows 7 및 Windows 8에서 항상 TRUE이므로 `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground`가 제거되었습니다.

- Windows Vista, Windows 7 및 Windows 8에서 항상 TRUE이므로 `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable`가 제거되었습니다.

- `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`가 제거되었습니다. Windows Vista, Windows 7 및 Windows 8에서는 Windows API를 직접 호출합니다.

- `AFX_GLOBAL_DATA::DwmDefWindowProc`가 제거되었습니다. Windows Vista, Windows 7 및 Windows 8에서는 Windows API를 직접 호출합니다.

- 이름 충돌을 제거하기 위해 `AFX_GLOBAL_DATA::DwmIsCompositionEnabled`의 이름을 `IsDwmCompositionEnabled`로 바꾸었습니다.

- 많은 MFC 내부 타이머의 식별자가 변경되고 정의가 afxres.h(AFX_TIMER_ID_*)로 이동되었습니다.

- `OnExitSizeMove` 메서드의 서명이 ON_WM_EXITSIZEMOVE 매크로와 일치하도록 변경되었습니다.

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- `OnDWMCompositionChanged`의 이름과 서명이 ON_WM_DWMCOMPOSITIONCHANGED 매크로와 일치하도록 변경되었습니다.

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- `OnMouseLeave` 메서드의 서명이 ON_WM_MOUSELEAVE 매크로와 일치하도록 변경되었습니다.

  - `CMFCCaptionBar`

  - `CMFCColorBar`

  - `CMFCHeaderCtrl`

  - `CMFCProperySheetListBox`

  - `CMFCRibbonBar`

  - `CMFCRibbonPanelMenuBar`

  - `CMFCRibbonRichEditCtrl`

  - `CMFCSpinButtonCtrl`

  - `CMFCToolBar` ReplaceThisText

  - `CMFCToolBarComboBoxEdit`

  - `CMFCToolBarEditCtrl`

  - `CMFCAutoHideBar`

- `OnPowerBroadcast`의 서명이 ON_WM_POWERBROADCAST 매크로와 일치하도록 변경되었습니다.

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

- `OnStyleChanged`의 서명이 ON_WM_STYLECHANGED 매크로와 일치하도록 변경되었습니다.

  - `CMFCListCtrl`

  - `CMFCStatusBar`

- 내부 메서드 `FontFamalyProcFonts`의 이름을 `FontFamilyProcFonts`로 바꾸었습니다.

- 일부 상황에서 메모리 누수를 방지하기 위해 수많은 정적 글로벌 `CString` 개체가 제거되었으며(#defines로 대체), 다음 클래스 멤버 변수가 제거되었습니다.

  - `CKeyBoardManager::m_strDelimiter`

  - `CMFCPropertyGridProperty::m_strFormatChar`

  - `CMFCPropertyGridProperty::m_strFormatShort`

  - `CMFCPropertyGridProperty::m_strFormatLong`

  - `CMFCPropertyGridProperty::m_strFormatUShort`

  - `CMFCPropertyGridProperty::m_strFormatULong`

  - `CMFCPropertyGridProperty::m_strFormatFloat`

  - `CMFCPropertyGridProperty::m_strFormatDouble`

  - `CMFCToolBarImages::m_strPngResType`

  - `CMFCPropertyGridProperty::m_strFormat`

- `CKeyboardManager::ShowAllAccelerators`의 서명이 변경되고 액셀러레이터 구분 기호 매개 변수가 제거되었습니다.

- `CPropertyPage::GetParentSheet`가 추가되었으며, `CPropertyPage` 클래스에서 `GetParent` 대신 이 변수를 호출하여 올바른 부모 시트 창을 가져옵니다. 이 창은 `CPropertyPage`에 대한 부모 또는 최상위 항목일 수 있습니다. `GetParent` 대신 `GetParentSheet`를 호출하도록 코드를 변경해야 할 수도 있습니다.

- ATLBASE.H에서 짝이 맞지 않는 #pragma warning(push)가 수정되었습니다. 이 코드 때문에 경고가 사용되지 않는 오류가 발생했었습니다. 이제 ATLBASE.H가 구문 분석된 후 이러한 경고가 올바르게 사용됩니다.

- D2D 관련 메서드가 AFX_GLOBAL_DATA에서 _AFX_D2D_STATE로 이동되었습니다.

  - `GetDirectD2dFactory`

  - `GetWriteFactory`

  - `GetWICFactory`

  - `InitD2D`

  - `ReleaseD2DRefs`

  - `IsD2DInitialized`

  - `D2D1MakeRotateMatrix`

  - 예를 들어 `afxGlobalData.IsD2DInitialized`를 호출하는 대신 `AfxGetD2DState->IsD2DInitialized`을 호출합니다.

- 사용되지 않는 ATL*.CPP 파일이 \atlmfc\include\ 폴더에서 제거되었습니다.

- `DLLMain` 요구 사항을 충족하기 위해 CRT 초기화 시간 대신 `afxGlobalData` 초기화가 요청 시로 이동되었습니다.

- `RemoveButtonByIndex` 메서드가 `CMFCOutlookBarPane` 클래스에 추가되었습니다.

- `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd`가 `IsFrequentlyUsedCmd`로 수정되었습니다.

- `RestoreOriginalstate`의 여러 인스턴스가 `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`으로 수정되었습니다.

- `CDockablePane`에서 사용되지 않는 메서드가 제거되었습니다. `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo` 및 `CanAdjustLayout`

- `CDockablePane` 정적 멤버 변수 `m_bCaptionText` 및 `m_bHideDisabledButtons`가 제거되었습니다.

- 재정의 `DeleteString` 메서드가 `CMFCFontComboBox`에 추가되었습니다.

- `CPane`에서 사용되지 않는 메서드가 제거되었습니다. `GetMinLength` 및 `IsLastPaneOnLastRow`

- `CPane::GetDockSiteRow(CDockingPanesRow *)`의 이름이 `CPane::SetDockSiteRow`로 바뀌었습니다.

## <a name="visual-studio-2010-breaking-changes"></a>Visual Studio 2010 호환성이 손상되는 변경

### <a name="compiler"></a>컴파일러

- 키워드에는 **`auto`** 새로운 기본 의미가 있습니다. 이전 의미가 거의 사용되지 않았으므로 대부분의 애플리케이션은 이 변경의 영향을 받지 않습니다.

- 새 **`static_assert`** 키워드가 도입 되었습니다 .이 경우 코드에 해당 이름의 식별자가 이미 있는 경우 이름 충돌이 발생 합니다.

- 새 람다 표기법 지원에서 IDL uuid 특성에 따옴표가 없는 GUID를 코딩하기 위한 지원은 제외됩니다.

- .NET Framework 4에서는 프로세스를 복구할 수 없는 손상된 상태가 되게 하는 예외인 손상된 상태 예외 개념이 도입되었습니다. 기본적으로 다른 모든 예외를 catch하는 /EHa 컴파일러 옵션을 사용해도 손상된 상태 예외는 catch할 수 없습니다.                 손상된 상태 예외를 명시적으로 catch하려면 __try-\__except 문을 사용합니다. 또는 [HandledProcessCorruptedStateExceptions] 특성을 적용하여 함수가 손상된 상태 예외를 catch할 수 있게 합니다.  이 변경 내용은 주로 손상된 상태 예외를 catch해야 할 수 있는 시스템 프로그래머에게 영향을 줍니다. 8가지 예외는 STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE입니다.                 이러한 예외에 대한 자세한 내용은 [GetExceptionCode](/windows/win32/Debug/getexceptioncode) 매크로를 참조하세요.

- 수정된 `/GS` 컴파일러 옵션은 이전 버전에 비해 더 포괄적으로 버퍼 오버런으로부터 보호합니다. 이 버전에서는 스택에 추가 보안 검사가 삽입되어 성능이 느려질 수도 있습니다. 새로운 `__declspec(safebuffers)` 키워드를 사용하여 특정 함수에 대한 보안 검사를 삽입하지 않도록 컴파일러에 지시합니다.

- `/GL`(전체 프로그램 최적화) 및 `/clr`(공용 언어 런타임 컴파일) 컴파일러 옵션을 둘 다 사용하여 컴파일하는 경우 `/GL`은 무시됩니다. 이 변경은 컴파일러 옵션 조합 시 혜택이 거의 없기 때문입니다. 이 변경의 결과로 빌드 성능이 향상됩니다.

- 기본적으로 Visual Studio 2010에서는 삼중자 지원이 사용되지 않습니다. 삼중자 지원을 사용하려면 `/Zc:trigraphs` 컴파일러 옵션을 사용합니다. 삼중자는 두 개의 연속 물음표("??")와 고유한 세 번째 문자로 구성됩니다. 컴파일러는 삼중자를 해당 문장 부호 문자로 바꿉니다. 예를 들어 컴파일러는 `??=` 삼중자를 '#' 문자로 바꿉니다. 삼중자는 특정 문장 부호 문자에 대한 편리한 그래픽 표현을 포함하지 않는 문자 집합이 사용되는 C 소스 파일에서 사용합니다.

- 링커가 Windows 98용 최적화를 더 이상 지원하지 않습니다. `/OPT:WIN98` 또는 `/OPT:NOWIN98`을 지정하는 경우 `/OPT`(최적화) 옵션에서 컴파일 시간 오류가 생성됩니다.

- RuntimeLibrary 및 DebugInformationFormat 빌드 시스템 속성으로 지정되는 기본 컴파일러 옵션이 변경되었습니다. 기본적으로 이러한 빌드 속성은 Visual C++ 릴리스 7.0 ~ 10.0에서 생성된 프로젝트에 지정됩니다. Visual C++ 6.0에서 생성된 프로젝트를 마이그레이션하는 경우 이러한 속성 값을 지정할지 여부를 고려합니다.

- Visual Studio 2010에서는 RuntimeLibrary = MultiThreaded(`/MD`) 및 DebugInformationFormat = ProgramDatabase(`/Zi`)입니다. Visual C++ 9.0에서는 RuntimeLibrary = MultiThreaded(`/MT`) 및 DebugInformationFormat = Disabled입니다.

### <a name="clr"></a>CLR

- Microsoft C# 및 Visual Basic 컴파일러에서 이제 no-PIA(no 주 interop 어셈블리)를 생성할 수 있습니다. no-PIA 어셈블리는 관련 PIA(주 interop 어셈블리)를 배포하지 않고 COM 형식을 사용할 수 있습니다. Visual C# 또는 Visual Basic에서 생성된 no-PIA 어셈블리를 사용하는 경우 라이브러리를 사용하는 no-PIA 어셈블리를 참조하기 전에 컴파일 명령에서 PIA 어셈블리를 참조해야 합니다.

### <a name="visual-studio-c-projects-and-msbuild"></a>Visual Studio C++ 프로젝트 및 MSBuild

- 이제 Visual Studio C++ 프로젝트가 MSBuild 도구를 기반으로 합니다. 따라서 프로젝트 파일이 새로운 XML 파일 형식과 .vcxproj 파일 접미사를 사용합니다. Visual Studio 2010에서는 이전 Visual Studio 버전의 프로젝트 파일을 새 파일 형식으로 자동 변환합니다. 이전 빌드 도구인 VCBUILD.exe 또는 프로젝트 파일 접미사 .vcproj를 사용하는 기존 프로젝트에 영향을 줍니다.

- 이전 릴리스에서는 Visual C++가 속성 시트의 런타임 평가를 지원했습니다. 예를 들어 부모 속성 시트가 자식 속성 시트를 가져올 수 있고, 부모가 자식에 정의된 변수를 사용하여 다른 변수를 정의할 수 있었습니다. 런타임 평가를 통해 부모가 자식 속성 시트를 가져오기 전에도 자식 변수를 사용할 수 있었습니다. Visual Studio 2010에서는 MSBuild가 초기 평가만 지원하기 때문에 프로젝트 시트 변수가 정의되기 전에는 사용할 수 없습니다.

### <a name="ide"></a>IDE

- 애플리케이션 종료 대화 상자에서 더 이상 애플리케이션을 종료하지 않습니다. 이전 릴리스에서는 `abort()` 또는 `terminate()` 함수가 애플리케이션의 일반 정품 빌드를 닫을 때 C 런타임 라이브러리가 콘솔 창이나 대화 상자에 애플리케이션 종료 메시지를 표시했습니다. “이 애플리케이션에서 비정상적인 종료를 런타임에 요청했습니다. 자세한 내용은 해당 애플리케이션의 지원 팀에 문의하세요.”라는 메시지가 표시되었습니다. Windows에서 현재 종료 처리기 (일반적으로 Windows 오류 보고 (Dr. Watson) 대화 상자 또는 Visual Studio 디버거)를 표시 하기 때문에 응용 프로그램 종료 메시지가 중복 되었습니다. Visual Studio 2010부터 C 런타임 라이브러리가 메시지를 표시하지 않습니다. 또한 런타임에서 디버거가 시작되기 전에 애플리케이션이 종료되지 않도록 방지합니다. 이는 애플리케이션 종료 메시지의 이전 동작을 사용하는 경우에만 주요 변경 내용입니다.

- 특히 Visual Studio 2010에서는 IntelliSense가 C++/CLI 코드 또는 특성에 대해 작동하지 않고, **모든 참조 찾기** 가 지역 변수에 대해 작동하지 않으며, 코드 모델이 가져온 어셈블리에서 형식 이름을 검색하거나 형식을 정규화된 이름으로 확인하지 않습니다.

### <a name="libraries"></a>라이브러리

- SafeInt 클래스가 Visual C++에 포함되었으며 더 이상 별도 다운로드로 제공되지 않습니다. 이는 "SafeInt"라고도 하는 클래스를 개발한 경우에만 주요 변경 내용입니다.

- 라이브러리 배포 모델은 더 이상 매니페스트를 사용하여 특정 버전의 동적 연결 라이브러리를 찾지 않습니다. 대신, 각 동적 연결 라이브러리의 이름에 해당 버전 번호가 포함되므로 이름을 사용하여 라이브러리를 찾습니다.

- 이전 버전의 Visual Studio에서는 런타임 라이브러리를 다시 빌드할 수 있었습니다. Visual Studio 2010에서는 더 이상 C 런타임 라이브러리 파일의 고유 복사본을 작성할 수 없습니다.

### <a name="standard-library"></a>표준 라이브러리

- \<iterator>헤더는 더 이상 다른 많은 헤더 파일에 의해 자동으로 포함 되지 않습니다. 대신, 헤더에 정의된 독립 실행형 반복기에 대한 지원이 필요한 경우 해당 헤더가 명시적으로 포함됩니다. 이전 빌드 도구인 VCBUILD.exe 또는 프로젝트 파일 접미사인 .vcproj 반복기를 사용하는 기존 프로젝트에 영향을 줍니다.

- 헤더에서는 \<algorithm> checked_ * 및 unchecked_ \* 함수를 제거 합니다. \<iterator>> 헤더에서 `checked_iterator` 클래스가 제거 되 고 `unchecked_array_iterator` 클래스가 추가 되었습니다.

- `CComPtr::CComPtr(int)` 생성자가 제거되었습니다. 해당 생성자는 NULL 매크로에서 `CComPtr` 개체를 생성할 수 있게 해주지만 불필요하고 0이 아닌 정수에서 무의미한 생성을 허용했습니다.

   0으로 정의된 NULL에서는 `CComPtr`을 계속 생성할 수 있지만 리터럴 0이 아닌 정수에서 생성할 경우 실패합니다. **`nullptr`** 대신를 사용 합니다.

- 다음 `ctype` 멤버 함수가 제거되었습니다. `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s` 애플리케이션이 이러한 멤버 함수 중 하나를 사용하는 경우 해당하는 비보안 버전인 `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`으로 대체해야 합니다.

### <a name="crt-mfc-and-atl-libraries"></a>CRT, MFC 및 ATL 라이브러리

- 사용자가 CRT, MFC 및 ATL 라이브러리를 빌드할 수 있게 해주는 지원이 제거되었습니다. 예를 들어 해당하는 NMAKE 파일이 제공되지 않습니다. 그러나 사용자는 이러한 라이브러리에 대한 소스 코드에 계속 액세스할 수 있습니다. 또한 Microsoft에서 이러한 라이브러리를 빌드하는 데 사용하는 MSBuild 옵션을 설명하는 문서가 Visual C++ 팀 블로그에 게시될 예정입니다.

- IA64의 MFC 지원이 제거되었습니다. 그러나 IA64의 CRT 및 ATL 지원은 계속 제공됩니다.

- 서수가 MFC 모듈 정의(.def) 파일에서 더 이상 재사용되지 않습니다. 이 변경으로 인해 부 버전 간에는 서수가 동일하며, 서비스 팩 및 빠른 수정 엔지니어링 릴리스에 대한 이진 호환성이 개선됩니다.

- `CDocTemplate` 클래스에 새 가상 함수가 추가되었습니다. 새 가상 함수는 [CDocTemplate 클래스](../mfc/reference/cdoctemplate-class.md)입니다. 이전 버전의 `OpenDocumentFile`에는 두 개의 매개 변수가 있었습니다. 새 버전에는 세 개의 매개 변수가 있습니다. 다시 시작 관리자를 지원하려면 `CDocTemplate`에서 파생된 모든 클래스가 세 개의 매개 변수가 있는 버전을 구현해야 합니다. 새 매개 변수는 `bAddToMRU`입니다.

### <a name="macros-and-environment-variables"></a>매크로 및 환경 변수

- 환경 변수 __MSVCRT_HEAP_SELECT는 더 이상 지원되지 않습니다. 이 환경 변수가 제거되었으며 대체 항목은 없습니다.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft 매크로 어셈블러 참조

- Microsoft 매크로 어셈블러 참조 컴파일러에서 여러 지시문이 제거되었습니다. 제거된 지시문은 `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087` 및 `.NO87`입니다.

## <a name="visual-studio-2008-breaking-changes"></a>Visual Studio 2008 호환성이 손상되는 변경

### <a name="compiler"></a>컴파일러

- Windows 95, Windows 98, Windows ME 및 Windows NT 플랫폼은 더 이상 지원되지 않습니다. 이러한 운영 체제는 대상 플랫폼 목록에서 제거되었습니다.

- 컴파일러가 ATL 서버와 직접 연결된 여러 특성을 더 이상 지원하지 않습니다. 다음 특성은 더 이상 지원되지 않습니다.

  - perf_counter

  - perf_object

  - perfmon

  - request_handler

  - soap_handler

  - soap_header

  - soap_method

  - tag_name

### <a name="visual-studio-c-projects"></a>Visual Studio C++ 프로젝트

- 이전 버전의 Visual Studio에서 프로젝트를 업그레이드하는 경우 WINVER 및 _WIN32_WINNT 매크로를 0x0500보다 크거나 같도록 수정해야 할 수도 있습니다.

- Visual Studio 2008부터 새 프로젝트 마법사에는 C++ SQL Server 프로젝트를 만드는 옵션이 없습니다. 이전 버전의 Visual Studio를 사용하여 만든 SQL Server 프로젝트는 제대로 컴파일되고 작동합니다.

- Windows API 헤더 파일인 Winable.h가 제거되었습니다. Winuser.h를 대신 포함합니다.

- Windows API 라이브러리인 Rpcndr.lib가 제거되었습니다. 대신 rpcrt4.lib에 연결합니다.

### <a name="crt"></a>CRT

- Windows 95, Windows 98, Windows Millennium Edition 및 Windows NT 4.0에 대한 지원이 제거되었습니다.

- 다음 전역 변수가 제거되었습니다.

  - _osplatform

  - _osver

  - _winmajor

  - _winminor

  - _winver

- 다음 함수가 제거되었습니다. 대신 Windows API 함수 `GetVersion` 또는 `GetVersionEx`를 사용합니다.

  - _get_osplatform

  - _get_osver

  - _get_winmajor

  - _get_winminor

  - _get_winver

- SAL 주석 구문이 변경되었습니다. 자세한 내용은 [SAL 주석](../c-runtime-library/sal-annotations.md)을 참조하세요.

- 이제 IEEE 필터가 SSE 4.1 명령 집합을 지원합니다. 자세한 내용은 [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt를 참조하세요.

- Visual Studio와 함께 제공되는 C 런타임 라이브러리가 더 이상 시스템 DLL msvcrt.dll을 사용하지 않습니다.

### <a name="standard-library"></a>표준 라이브러리

- Windows 95, Windows 98, Windows Millennium Edition 및 Windows NT 4.0에 대한 지원이 제거되었습니다.

- _HAS_ITERATOR_DEBUGGING(Visual Studio 2010 후에는 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)로 대체됨)을 정의하여 디버그 모드에서 컴파일하는 경우 반복기가 기본 컨테이너의 경계를 지나서 증가 또는 감소를 시도하면 이제 애플리케이션이 어설션됩니다.

- 스택 클래스의 멤버 변수 c가 이제 protected로 선언됩니다. 이전에는 이 멤버 변수가 public으로 선언되었습니다.

- `money_get::do_get`의 동작이 변경되었습니다. 이전에는 `frac_digits`에 대해 호출되는 것보다 소수 자릿수가 많은 금액을 구문 분석할 때 `do_get`이 모든 자릿수를 처리했습니다. 이제 `do_get`이 `frac_digits` 문자를 처리한 후에 구문 분석을 중지합니다.

### <a name="atl"></a>ATL

- CRT에 대한 종속성 없이 ATL을 빌드할 수 없습니다. 이전 버전의 Visual Studio에서는 #define ATL_MIN_CRT를 사용하여 ATL 프로젝트의 CRT 종속성을 최소화할 수 있었습니다. Visual Studio 2008에서는 ATL_MIN_CRT 정의 여부에 관계없이 모든 ATL 프로젝트의 CRT 종속성이 최소화됩니다.

- ATL 서버 코드베이스가 CodePlex에 공유 소스 프로젝트로 릴리스되었으며 Visual Studio의 일부로 설치되지 않습니다. atlenc.h의 데이터 인코딩 및 디코딩 클래스와 atlutil.h 및 atlpath.h의 유틸리티 함수 및 클래스는 유지되고 ATL 라이브러리에 포함되었습니다. ATL 서버와 관련된 여러 파일이 더 이상 Visual Studio의 일부로 제공되지 않습니다.

- 일부 함수가 더 이상 DLL에 포함되지 않습니다. 가져오기 라이브러리에는 계속 유지됩니다. 정적으로 함수를 사용하는 코드에는 영향을 주지 않습니다. 이러한 함수를 동적으로 사용하는 코드에만 영향을 줍니다.

- PROP_ENTRY 및 PROP_ENTRY_EX 매크로는 사용되지 않으며 보안상의 이유로 PROP_ENTRY_TYPE 및 PROP_ENTRY_TYPE_EX 매크로로 대체되었습니다.

### <a name="atlmfc-shared-classes"></a>ATL/MFC 공유 클래스

- CRT에 대한 종속성 없이 ATL을 빌드할 수 없습니다. 이전 버전의 Visual Studio에서는 `#define ATL_MIN_CRT`를 사용하여 ATL 프로젝트의 CRT 종속성을 최소화할 수 있었습니다. Visual Studio 2008에서는 ATL_MIN_CRT 정의 여부에 관계없이 모든 ATL 프로젝트의 CRT 종속성이 최소화됩니다.

- ATL 서버 코드베이스가 CodePlex에 공유 소스 프로젝트로 릴리스되었으며 Visual Studio의 일부로 설치되지 않습니다. atlenc.h의 데이터 인코딩 및 디코딩 클래스와 atlutil.h 및 atlpath.h의 유틸리티 함수 및 클래스는 유지되고 ATL 라이브러리에 포함되었습니다. ATL 서버와 관련된 여러 파일이 더 이상 Visual Studio의 일부로 제공되지 않습니다.

- 일부 함수가 더 이상 DLL에 포함되지 않습니다. 가져오기 라이브러리에는 계속 유지됩니다. 정적으로 함수를 사용하는 코드에는 영향을 주지 않습니다. 이러한 함수를 동적으로 사용하는 코드에만 영향을 줍니다.

### <a name="mfc"></a>MFC

- `CTime` 클래스: 이제 `CTime` 클래스가 1970/1/1 C.E 대신 1900/1/1 C.E부터 날짜를 허용합니다.

- MFC 대화 상자의 컨트롤 탭 순서: MFC ActiveX 컨트롤이 탭 순서에 삽입된 경우 MFC 대화 상자에 있는 여러 컨트롤의 올바른 탭 순서를 방해합니다. 이 변경은 해당 문제를 해결합니다.

   예를 들어 ActiveX 컨트롤 및 여러 개의 편집 컨트롤이 들어 있는 MFC 대화 상자 애플리케이션을 만듭니다. 편집 컨트롤의 탭 순서 중간에 ActiveX 컨트롤을 배치합니다. 응용 프로그램을 시작 하 고 탭 순서가 ActiveX 컨트롤 뒤에 있는 편집 컨트롤을 클릭 한 다음 tab 키를 누릅니다. 이러한 변경 전에 포커스가 탭 순서에서 다음 편집 컨트롤 대신 ActiveX 컨트롤 뒤에 있는 편집 컨트롤로 이동 했습니다.

- `CFileDialog` 클래스: 클래스의 사용자 지정 템플릿은 `CFileDialog` 자동으로 Windows Vista로 이식할 수 없습니다. 여전히 사용할 수는 있지만 Windows Vista 스타일 대화 상자의 추가 기능이나 모양은 제공되지 않습니다.

- `CWnd` 클래스 및 `CFrameWnd` 클래스: `CWnd::GetMenuBarInfo` 메서드가 제거되었습니다.

   `CFrameWnd::GetMenuBarInfo` 메서드는 이제 비가상 메서드입니다. 자세한 내용은 Windows SDK의 **GetMenuBarInfo 함수** 를 참조하세요.

- MFC ISAPI 지원: MFC에서 ISAPI(Internet Server Application Programming Interface)를 사용한 애플리케이션 빌드를 더 이상 지원하지 않습니다. ISAPI 애플리케이션을 빌드하려는 경우 ISAPI 확장을 직접 호출합니다.

- 사용되지 않는 ANSI API: 여러 MFC 메서드의 ANSI 버전이 사용되지 않습니다. 이후 애플리케이션에서는 해당 메서드의 유니코드 버전을 사용합니다. 자세한 내용은 **Windows Vista 공용 컨트롤의 빌드 요구 사항** 을 참조하세요.

## <a name="visual-studio-2005-breaking-changes"></a>Visual Studio 2005 호환성이 손상되는 변경

### <a name="crt"></a>CRT

- 많은 함수가 사용되지 않습니다. **사용되지 않는 CRT 함수** 를 참조하세요.

- 이제 많은 함수가 매개 변수의 유효성을 검사하며, 잘못된 매개 변수가 제공될 경우 실행을 중지합니다. 이 유효성 검사로 인해 잘못된 매개 변수를 전달하며, 함수가 해당 매개 변수를 무시하거나 단순히 오류 코드를 반환해야 하는 코드가 중단될 수 있습니다. **매개 변수 유효성 검사** 를 참조하세요.

- 이제 파일 설명자 값 -2를 사용하여 `stdout` 및 `stderr`을 출력에 사용할 수 없음을 나타냅니다(예: 콘솔 창이 없는 Windows 애플리케이션의 경우). 이전에는 값 -1을 사용했습니다. 자세한 내용은 [_fileno](../c-runtime-library/reference/fileno.md)를 참조하세요.

- 단일 스레드 CRT 라이브러리(libc.lib 및 libcd.lib)가 제거되었습니다. 다중 스레드 CRT 라이브러리를 사용합니다. `/ML` 컴파일러 플래그가 더 이상 지원되지 않습니다. 다중 스레드 코드와 단일 스레드 코드 간의 성능 차이가 잠재적으로 중요한 경우를 위해 일부 함수의 비잠금 버전이 추가되었습니다.

- pow 오버로드인 double pow(int, int)가 표준 준수를 개선하기 위해 제거되었습니다.

- 본질적으로 안전하지 않은 %n 형식 지정자는 함수의 printf 계열에서 더 이상 기본적으로 지원되지 않습니다. %n이 발견된 경우 기본 동작은 잘못된 매개 변수 처리기를 호출하는 것입니다. %n 지원을 설정하려면 `_set_printf_count_output`을 사용합니다(`_get_printf_count_output` 참조).

- 이제 `sprintf`가 signed 0의 음수 기호를 인쇄합니다.

- `swprintf`가 표준을 준수하도록 변경되었습니다. 이제 size 매개 변수가 필요합니다. size 매개 변수가 없는 `swprintf` 형태는 사용되지 않습니다.

- `_set_security_error_handler` 는 제거되었습니다. 해당 함수에 대한 호출을 모두 제거합니다. 기본 처리기가 보안 오류를 처리하는 훨씬 안전한 방법입니다.

- 이제 `time_t`가 64비트 값입니다(_USE_32BIT_TIME_T가 정의되지 않은 경우).

- 이제 `_spawn`, `_wspawn` 함수가 C Standard에 지정된 대로 성공 시 `errno`를 그대로 유지합니다.

- 이제 RTC가 기본적으로 와이드 문자를 사용합니다.

- 부동 소수점 제어 단어 지원 함수가 `/CLR` 또는 `/CLR:PURE`로 컴파일된 애플리케이션에서 사용되지 않습니다. 영향을 받는 함수는 `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87`, `_statusfp`입니다. _CRT_MANAGED_FP_NO_DEPRECATE를 정의하여 사용 중단 경고를 해제할 수 있지만 관리 코드에서 이러한 함수의 사용은 예측하기 어렵고 지원되지 않습니다.

- 이제 일부 함수가 const 포인터를 반환합니다. _CONST_RETURN을 정의하면 이전의 비 const 동작을 복구할 수 있습니다. 영향을 받는 함수는 다음과 같습니다.

  - memchr, wmemchr

  - strchr, wcschr, _mbschr, _mbschr_l

  - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

  - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

  - strstr, wcsstr, _mbsstr, _mbsstr_l

- Setargv.obj 또는 Wsetargv.obj에 연결하는 경우 더 이상 명령줄에서 와일드카드 문자를 큰따옴표로 묶어 확장을 억제할 수 없습니다. 자세한 내용은 [와일드카드 인수 확장](../c-language/expanding-wildcard-arguments.md)을 참조하세요.

### <a name="standard-library-2005"></a>표준 라이브러리(2005)

- 헤더에 있는 예외 클래스는 \<exception> `std` 네임 스페이스로 이동 되었습니다. 이전 버전에서는 이 클래스가 전역 네임스페이스에 있었습니다. 예외 클래스를 찾을 수 없다는 오류를 해결하려면 다음 using 문을 코드에 추가합니다. `using namespace std;`

- `valarray::resize()`를 호출하는 경우 `valarray`의 내용이 손실되고 기본값으로 대체됩니다. `resize()` 메서드는 벡터처럼 동적으로 확장하는 대신 `valarray`를 다시 초기화합니다.

- 디버그 반복기: C 런타임 라이브러리의 디버그 버전으로 빌드된 애플리케이션이 반복기를 잘못 사용하는 경우 런타임에 어설션이 표시될 수 있습니다. 이러한 어설션을 사용하지 않으려면 _HAS_ITERATOR_DEBUGGING(Visual Studio 2010 후에는 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)로 대체됨)을 0으로 정의해야 합니다. 자세한 내용은 [디버그 반복기 지원](../standard-library/debug-iterator-support.md)을 참조하세요.

## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003의 주요 변경 내용

### <a name="compiler"></a>컴파일러

- 이제 정의된 전처리기 지시문(C2004)에 닫는 괄호가 필요합니다.

- 명시적 특수화가 더 이상 기본 템플릿에서 템플릿 매개 변수를 찾지 않습니다([컴파일러 오류 C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- 보호된 멤버(n)는 (n)이 속하는 클래스(A)에서 상속하는 클래스(B)의 멤버 함수를 통해서만 액세스할 수 있습니다([컴파일러 오류 C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- 이제 컴파일러의 향상된 접근성 검사에서 액세스할 수 없는 기본 클래스가 검색됩니다([컴파일러 오류 C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- 소멸자로 및/또는 복사 생성자에 액세스할 수 없는 경우 예외를 catch할 수 없습니다(C2316).

- 함수에 대한 포인터의 기본 인수가 더 이상 허용되지 않습니다([컴파일러 오류 C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- 파생 클래스를 통해 정적 데이터 멤버를 초기화할 수 없습니다([컴파일러 오류 C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- 의 초기화는 **`typedef`** 표준에서 허용 되지 않으며 이제 컴파일러 오류 ( [컴파일러 오류 C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md))를 생성 합니다.

- **`bool`** 는 이제 적절 한 형식 ( [컴파일러 오류 C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md))입니다.

- 이제 UDC가 오버로드된 연산자로 모호성을 만들 수 있습니다([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- 이제 더 많은 식이 유효한 null 포인터 상수로 간주됩니다([컴파일러 오류 C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- 이전에는 컴파일러에서 암시되었을 위치에 이제 template<>이 필요합니다([컴파일러 오류 C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- 함수가 이미 템플릿 클래스 특수화를 통해 명시적으로 특수화된 경우 클래스 외부에서 멤버 함수의 명시적 특수화는 유효하지 않습니다([컴파일러 오류 C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- 부동 소수점 비형식 템플릿 매개 변수가 더 이상 허용되지 않습니다([컴파일러 오류 C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- 클래스 템플릿을 템플릿 형식 인수로 허용하지 않습니다(C3206).

- 친숙한 함수 이름이 포함하는 네임스페이스에 더 이상 도입되지 않습니다([컴파일러 오류 C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- 컴파일러에서 매크로의 추가 쉼표를 더 이상 허용하지 않습니다(C4002).

- form()의 이니셜라이저로 생성된 POD 형식의 개체가 기본값으로 초기화됩니다(C4345).

- 이제 종속 이름이 형식으로 처리되어야 하는 경우 typename이 필요합니다([컴파일러 경고(수준 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- 템플릿 특수화로 잘못 간주된 함수가 더 이상 그렇게 간주되지 않습니다(C4347).

- 파생 클래스를 통해 정적 데이터 멤버를 초기화할 수 없습니다(C4356).

- 클래스 템플릿 특수화가 반환 형식에 사용되기 전에 정의해야 합니다([컴파일러 경고(수준 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- 이제 컴파일러에서 연결할 수 없는 코드를 보고합니다(C4702).

## <a name="see-also"></a>참조

[새로워진 Visual Studio의 Visual C++ 기능](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
