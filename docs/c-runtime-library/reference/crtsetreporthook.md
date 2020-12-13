---
description: '다음에 대 한 자세한 정보: _CrtSetReportHook'
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 1e99e17b3a245dfe78e5a0f7367e422f4dc97600
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342246"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

클라이언트 정의 보고 함수를 C 런타임 디버그 보고 프로세스에 연결함으로써 설치합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>매개 변수

*reportHook*<br/>
C 런타임 디버그 보고 프로세스에 연결할 새로운 클라이언트 정의 보고 함수입니다.

## <a name="return-value"></a>반환 값

이전 클라이언트 정의 보고 함수를 반환합니다.

## <a name="remarks"></a>설명

**_CrtSetReportHook** 를 사용 하면 응용 프로그램에서 해당 보고 함수를 C 런타임 디버그 라이브러리 보고 프로세스에 사용할 수 있습니다. 결과적으로 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md)가 호출되어 디버그 보고서를 생성할 때마다 애플리케이션의 보고 함수가 먼저 호출됩니다. 이 기능을 사용 하면 응용 프로그램이 특정 할당 형식에 초점을 맞출 수 있도록 디버그 보고서를 필터링 하거나 **_CrtDbgReport** 를 사용 하 여 사용할 수 없는 대상으로 보고서를 보낼 수 있습니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetReportHook** 대 한 호출이 제거 됩니다.

보다 강력한 버전의 **_CrtSetReportHook** [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)를 참조 하세요.

**_CrtSetReportHook** 함수는 *reportHook* 에 지정 된 새로운 클라이언트 정의 보고 함수를 설치 하 고 이전 클라이언트 정의 후크를 반환 합니다. 다음 예제에서는 클라이언트 정의 보고서 후크가 어떻게 프로토타입화되어야 하는지를 보여 줍니다.

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

여기서 *reportType* 는 디버그 보고서 형식 (**_CRT_WARN**, **_CRT_ERROR** 또는 **_CRT_ASSERT**)이 고, *메시지* 는 보고서에 포함 될 완전히 어셈블된 디버그 사용자 메시지이 고, **returnValue** 는 **_CrtDbgReport** 에서 반환 해야 하는 클라이언트 정의 보고 함수에서 지정 된 값입니다. 사용 가능한 보고서 형식에 대한 자세한 설명은 [_CrtSetReportMode](crtsetreportmode.md) 함수를 참조하세요.

클라이언트 정의 보고 함수에서 추가 보고가 필요 하지 않도록 디버그 메시지를 완전히 처리 하는 경우이 함수는 **TRUE** 를 반환 해야 합니다. 함수가 **FALSE** 를 반환 하는 경우 보고서 유형, 모드 및 파일에 대 한 현재 설정을 사용 하 여 디버그 보고서를 생성 하기 위해 **_CrtDbgReport** 가 호출 됩니다. 또한 응용 프로그램은 **returnValue** 에서 **_CrtDbgReport** 반환 값을 지정 하 여 디버그 중단이 발생 하는지 여부를 제어할 수도 있습니다. 디버그 보고서를 구성 하 고 생성 하는 방법에 대 한 자세한 설명은 **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md)및 **_CrtDbgReport** 를 참조 하세요.

다른 후크 가능 런타임 함수를 사용하고 고유한 클라이언트 정의 후크 함수를 작성하는 방법에 대한 자세한 내용은 [디버그 후크 함수 작성](/visualstudio/debugger/debug-hook-function-writing)을 참조하세요.

> [!NOTE]
> 응용 프로그램이 **/clr** 을 사용 하 여 컴파일되고 응용 프로그램의 main이 종료 된 후 보고 함수가 호출 되는 경우 보고 함수가 CRT 함수를 호출 하면 clr에서 예외가 throw 됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
