---
description: '다음에 대 한 자세한 정보: _get_daylight'
title: _get_daylight
ms.date: 4/2/2020
api_name:
- __daylight
- _get_daylight
- _o___daylight
- _o__get_daylight
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: dcb4ffb80ea79d89cad84617d4c8e4dceb1735c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341479"
---
# <a name="_get_daylight"></a>_get_daylight

일광 절약 시간 오프셋(시간)을 검색합니다.

## <a name="syntax"></a>구문

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>매개 변수

*시간의*<br/>
일관 절약 시간의 오프셋(시간)입니다.

## <a name="return-value"></a>반환 값

성공 하면 0이 고, 오류가 발생 하면 **errno** 값입니다.

## <a name="remarks"></a>설명

**_Get_daylight** 함수는 일광 절약 시간의 시간 수를 정수로 검색 합니다. 일광 절약 시간이 적용 중인 경우 몇몇 지역에서 2시간 오프셋을 따르고 있더라도 기본 오프셋은 1시간입니다.

*Hours* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

매크로 **_daylight** 또는 사용 되지 않는 함수 **__daylight** 대신이 함수를 사용 하는 것이 좋습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
