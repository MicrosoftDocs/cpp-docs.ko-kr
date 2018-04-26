---
title: _gcvt_s | Microsoft 문서
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _gcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gcvt_s
- gcvt_s
dev_langs:
- C++
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60f68507f25ba6255b1c6a439c5e74729d2a2646
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="gcvts"></a>_gcvt_s

부동 소수점 값을 문자열로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [_gcvt](gcvt.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>매개 변수

*buffer*<br/>
변환 결과를 저장할 버퍼입니다.

*sizeInBytes*<br/>
버퍼의 크기입니다.

*값*<br/>
변환할 값입니다.

*digits*<br/>
저장된 유효 자릿수입니다.

## <a name="return-value"></a>반환 값

성공할 경우 0입니다. 잘못된 매개 변수로 인해 실패할 경우(잘못된 값은 다음 표 참조) [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 실행하도록 허용된 경우 오류 코드가 반환됩니다. 오류 코드는 Errno.h에서 정의됩니다. 이러한 오류 목록은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

### <a name="error-conditions"></a>오류 조건

|*buffer*|*sizeInBytes*|*값*|*digits*|반환|값을 *버퍼*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|모두|모두|모두|**EINVAL**|수정되지 않습니다.|
|하지 **NULL** (올바른 메모리를 가리킴)|0|모두|모두|**EINVAL**|수정되지 않습니다.|
|하지 **NULL** (올바른 메모리를 가리킴)|모두|모두|>= *sizeInBytes*|**EINVAL**|수정되지 않습니다.|

**보안 문제**

**_gcvt_s** 경우 액세스 위반이 발생 수 *버퍼* 올바른 메모리를 가리키지 않습니다 아니며 **NULL**합니다.

## <a name="remarks"></a>설명

**_gcvt_s** 함수는 부동 소수점 변환 *값* 문자 문자열로 (소수점 및 가능한 기호 바이트 포함)에 문자열을 저장 하 고 *버퍼* . *버퍼* 변환 된 값에 더한 값은 자동으로 추가 종결 null 문자를 수용할 수 있어야 합니다. 버퍼 길이를 **_CVTBUFSIZE** 충분히는 부동 소수점 값입니다. 경우 버퍼 크기는 *자릿수* + 1이 사용, 함수 끝을 덮어쓰지 것입니다는 버퍼의 수 없으므로이 작업에 대 한 충분 한 버퍼를 제공 합니다. **_gcvt_s** 생성 하려고 *자릿수* 10 진수 형식의 숫자입니다. 생성을 표시할 수 없는 경우 *자릿수* 지 수 서식의 자릿수입니다. 변환 시 뒤에 오는 0을 표시하지 않을 수 있습니다.

C++에서는 템플릿 오버로드로 인해 이 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.

이 함수의 디버그 버전은 우선 0xFD로 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>참고자료

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
