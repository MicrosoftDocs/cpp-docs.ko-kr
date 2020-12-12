---
description: '다음에 대 한 자세한 정보: _ecvt_s'
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: abda39ce5c33a5f6b6cca0757411e16c4171cd97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206944"
---
# <a name="_ecvt_s"></a>_ecvt_s

숫자를 **`double`** 문자열로 변환 합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [_ecvt](ecvt.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>매개 변수

*_Buffer*<br/>
변환의 결과인 숫자 문자열에 대한 포인터로 채워집니다.

*_SizeInBytes*<br/>
버퍼의 크기(바이트)입니다.

*_Value*<br/>
변환할 숫자입니다.

*_Count*<br/>
저장된 자릿수입니다.

*_Dec*<br/>
저장된 소수점 위치입니다.

*_Sign*<br/>
변환된 숫자의 부호입니다.

## <a name="return-value"></a>반환 값

성공할 경우 0입니다. 오류가 있을 경우 반환 값은 오류 코드입니다. 오류 코드는 Errno.h에서 정의됩니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

다음 표에 나와 있는 잘못된 매개 변수의 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 이 함수는 잘못된 매개 변수 처리기를 호출합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

### <a name="error-conditions"></a>오류 조건

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|반환 값|*버퍼* 의 값|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|수정되지 않습니다.|
|Not **NULL** (유효한 메모리를 가리킴)|<=0|any|any|any|any|**EINVAL**|수정되지 않습니다.|
|any|any|any|any|**NULL**|any|**EINVAL**|수정되지 않습니다.|
|any|any|any|any|any|**NULL**|**EINVAL**|수정되지 않습니다.|

## <a name="security-issues"></a>보안 문제

*버퍼가* 유효한 메모리를 가리키지 않고 **NULL** 이 아닌 경우에는 **_ecvt_s** 에서 액세스 위반이 발생할 수 있습니다.

## <a name="remarks"></a>설명

**_Ecvt_s** 함수는 부동 소수점 숫자를 문자열로 변환 합니다. *_Value* 매개 변수는 변환할 부동 소수점 숫자입니다. 이 함수는 *_Value* 의 *숫자를* 문자열로 저장 하 고 null 문자 (' \ 0 ')를 추가 합니다. *_Value* 의 자릿수가 *_Count* 을 초과 하는 경우 하위 숫자가 반올림 됩니다. *개수* 보다 작은 경우 문자열은 0으로 채워집니다.

숫자만 문자열에 저장됩니다. 소수점의 위치와 *_Value* 부호는 *_Dec* 에서 가져올 수 있으며 호출 후에 *_Sign* 수 있습니다. *_Dec* 매개 변수는 문자열의 시작 부분을 기준으로 소수점의 위치를 제공 하는 정수 값을 가리킵니다. 0 또는 음의 정수 값은 소수점이 첫 번째 숫자의 왼쪽에 있다는 것을 나타냅니다. *_Sign* 매개 변수는 변환 된 숫자의 부호를 나타내는 정수를 가리킵니다. 정수 값이 0이면 숫자가 양수입니다. 그렇지 않으면 숫자가 음수입니다.

모든 부동 소수점 값에는 길이가 **_CVTBUFSIZE** 버퍼가 면 충분 합니다.

**_Ecvt_s** 와 **_fcvt_s** 의 차이점은 *_Count* 매개 변수를 해석 하는 것입니다. **_ecvt_s** 는 *_Count* 를 출력 문자열의 전체 자릿수로 해석 하는 반면 **_fcvt_s** 는 *_Count* 를 소수점 뒤의 자릿수로 해석 합니다.

C++에서는 템플릿 오버로드로 인해 이 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이 함수의 디버그 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
