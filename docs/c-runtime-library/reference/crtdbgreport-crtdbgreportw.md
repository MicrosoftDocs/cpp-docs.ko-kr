---
description: '자세히 알아보기: _CrtDbgReport, _CrtDbgReportW'
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 523dc65f846804b13b83bf08b0499b2459fe22ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319806"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

디버깅 메시지가 포함된 보고서를 생성하고 이 보고서를 가능한 대상 3개로 보냅니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 유형: **_CRT_WARN**, **_CRT_ERROR** 및 **_CRT_ASSERT** 합니다.

*filename*<br/>
어설션/보고서가 발생 하거나 **NULL 인** 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
어설션/보고서가 발생 하거나 **NULL 인** 소스 파일의 줄 번호입니다.

*moduleName*<br/>
어설션 또는 보고서가 발생한 모듈(.exe 또는 .dll)의 이름에 대한 포인터입니다.

*format*<br/>
사용자 메시지를 만드는 데 사용되는 형식 컨트롤 문자열에 대한 포인터입니다.

*argument*<br/>
*형식* 에서 사용 하는 선택적 대체 인수입니다.

## <a name="return-value"></a>반환 값

모든 보고서 대상에 대해 **_CrtDbgReport** 및 **_CrtDbgReportW** 오류가 발생 하면-1을 반환 하 고 오류가 발생 하지 않으면 0을 반환 합니다. 그러나 보고서 대상이 디버그 메시지 창이고 사용자가 **다시 시도** 단추를 클릭하면 이러한 함수는 1을 반환합니다. 사용자가 디버그 메시지 창에서 **중단** 단추를 클릭하면 이러한 함수가 즉시 중단되고 값을 반환하지 않습니다.

_RPT 디버그 매크로 [_RPTF](rpt-rptf-rptw-rptfw-macros.md) **_CrtDbgReport** 호출 하 여 디버그 보고서를 생성 합니다. 이러한 매크로의 와이드 문자 버전 뿐만 아니라 [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) 및 [_RPTFW](rpt-rptf-rptw-rptfw-macros.md)는 **_CrtDbgReportW** 를 사용 하 여 디버그 보고서를 생성 합니다. JIT (just-in-time) 디버깅을 사용 하도록 설정 된 경우 **_CrtDbgReport** 또는 **_CrtDbgReportW** 1을 반환 하면 이러한 매크로는 디버거를 시작 합니다.

## <a name="remarks"></a>설명

**_CrtDbgReport** 및 **_CrtDbgReportW** 는 디버그 보고서 파일, 디버그 모니터 (Visual Studio 디버거) 또는 디버그 메시지 창과 같은 세 가지 대상으로 디버그 보고서를 보낼 수 있습니다. 두 구성 함수인 [_CrtSetReportMode](crtsetreportmode.md)와 [_CrtSetReportFile](crtsetreportfile.md)은 각 보고서 형식의 대상을 지정하는 데 사용됩니다. 이러한 함수를 사용하면 각 보고서 형식의 보고 대상을 개별적으로 제어할 수 있습니다. 예를 들어 **_CRT_WARN** 의 *reportType* 를 디버그 모니터로만 보내도록 지정 하 고, *reportType* **_CRT_ASSERT** 를 디버그 메시지 창과 사용자 정의 보고서 파일로 보낼 수 있습니다.

**_CrtDbgReportW** 은 **_CrtDbgReport** 의 와이드 문자 버전입니다. 이 함수의 모든 출력 및 문자열 매개 변수는 와이드 문자열에 있습니다. 이 점을 제외하면 이 함수는 싱글바이트 문자 버전과 동일합니다.

**_CrtDbgReport** 및 **_CrtDbgReportW** **printf** 또는 **wprintf** 함수에서 정의한 동일한 규칙을 사용 하 여 *인수*[**n**] 인수를 *형식* 문자열로 대체 하 여 디버그 보고서에 대 한 사용자 메시지를 만듭니다. 그런 다음 이러한 함수는 디버그 보고서를 생성 하 고 *reportType* 에 대해 정의 된 현재 보고서 모드 및 파일을 기반으로 대상을 결정 합니다. 보고서를 디버그 메시지 창으로 보내면 *파일 이름*, **lineNumber** 및 *moduleName* 이 창에 표시 되는 정보에 포함 됩니다.

다음 표에서는 보고서 모드 또는 모드와 파일 및 **_CrtDbgReport** 및 **_CrtDbgReportW** 의 결과 동작에 사용할 수 있는 선택 항목을 보여 줍니다. 이러한 옵션은에서 비트 플래그로 정의 됩니다 \<crtdbg.h> .

|보고서 모드|보고서 파일|**_CrtDbgReport**, **_CrtDbgReportW** 동작|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|해당 없음|Windows [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) API를 사용하여 메시지를 작성합니다.|
|**_CRTDBG_MODE_WNDW**|해당 없음|Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) API를 호출하여 **중단**, **다시 시도** 및 **무시** 단추와 함께 메시지를 표시하는 메시지 상자를 만듭니다. 사용자가 **중단** 을 클릭 하면 **_CrtDbgReport** 또는 **_CrtDbgReport** 즉시 중단 됩니다. 사용자가 **다시 시도** 를 클릭하면 1이 반환됩니다. 사용자가 **무시** 를 클릭 하면 실행이 계속 되 고 **_CrtDbgReport** **_CrtDbgReportW** 0이 반환 됩니다. 오류 조건이 있을 때 **무시** 를 클릭하면 종종 "정의되지 않은 동작"이 발생할 수 있습니다.|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) API를 사용 하 여 사용자 제공 **핸들** 에 메시지를 쓰고 파일 핸들의 유효성을 확인 하지 않습니다. 응용 프로그램은 보고서 파일을 열고 유효한 파일 핸들을 전달 하는 일을 담당 합니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|**Stderr** 에 메시지를 씁니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|**Stdout** 에 메시지를 씁니다.|

보고서는 1개, 2개 또는 3개 대상으로 보내거나 아무 대상으로도 보내지 않을 수 있습니다. 보고서 모드 및 보고서 파일을 지정하는 방법에 대한 자세한 내용은 [_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수를 참조하세요. 디버그 매크로 및 보고 함수 사용에 대한 자세한 내용은 [보고서 매크로](/visualstudio/debugger/macros-for-reporting)를 참조하세요.

응용 프로그램에 **_CrtDbgReport** 및 **_CrtDbgReportW** 에서 제공 하는 것 보다 더 많은 유연성이 필요한 경우에는 [_CrtSetReportHook](crtsetreporthook.md) 함수를 사용 하 여 사용자 고유의 보고 함수를 작성 하 고 C 런타임 라이브러리 보고 메커니즘에 후크 할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** 및 **_CrtDbgReportW** 는 Microsoft 확장입니다. 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

보고 함수 변경 방법의 예는 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)를 참조하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
