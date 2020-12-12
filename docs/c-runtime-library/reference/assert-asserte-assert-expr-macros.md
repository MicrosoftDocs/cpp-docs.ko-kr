---
description: _ASSERT, _ASSERTE, _ASSERT_EXPR 매크로에 대해 자세히 알아보세요.
title: _ASSERT, _ASSERTE, _ASSERT_EXPR 매크로
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: 28c90d2c92feb298b2416633e783c5d0a87e4bd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117577"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR 매크로

식을 계산 하 고 결과가 **False** 인 경우 디버그 보고서를 생성 합니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
0이 아닌 값(true) 또는 0(false)으로 계산되는 스칼라 식(포인터 식 포함)입니다.

*message*<br/>
보고서 일부로 표시할 전각 문자열입니다.

## <a name="remarks"></a>설명

**_ASSERT_EXPR**, **_ASSERT** 및 **_ASSERTE** 매크로를 사용 하 여 디버깅 프로세스 중 가정을 확인 하는 데 필요한 깔끔하고 간단한 메커니즘을 응용 프로그램에 제공 합니다. 이들 매크로는 애플리케이션의 정품 빌드 시 호출되지 않도록 `#ifdef` 문에 포함할 필요가 없으므로 매우 유연합니다. 이 유연성을 얻으려면 [_DEBUG](../../c-runtime-library/debug.md) 매크로를 사용합니다. **_ASSERT_EXPR**, **_ASSERT** 및 **_ASSERTE** 는 컴파일 시간에 **_DEBUG** 정의 된 경우에만 사용할 수 있습니다. **_DEBUG** 정의 되지 않은 경우 전처리 중에 이러한 매크로에 대 한 호출이 제거 됩니다.

*BooleanExpression* 인수를 **_ASSERT** 및 **_ASSERTE** 평가 하 고 결과가  **`false`** (0) 이면 진단 메시지를 인쇄 하 고 [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 를 호출 하 여 디버그 보고서를 생성 합니다. _ASSERT_EXPR **_ASSERT** 매크로는 간단한 진단 메시지를 출력 하 고, 메시지에 실패 한 식의 문자열 표현을 포함 하 고, **_ASSERT_EXPR** 는 메시지 *문자열을* 진단 메시지에 포함 **_ASSERTE** 합니다. *BooleanExpression* 가 0이 아닌 값으로 계산 되 면 이러한 매크로는 아무 작업도 수행 하지 않습니다.

**_ASSERT_EXPR**, **_ASSERT** 및 **_ASSERTE** 를 **_CrtDbgReportW** 호출 하면 모든 출력이 와이드 문자로 됩니다. **_ASSERTE** *booleanExpression* 에서 유니코드 문자를 올바르게 인쇄 하 고 *메시지* 에 유니코드 문자를 인쇄 **_ASSERT_EXPR** 합니다.

**_ASSERTE** 매크로는 실패 한 식을 지정 하 고 **_ASSERT_EXPR** 를 사용 하 여 생성 된 보고서에 메시지를 지정할 수 있으므로 사용자는 응용 프로그램 소스 코드를 참조 하지 않고 문제를 식별할 수 있습니다. 그러나 **_ASSERT_EXPR** 에서 인쇄 되는 모든 *메시지* 와 **_ASSERTE** 에 의해 평가 되는 모든 식은 응용 프로그램의 출력 (디버그 버전) 파일에 문자열 상수로 포함 된다는 단점이 있습니다. 따라서 **_ASSERT_EXPR** 또는 **_ASSERTE** 에 대해 많은 수의 호출을 수행 하는 경우 이러한 식은 출력 파일의 크기를 크게 늘릴 수 있습니다.

[_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수를 사용해서 지정하지 않으면 메시지가 설정에 해당하는 팝업 대화 상자에 표시됩니다.

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** 는 디버그 보고서를 생성 하 고 현재 보고서 모드 또는 **_CRT_ASSERT** 보고서 형식에 대해 정의 된 모드 및 파일을 기반으로 대상을 결정 합니다. 기본적으로 어설션 실패 및 오류는 디버그 메시지 창에 전달됩니다. [_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수는 각 보고서 종류의 대상을 정의하는 데 사용됩니다.

대상이 디버그 메시지 창이 고 사용자가 **다시 시도** 단추를 클릭 하면 **_CrtDbgReportW** 1을 반환 하 여 JIT (just-in-time) 디버깅을 사용 하도록 설정 된 경우 **_ASSERT_EXPR**, **_ASSERT** 및 **_ASSERTE** 매크로를 사용 하 여 디버거를 시작 합니다.

보고 프로세스에 대한 자세한 내용은 [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 함수를 참조하세요. 어설션 실패를 해결하고 이들 매크로를 디버깅 오류 처리 메커니즘으로 사용하는 방법에 대한 자세한 내용은 [확인 및 보고에 매크로 사용](/visualstudio/debugger/macros-for-reporting)을 참조하세요.

**_ASSERT** 매크로 외에도 [ASSERT](assert-macro-assert-wassert.md) 매크로를 사용 하 여 프로그램 논리를 확인할 수 있습니다. 이 매크로는 라이브러리의 디버그 및 릴리스 버전에서 둘 다 사용할 수 있습니다. [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) 디버그 매크로는 디버그 보고서 생성에도 사용할 수 있지만 식을 계산하지 않습니다. **_RPT** 매크로는 간단한 보고서를 생성 합니다. **_RPTF** 매크로에는 생성 된 보고서에서 보고서 매크로가 호출 된 소스 파일과 줄 번호가 포함 되어 있습니다. 이러한 매크로의 와이드 문자 버전을 사용할 수 있습니다 (**_RPTW**, **_RPTFW**). 와이드 문자 문자열이 모든 문자열 매개 변수 및 출력에 사용된다는 점을 제외하고 와이드 문자 버전은 반각 문자 버전과 똑같습니다.

**_ASSERT_EXPR** **_ASSERT** 및 **_ASSERTE** 는 매크로 이며를 포함 하 여 사용할 수 있지만 \<crtdbg.h> , 이러한 매크로는 다른 런타임 함수를 호출 하므로 **_DEBUG** 정의 될 때 응용 프로그램은 C 런타임 라이브러리의 디버그 버전과 연결 해야 합니다.

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>예제

이 프로그램에서는 **_ASSERT** 및 **_ASSERTE** 매크로를 호출 하 여 조건을 테스트 `string1 == string2` 합니다. 조건이 실패하면 이들 매크로가 진단 메시지를 출력합니다. 이 프로그램에서는 매크로의 **_RPT** 및 **_RPTF** 그룹도 **printf** 함수 대신 실행 됩니다.

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[assert 매크로, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW 매크로](rpt-rptf-rptw-rptfw-macros.md)<br/>
