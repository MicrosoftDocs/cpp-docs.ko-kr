---
title: _CrtSetReportMode
description: '다음에 대 한 자세한 정보: _CrtSetReportMode'
ms.date: 3/8/2021
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
ms.openlocfilehash: 770ef955894563dc11dee9f13946067d5d024c11
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514384"
---
# `_CrtSetReportMode`

**_CrtDbgReport** 에서 생성 한 특정 보고서 형식의 대상 또는 대상을 지정 합니다 [`_CrtDbgReport, _CrtDbgReportW`](crtdbgreport-crtdbgreportw.md) (예: [ `_ASSERT, _ASSERTE, _ASSERT_EXPR` 매크로](assert-asserte-assert-expr-macros.md), [ `_ASSERT, _ASSERTE, _ASSERT_EXPR` 매크로](assert-asserte-assert-expr-macros.md), [ `_RPT, _RPTF, _RPTW, _RPTFW` 매크로](rpt-rptf-rptw-rptfw-macros.md)및 [ `_RPT, _RPTF, _RPTW, _RPTFW` 매크로](rpt-rptf-rptw-rptfw-macros.md) ). (디버그 버전에만 해당)를 호출 하는 매크로입니다.

## <a name="syntax"></a>구문

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>매개 변수

*`reportType`*\
보고서 유형: **`_CRT_WARN`** , **`_CRT_ERROR`** 및 **`_CRT_ASSERT`**

*`reportMode`*\
의 새 보고서 모드 또는 모드 *`reportType`* 입니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면는 **`_CrtSetReportMode`** 에 지정 된 보고서 유형에 대 한 이전 보고서 모드를 반환 합니다 *`reportType`* . 에 잘못 된 값이 전달 *`reportType`* 되거나에 잘못 된 모드가 지정 된 경우 *`reportMode`* 는 **`_CrtSetReportMode`** [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **`errno`** 를로 설정 하 **`EINVAL`** 고-1을 반환 합니다. 자세한 내용은 [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**`_CrtSetReportMode`** 의 출력 대상을 지정 합니다 **`_CrtDbgReport`** . 매크로 [`_ASSERT`](assert-asserte-assert-expr-macros.md) , [`_ASSERTE`](assert-asserte-assert-expr-macros.md) , [`_RPT`](rpt-rptf-rptw-rptfw-macros.md) 및 [`_RPTF`](rpt-rptf-rptw-rptfw-macros.md) 호출에서는 **`_CrtDbgReport`** **`_CrtSetReportMode`** 해당 매크로를 사용 하 여 지정 된 텍스트의 출력 대상을 지정 합니다.

[`_DEBUG`](../../c-runtime-library/debug.md)가 정의 되지 않은 경우 전처리 중에 대 한 호출이 **`_CrtSetReportMode`** 제거 됩니다.

**`_CrtSetReportMode`** 을 호출 하 여 메시지의 출력 대상을 정의 하지 않으면 다음 기본값이 적용 됩니다.

- 어설션 실패 및 오류는 디버그 메시지 창에 전달됩니다.

- Windows 애플리케이션의 경고는 디버거의 출력 창에 전송됩니다.

- 콘솔 애플리케이션의 경고는 표시되지 않습니다.

다음 표에서는에 정의 된 보고서 유형을 나열 합니다 `Crtdbg.h` .

|보고서 종류|Description|
|-----------------|-----------------|
|**`_CRT_WARN`**|경고, 메시지 및 즉각적인 주의가 필요하지 않은 정보입니다.|
|**`_CRT_ERROR`**|오류, 복구할 수 없는 문제 및 즉각적인 주의가 필요한 문제입니다.|
|**`_CRT_ASSERT`**|어설션 실패 (로 평가 되는 어설션된 식 **`FALSE`** ).|

함수는에 지정 된 **`_CrtSetReportMode`** 새 보고서 모드를에 *`reportMode`* 지정 된 보고서 형식에 할당 *`reportType`* 하 고에 대해 이전에 정의 된 보고서 모드를 반환 합니다 *`reportType`* . 다음 표에서는에 사용할 수 있는 선택 항목 *`reportMode`* 및의 결과 동작을 보여 줍니다 **`_CrtDbgReport`** . 이러한 옵션은 Crtdbg.h에서 비트 플래그로 정의되어 있습니다.

|보고서 모드|_CrtDbgReport 동작|
|-----------------|-----------------------------|
|**`_CRTDBG_MODE_DEBUG`**|디버거의 출력 창에 메시지를 작성합니다.|
|**`_CRTDBG_MODE_FILE`**|사용자가 제공한 파일 핸들에 메시지를 작성합니다. [`_CrtSetReportFile`](crtsetreportfile.md) 대상으로 사용할 특정 파일 또는 스트림을 정의 하기 위해를 호출 해야 합니다.|
|**`_CRTDBG_MODE_WNDW`**|[`abort`](abort.md), **`Retry`** 및 **무시** 단추와 함께 메시지를 표시 하는 메시지 상자를 만듭니다.|
|**`_CRTDBG_REPORT_MODE`**|*`reportMode`* 지정 된에 대 한를 반환 합니다 *`reportType`* .<br /><br /> 1(sp1)   **`_CRTDBG_MODE_FILE`**<br /><br /> sr-2   **`_CRTDBG_MODE_DEBUG`**<br /><br /> 3-4   **`_CRTDBG_MODE_WNDW`**|

한 가지, 두 가지 또는 세 가지 모드를 사용하거나 모드를 전혀 사용하고 각 보고서 형식을 보고할 수 있습니다. 따라서 단일 보고서 형식에 대해 정의된 대상이 둘 이상 있을 수 있습니다. 예를 들어 다음 코드 조각에서는 어설션 실패를 디버그 메시지 창과로 전송 합니다 **`stderr`** .

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

또한 각 보고서 형식에 대한 보고 모드를 개별적으로 제어할 수 있습니다. 예를 들어 앞에서 설명한 *`reportType`* 대로의를 **`_CRT_WARN`** 출력 디버그 문자열로 보내도록 지정 하 **`_CRT_ASSERT`** 고, 디버그 메시지 창을 사용 하 여 표시 하 고로 보낼 수 있습니다 **`stderr`** .

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**`_CrtSetReportMode`**|`<crtdbg.h>`|`<errno.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md) 만 해당 합니다.

## <a name="see-also"></a>추가 정보

[디버그 루틴](../../c-runtime-library/debug-routines.md)
