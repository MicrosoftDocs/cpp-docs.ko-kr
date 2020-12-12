---
description: _RPT, _RPTF, _RPTW, _RPTFW 매크로에 대해 자세히 알아보세요.
title: _RPT, _RPTF, _RPTW, _RPTFW 매크로
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 6cc20032454002b33b4f3d297db582af09c90805
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341440"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW 매크로

디버그 보고서를 생성하여 애플리케이션의 진행률을 추적합니다(디버그 버전에만 해당함). *N* 은 *args* 의 인수 수를 지정 하며 0, 1, 2, 3, 4 또는 5 일 수 있습니다.

## <a name="syntax"></a>구문

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 유형: **_CRT_WARN**, **_CRT_ERROR** 또는 **_CRT_ASSERT**.

*format*<br/>
사용자 메시지를 만드는 데 사용되는 형식 제어 문자열입니다.

*args*<br/>
*형식* 에서 사용 하는 대체 인수입니다.

## <a name="remarks"></a>설명

이러한 모든 매크로는 *reportType* 및 *format* 매개 변수를 사용 합니다. 또한 매크로 이름에 추가된 번호로 표시되는 추가 인수도 4개까지 사용할 수 있습니다. 예를 들어 **_RPT0** 및 **_RPTF0** 는 추가 인수 *를 사용 하지* 않으며, **_RPT1** 및 *arg1* **_RPT2** **을 사용** **_RPTF1** arg1 및 **arg2** 를 사용 합니다.

**_RPT** 및 **_RPTF** 매크로는 디버깅 프로세스 중에 응용 프로그램의 진행률을 추적 하는 데 사용할 수 있으므로 [printf](printf-printf-l-wprintf-wprintf-l.md) 함수와 비슷합니다. 그러나 이러한 매크로는 응용 프로그램의 정품 빌드 시 호출 되지 않도록 **#ifdef** 문으로 묶을 필요가 없기 때문에 **printf** 보다 더 유연 합니다. [_DEBUG](../../c-runtime-library/debug.md) 매크로를 사용 하 여 이러한 유연성을 얻을 수 있습니다. **_RPT** 및 **_RPTF** 매크로는 **_DEBUG** 플래그가 정의 된 경우에만 사용할 수 있습니다. **_DEBUG** 정의 되지 않은 경우 전처리 중에 이러한 매크로에 대 한 호출이 제거 됩니다.

**_RPTW** 및 **_RPTFW** 매크로는 이러한 매크로의 와이드 문자 버전입니다. **Wprintf** 와 비슷하며 와이드 문자열을 인수로 사용 합니다.

**_RPT** 매크로는 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) 함수를 호출 하 여 사용자 메시지를 사용 하 여 디버그 보고서를 생성 합니다. **_RPTW** 매크로는 **_CrtDbgReportW** 함수를 호출 하 여 와이드 문자를 사용 하 여 동일한 보고서를 생성 합니다. **_RPTF** 및 **_RPTFW** 매크로는 보고서 매크로가 호출 된 소스 파일과 줄 번호를 사용 하 여 디버그 보고서를 만들고 사용자 메시지에 추가 합니다. 사용자 메시지는 [printf](printf-printf-l-wprintf-wprintf-l.md) 함수에서 정의한 동일한 규칙을 사용 하 여 **arg**[*n*] 인수를 *형식* 문자열로 대체 하 여 생성 됩니다.

**_CrtDbgReport** 또는 **_CrtDbgReportW** 는 디버그 보고서를 생성 하 고 *reportType* 에 대해 정의 된 현재 보고서 모드 및 파일을 기반으로 대상을 결정 합니다. [_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수는 각 보고서 종류의 대상을 정의하는 데 사용됩니다.

**_RPT** 매크로를 호출 하 고 **_CrtSetReportMode** 나 **_CrtSetReportFile** 를 호출 하지 않은 경우 메시지가 다음과 같이 표시 됩니다.

|보고서 종류|출력 대상|
|-----------------|------------------------|
|**_CRT_WARN**|경고 텍스트가 표시되지 않습니다.|
|**_CRT_ERROR**|팝업 창이 표시됩니다. `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`를 지정한 경우와 동일합니다.|
|**_CRT_ASSERT**|**_CRT_ERROR** 와 동일 합니다.|

대상이 디버그 메시지 창이 고 사용자가 **다시 시도** 단추를 선택 하는 경우 **_CrtDbgReport** 또는 **_CrtDbgReportW** 1을 반환 하 여 JIT (just-in-time) 디버깅을 사용 하도록 설정 된 경우 이러한 매크로가 디버거를 시작 합니다. 이들 매크로를 디버깅 오류 처리 메커니즘으로 사용하는 방법에 대한 자세한 내용은 [확인 및 보고에 매크로 사용](/visualstudio/debugger/macros-for-reporting)을 참조하세요.

디버그 보고서를 생성하는 두 가지 다른 매크로가 있습니다. [_ASSERT](assert-asserte-assert-expr-macros.md) 매크로는 해당 식 인수가 FALSE인 경우에 한해 보고서를 생성합니다. [_ASSERTE](assert-asserte-assert-expr-macros.md) 은 **_ASSERT** 와 동일 하지만 생성 된 보고서에 실패 한 식을 포함 합니다.

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-----------|---------------------|
|**_RPT** 매크로|\<crtdbg.h>|
|**_RPTF** 매크로|\<crtdbg.h>|
|**_RPTW** 매크로|\<crtdbg.h>|
|**_RPTFW** 매크로|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

이러한 항목은 매크로이며 Crtdbg.h를 포함하면 가져올 수 있지만, 이러한 매크로는 다른 런타임 함수를 호출하므로 애플리케이션을 디버그 라이브러리 중 하나와 연결해야 합니다.

## <a name="example"></a>예제

[_ASSERT](assert-asserte-assert-expr-macros.md) 항목의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
