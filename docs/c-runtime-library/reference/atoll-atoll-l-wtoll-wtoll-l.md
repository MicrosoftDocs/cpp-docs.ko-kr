---
title: "atoll, _atoll_l, _wtoll, _wtoll_l | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
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
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
dev_langs:
- C++
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 673e8aa823e8624dc70a06447db3da5c68617fc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="atoll-atolll-wtoll-wtolll"></a>atoll, _atoll_l, _wtoll, _wtoll_l
문자열을 `long long` 정수로 변환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
long long atoll(  
   const char *str   
);  
long long _wtoll(  
   const wchar_t *str   
);  
long long _atoll_l(  
   const char *str,  
   _locale_t locale  
);  
long long _wtoll_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `str`  
 변환할 문자열입니다.  
  
 `locale`  
 사용할 로캘입니다.  
  
## <a name="return-value"></a>반환 값  
 각 함수는 입력 문자를 숫자로 해석하여 생성된 `long long` 값을 반환합니다. 입력이 이 형식의 값으로 변환될 수 없는 경우 `atoll`에 대한 반환 값은 0입니다.  
  
 큰 양의 정수 값을 사용하는 오버플로의 경우 `atoll`은 `LLONG_MAX`를 반환하고, 큰 음의 정수 값을 사용하는 오버플로의 경우 `LLONG_MIN`을 반환합니다.  
  
 범위를 벗어난 모든 경우 `errno`는 `ERANGE`로 설정됩니다. 전달된 매개 변수가 `NULL`인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속해서 실행하도록 허용된 경우, 이러한 함수는 `errno`를 `EINVAL`로 설정하고 0을 반환합니다.  
  
## <a name="remarks"></a>설명  
 이러한 함수는 문자열을 `long long` 정수 값으로 변환합니다.  
  
 입력 문자열은 지정된 형식의 숫자 값으로 해석될 수 있는 문자 시퀀스입니다. 함수는 숫자의 일부로 인식할 수 없는 첫 번째 문자에서 입력 문자열 읽기를 중지합니다. 이 문자는 문자열을 종결하는 null 문자('\0' 또는 L'\0')일 수 있습니다.  
  
 `atoll`에 대한 `str` 인수의 형식은 다음과 같습니다.  
  
```  
[whitespace] [sign] [digits]  
```  
  
 A `whitespace` ; 무시 되는 공백 또는 탭 문자로 구성 되어 `sign` 는 더하기 (+) 또는 빼기 (-); 및 `digits` 하나 이상의 숫자가 됩니다.  
  
 `_wtoll`은 와이드 문자를 매개 변수로 사용한다는 점을 제외하고 `atoll`과 동일합니다.  
  
 `_l` 접미사가 있는 이러한 함수 버전은 현재 로캘 대신 전달된 로캘 매개 변수를 사용한다는 점을 제외하고, 접미사가 없는 버전과 동일합니다. 자세한 내용은 [로캘](../../c-runtime-library/locale.md)을 참조하세요.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑  
  
|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tstoll`|`atoll`|`atoll`|`_wtoll`|  
|`_tstoll_l`|`_atoll_l`|`_atoll_l`|`_wtoll_l`|  
|`_ttoll`|`_atoll`|`_atoll`|`_wtoll`|  
  
## <a name="requirements"></a>요구 사항  
  
|루틴|필수 헤더|  
|--------------|---------------------|  
|`atoll`, `_atoll_l`|\<stdlib.h>|  
|`_wtoll`, `_wtoll_l`|\<stdlib.h> 또는 \<wchar.h>|  
  
## <a name="example"></a>예  
 이 프로그램은 `atoll` 함수를 사용하여 문자열로 저장된 숫자를 숫자 값으로 변환하는 방법을 보여 줍니다.  
  
```  
// crt_atoll.c  
// Build with: cl /W4 /Tc crt_atoll.c  
// This program shows how to use the atoll   
// functions to convert numbers stored as   
// strings to numeric values.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main(void)  
{  
    char *str = NULL;  
    long long value = 0;  
  
    // An example of the atoll function  
    // with leading and trailing white spaces.  
    str = "  -27182818284 ";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
```Output  
Function: atoll("  -27182818284 ") = -27182818284  
Function: atoll("314127.64") = 314127  
Function: atoll("3336402735171707160320") = 9223372036854775807  
Overflow condition occurred.  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터 변환](../../c-runtime-library/data-conversion.md)   
 [부동 소수점 지원](../../c-runtime-library/floating-point-support.md)   
 [로캘](../../c-runtime-library/locale.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)