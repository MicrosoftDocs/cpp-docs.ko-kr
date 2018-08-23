---
title: _CrtDbgReport, _CrtDbgReportW | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
apilocation:
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
apitype: DLLExport
f1_keywords:
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2b0bcdc5ee6c4c2b71837f1cdd958f50d8d0b4a
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42572893"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

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
보고서 형식: **_CRT_WARN**를 **_CRT_ERROR**, 및 **_CRT_ASSERT**합니다.

*filename*<br/>
어설션/보고서가 발생 한 소스 파일의 이름에 대 한 포인터 또는 **NULL**합니다.

*linenumber*<br/>
어설션/보고서가 발생 한 소스 파일의 줄 번호 또는 **NULL**합니다.

*moduleName*<br/>
어설션 또는 보고서가 발생한 모듈(.exe 또는 .dll)의 이름에 대한 포인터입니다.

*format*<br/>
사용자 메시지를 만드는 데 사용되는 형식 컨트롤 문자열에 대한 포인터입니다.

*argument*<br/>
사용 되는 선택적 대체 인수 *형식*합니다.

## <a name="return-value"></a>반환 값

모든 보고서 대상에 대해 **_CrtDbgReport** 하 고 **_CrtDbgReportW** 오류가 발생 하는 경우 오류가 발생 하면-1과 0을 반환 합니다. 그러나 보고서 대상이 디버그 메시지 창이고 사용자가 **다시 시도** 단추를 클릭하면 이러한 함수는 1을 반환합니다. 사용자가 디버그 메시지 창에서 **중단** 단추를 클릭하면 이러한 함수가 즉시 중단되고 값을 반환하지 않습니다.

합니다 [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) 매크로 호출을 디버그 **_CrtDbgReport** 디버그를 생성 하려면 보고 합니다. 이러한 매크로의 와이드 문자 버전 뿐만 [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md)를 [_RPTW](rpt-rptf-rptw-rptfw-macros.md) 하 고 [_RPTFW](rpt-rptf-rptw-rptfw-macros.md)를 사용 하 여 **_CrtDbgReportW** 를 디버그 보고서를 생성 합니다. 때 **_CrtDbgReport** 하거나 **_CrtDbgReportW** 1을 반환 이러한 매크로 시간 (JIT) 디버깅을 사용 하는 디버거를 시작 합니다.

## <a name="remarks"></a>설명

**_CrtDbgReport** 하 고 **_CrtDbgReportW** 를 다른 대상 3 개로 디버그 보고서를 보낼 수 있습니다: 디버그 보고서 파일, 디버그 모니터 (Visual Studio 디버거) 또는 디버그 메시지 창. 두 구성 함수인 [_CrtSetReportMode](crtsetreportmode.md)와 [_CrtSetReportFile](crtsetreportfile.md)은 각 보고서 형식의 대상을 지정하는 데 사용됩니다. 이러한 함수를 사용하면 각 보고서 형식의 보고 대상을 개별적으로 제어할 수 있습니다. 지정할 수는 예를 들어, 한 *reportType* 의 **_CRT_WARN** 만 디버그 모니터를 전송 하는 동안를 *reportType* 의 **_CRT_ASSERT** 디버그 메시지 창이 고 사용자 정의 보고서 파일로 보낼 수 있습니다.

**_CrtDbgReportW** 의 와이드 문자 버전이 **_CrtDbgReport**합니다. 이 함수의 모든 출력 및 문자열 매개 변수는 와이드 문자열에 있습니다. 이 점을 제외하면 이 함수는 싱글바이트 문자 버전과 동일합니다.

**_CrtDbgReport** 하 고 **_CrtDbgReportW** 대체 하 여 디버그 보고서에 대 한 사용자 메시지를 만듭니다를 *인수*[**n**] 인수를 를*형식* 문자열를 정의한 동일한 규칙을 사용 하는 **printf** 하거나 **wprintf** 함수. 파일에 대 한 정의 및 이러한 함수에서 다음 디버그 보고서를 생성 하 고 대상을, 현재 보고서 모드에 따라 결정 *reportType*합니다. 디버그 메시지 창에 보고서를 보낼 때 합니다 *filename*를 **lineNumber**, 및 *moduleName* 창에 표시 되는 정보에 포함 됩니다.

다음 표에서 보고서 모드 및 파일 및 결과 동작에 대 한 사용 가능한 선택 항목을 나열 **_CrtDbgReport** 하 고 **_CrtDbgReportW**합니다. 이러한 옵션은 \<crtdbg.h>에서 비트 플래그로 정의되어 있습니다.

|보고서 모드|보고서 파일|**_CrtDbgReport**하십시오 **_CrtDbgReportW** 동작|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|적용할 수 없음|Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) API를 사용하여 메시지를 작성합니다.|
|**_CRTDBG_MODE_WNDW**|적용할 수 없음|Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) API를 호출하여 **중단**, **다시 시도** 및 **무시** 단추와 함께 메시지를 표시하는 메시지 상자를 만듭니다. 사용자가 **중단**를 **_CrtDbgReport** 하거나 **_CrtDbgReport** 즉시 중단 합니다. 사용자가 **다시 시도**를 클릭하면 1이 반환됩니다. 사용자가 **무시**, 실행이 계속 됩니다 및 **_CrtDbgReport** 하 고 **_CrtDbgReportW** 0을 반환 합니다. 오류 조건이 있을 때 **무시**를 클릭하면 종종 "정의되지 않은 동작"이 발생할 수 있습니다.|
|**_CRTDBG_MODE_FILE**|**__HFILE**|사용자 제공 메시지를 작성 **처리할**에 Windows를 사용 하 여 [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) API 및 파일 핸들의 유효성을 검사 하지 않으면 응용 프로그램은 보고서 파일 열기 및 유효한 파일을 전달 하는 일을 담당 핸들입니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|메시지를 작성 **stderr**합니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|메시지를 작성 **stdout**합니다.|

보고서는 1개, 2개 또는 3개 대상으로 보내거나 아무 대상으로도 보내지 않을 수 있습니다. 보고서 모드 및 보고서 파일을 지정하는 방법에 대한 자세한 내용은 [_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수를 참조하세요. 디버그 매크로 및 보고 함수 사용에 대한 자세한 내용은 [보고서 매크로](/visualstudio/debugger/macros-for-reporting)를 참조하세요.

응용 프로그램에서 제공 된 것 보다 더 뛰어난 유연성이 필요한 경우 **_CrtDbgReport** 하 고 **_CrtDbgReportW**, 고유한 보고 함수를 작성 하 고 C 런타임 라이브러리 보고 연결 수 사용 하 여 메커니즘 합니다 [_CrtSetReportHook](crtsetreporthook.md) 함수입니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** 하 고 **_CrtDbgReportW** 는 Microsoft 확장입니다. 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예

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

## <a name="see-also"></a>참고자료

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
