---
description: '다음에 대 한 자세한 정보: _CrtSetReportMode'
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 645a9f8ddf1a1725319eba7a83d9f63270bbed8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279821"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

**_CrtDbgReport** 에서 생성 되는 특정 보고서 종류의 대상 또는 대상을 지정 합니다. 예 [를 들어 _ASSERT, _ASSERTE, _ASSERT_EXPR 매크로](assert-asserte-assert-expr-macros.md), [_ASSERT, _ASSERTE, _ASSERT_EXPR](assert-asserte-assert-expr-macros.md)매크로, _RPT [, _RPTF](rpt-rptf-rptw-rptfw-macros.md), _RPTW, _RPTFW 매크로 [, _RPT 매크로 (디버그](rpt-rptf-rptw-rptfw-macros.md) 버전에만 해당)와 같은 [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)를 호출 하는 매크로입니다.

## <a name="syntax"></a>구문

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 유형: **_CRT_WARN**, **_CRT_ERROR** 및 **_CRT_ASSERT** 합니다.

*reportMode*<br/>
*ReportType* 에 대 한 새 보고서 모드 또는 모드입니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면 **_CrtSetReportMode** *reportType* 에 지정 된 보고서 유형에 대 한 이전 보고서 모드를 반환 합니다. 잘못 된 값이 *reportType* 로 전달 되거나 *reportmode* 에 대해 잘못 된 모드가 지정 된 경우 **_CrtSetReportMode** [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_CrtSetReportMode** **_CrtDbgReport** 의 출력 대상을 지정 합니다. 매크로 [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md)및 [_RPTF](rpt-rptf-rptw-rptfw-macros.md) 호출 **_CrtDbgReport** 는 해당 매크로를 사용 하 여 지정 된 텍스트의 출력 **대상을 지정 합니다** .

[_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetReportMode** 대 한 호출이 제거 됩니다.

**_CrtSetReportMode** 를 호출 하 여 메시지의 출력 대상을 정의 하지 않으면 다음 기본값이 적용 됩니다.

- 어설션 실패 및 오류는 디버그 메시지 창에 전달됩니다.

- Windows 애플리케이션의 경고는 디버거의 출력 창에 전송됩니다.

- 콘솔 애플리케이션의 경고는 표시되지 않습니다.

다음 표에는 Crtdbg.h에 정의된 보고서 형식 목록이 나와 있습니다.

|보고서 종류|설명|
|-----------------|-----------------|
|**_CRT_WARN**|경고, 메시지 및 즉각적인 주의가 필요하지 않은 정보입니다.|
|**_CRT_ERROR**|오류, 복구할 수 없는 문제 및 즉각적인 주의가 필요한 문제입니다.|
|**_CRT_ASSERT**|어설션 실패 ( **FALSE** 로 평가 되는 어설션된 식).|

**_CrtSetReportMode** 함수는 *reportmode* 에 지정 된 새 보고서 모드를 *reportType* 에 지정 된 보고서 형식에 할당 하 고 *reportType* 에 대해 이전에 정의 된 보고서 모드를 반환 합니다. 다음 표에서는 *Reportmode* 에 사용할 수 있는 옵션과 **_CrtDbgReport** 의 결과 동작을 보여 줍니다. 이러한 옵션은 Crtdbg.h에서 비트 플래그로 정의되어 있습니다.

|보고서 모드|_CrtDbgReport 동작|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|디버거의 출력 창에 메시지를 작성합니다.|
|**_CRTDBG_MODE_FILE**|사용자가 제공한 파일 핸들에 메시지를 작성합니다. [_CrtSetReportFile](crtsetreportfile.md)을 호출하여 대상으로 사용할 특정 파일 또는 스트림을 정의해야 합니다.|
|**_CRTDBG_MODE_WNDW**|[중단](abort.md), **다시 시도** 및 **무시** 단추와 함께 메시지를 표시 하는 메시지 상자를 만듭니다.|
|**_CRTDBG_REPORT_MODE**|지정 된 *reportType* 에 대해 *reportmode* 를 반환 합니다.<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

한 가지, 두 가지 또는 세 가지 모드를 사용하거나 모드를 전혀 사용하고 각 보고서 형식을 보고할 수 있습니다. 따라서 단일 보고서 형식에 대해 정의된 대상이 둘 이상 있을 수 있습니다. 예를 들어 다음 코드 조각에서는 어설션 오류가 디버그 메시지 창과 **stderr** 모두에 전송 되도록 합니다.

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

또한 각 보고서 형식에 대한 보고 모드를 개별적으로 제어할 수 있습니다. 예를 들어 앞에서 설명한 대로 디버그 메시지 창을 사용 하 여 표시 되 고 **stderr** 로 전송 되는 **_CRT_ASSERT** **_CRT_WARN** 의 *reportType* 를 출력 디버그 문자열로 보내도록 지정할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
