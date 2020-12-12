---
description: '다음에 대 한 자세한 정보: _RTC_SetErrorType'
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 8b0b28eaf97a27dbfcf4dcb414c9a17f03df7f9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168698"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

RTC(런타임 오류 검사)에서 발견된 오류를 형식에 연결합니다. 오류 처리기는 지정된 형식의 오류를 출력하는 방법을 처리합니다.

## <a name="syntax"></a>구문

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>매개 변수

*errnum*<br/>
0과 [_RTC_NumErrors](rtc-numerrors.md)에서 반환한 값에서 1을 뺀 수 사이의 숫자를 반환합니다.

*ErrType*<br/>
이 *errnum* 에 할당할 값입니다. 예를 들어 **_CRT_ERROR** 를 사용할 수 있습니다. **_CrtDbgReport** 를 오류 처리기로 사용 하는 경우 *errtype* 은 [_CrtSetReportMode](crtsetreportmode.md)에 정의 된 기호 중 하나일 수만 있습니다. 사용자 고유의 오류 처리기([_RTC_SetErrorFunc](rtc-seterrorfunc.md))가 있는 경우 *errnum* 개수만큼 *ErrType* 을 사용할 수 있습니다.

*Errtype* _RTC_ERRTYPE_IGNORE는 **_CrtSetReportMode** 에 특별 한 의미가 있습니다. 오류는 무시 됩니다.

## <a name="return-value"></a>반환 값

오류 유형 *형식* 에 대 한 이전 값입니다.

## <a name="remarks"></a>설명

기본적으로 모든 오류가 *_CRT_ERROR* 에 해당하는 **ErrType**= 1로 설정됩니다. **_CRT_ERROR** 와 같은 기본 오류 유형에 대한 자세한 내용은 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md)를 참조하세요.

이 함수를 호출하려면 먼저 런타임 오류 검사 초기화 함수 중 하나를 호출해야 합니다. [C 런타임 라이브러리 없이 런타임 검사 사용](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[런타임 오류 검사](../../c-runtime-library/run-time-error-checking.md)<br/>
