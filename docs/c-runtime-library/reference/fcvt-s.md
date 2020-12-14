---
description: '다음에 대 한 자세한 정보: _fcvt_s'
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: dd4d58b39d4c18f2fff7da54c5fbd0f2346dfdd4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235881"
---
# <a name="_fcvt_s"></a>_fcvt_s

부동 소수점 숫자를 문자열로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [_fcvt](fcvt.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
변환 결과를 포함할 제공된 버퍼입니다.

*sizeInBytes*<br/>
버퍼 크기(바이트)입니다.

*value*<br/>
변환할 숫자입니다.

*count*<br/>
소수점 뒤의 자릿수입니다.

*dec*<br/>
저장된 소수점 위치의 포인터입니다.

*sign*<br/>
저장된 부호 표시기의 포인터입니다.

## <a name="return-value"></a>반환 값

성공할 경우 0입니다. 오류가 있을 경우 반환 값은 오류 코드입니다. 오류 코드는 Errno.h에서 정의됩니다. 이러한 오류 목록은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

다음 표에 나와 있는 잘못된 매개 변수의 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 이 함수는 잘못된 매개 변수 처리기를 호출합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

### <a name="error-conditions"></a>오류 조건

|*버퍼*|*sizeInBytes*|값|count|dec|sign|반환 값|*버퍼* 의 값|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|수정되지 않습니다.|
|Not **NULL** (유효한 메모리를 가리킴)|<=0|any|any|any|any|**EINVAL**|수정되지 않습니다.|
|any|any|any|any|**NULL**|any|**EINVAL**|수정되지 않습니다.|
|any|any|any|any|any|**NULL**|**EINVAL**|수정되지 않습니다.|

## <a name="security-issues"></a>보안 문제

*버퍼가* 유효한 메모리를 가리키지 않고 **NULL** 이 아닌 경우에는 **_fcvt_s** 에서 액세스 위반이 발생할 수 있습니다.

## <a name="remarks"></a>설명

**_Fcvt_s** 함수는 부동 소수점 숫자를 null로 끝나는 문자열로 변환 합니다. *값* 매개 변수는 변환할 부동 소수점 숫자입니다. **_fcvt_s** 은 *값* 의 숫자를 문자열로 저장 하 고 null 문자 (' \ 0 ')를 추가 합니다. *Count* 매개 변수는 소수점 뒤에 저장할 자릿수를 지정 합니다. 자릿수를 *계산* 하기 위해 초과 하는 숫자가 반올림 됩니다. 정밀도의 *자릿수가 보다 적으면* 문자열은 0으로 채워집니다.

숫자만 문자열에 저장됩니다. 소수점 및 부호 *값* 의 위치는 *dec* 에서 가져오고 호출 후에 *서명할* 수 있습니다. *Dec* 매개 변수는 정수 값을 가리킵니다. 이 정수 값은 문자열의 시작 부분을 기준으로 소수점의 위치를 제공 합니다. 0 또는 음의 정수 값은 소수점이 첫 번째 숫자의 왼쪽에 있다는 것을 나타냅니다. 매개 변수 *부호* 는 *값* 의 부호를 나타내는 정수를 가리킵니다. *값* 이 양수 이면 정수는 0으로 설정 되 고 *값* 이 음수 이면 0이 아닌 숫자로 설정 됩니다.

모든 부동 소수점 값에는 길이가 **_CVTBUFSIZE** 버퍼가 면 충분 합니다.

**_Ecvt_s** 와 **_fcvt_s** 의 차이는 *count* 매개 변수를 해석 하는 것입니다. **_ecvt_s** 은 *개수* 를 출력 문자열의 총 자릿수로 해석 하 고 **_fcvt_s** 은 소수점이 하 자릿수를 *숫자로 해석 합니다* .

C++에서는 템플릿 오버로드로 인해 이 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이 함수의 디버그 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 모든 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
