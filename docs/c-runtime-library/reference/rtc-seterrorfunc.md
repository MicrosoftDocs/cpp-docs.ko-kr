---
description: '다음에 대 한 자세한 정보: _RTC_SetErrorFunc'
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 454fd54e0960e8ce52c94b4e4a1e0a93ea99d3eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268940"
---
# <a name="_rtc_seterrorfunc"></a>_RTC_SetErrorFunc

RTC(런타임 오류 검사) 보고를 위한 처리기로 함수를 지정합니다. 이 함수는 사용 되지 않습니다. 대신 **_RTC_SetErrorFuncW** 를 사용 해야 합니다.

## <a name="syntax"></a>구문

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>매개 변수

*function*<br/>
런타임 오류 검사를 처리할 함수의 주소입니다.

## <a name="return-value"></a>반환 값

이전에 정의된 오류 함수입니다. 이전에 정의 된 함수가 없으면 **NULL** 을 반환 합니다.

## <a name="remarks"></a>설명

이 함수를 사용 하지 마십시오. 대신 **_RTC_SetErrorFuncW** 를 사용 합니다. 이전 버전과의 호환성을 위해서만 유지됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[런타임 오류 검사](../../c-runtime-library/run-time-error-checking.md)<br/>
