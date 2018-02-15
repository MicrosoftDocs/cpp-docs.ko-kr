---
title: _strdate_s, _wstrdate_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strdate_s
- _wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs:
- C++
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e71476fbb1810505f0b50a04d20f6235ff727c92
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s
현재 시스템 날짜를 버퍼에 복사합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [_strdate, _wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md)의 버전입니다.  
  
## <a name="syntax"></a>구문  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>매개 변수  
 [out] `buffer`  
 형식이 지정된 날짜 문자를 입력할 버퍼에 대한 포인터입니다.  
  
 [in] `numberOfElements`  
 버퍼의 크기입니다.  
  
## <a name="return-value"></a>반환 값  
 정상적으로 실행되는 경우 0입니다. 오류가 있을 경우 반환 값은 오류 코드입니다. 오류 코드는 ERRNO.H에 정의됩니다. 이 함수가 생성하는 정확한 오류는 아래 표를 참조하세요. 오류 코드에 대한 자세한 내용은 [errno](../../c-runtime-library/errno-constants.md)를 참조하세요.  
  
## <a name="error-conditions"></a>오류 조건  
  
|`buffer`|`numberOfElements`|반환|`buffer`의 내용|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|(임의)|`EINVAL`|수정 안 됨|  
|`NULL` 아님(유효한 버퍼를 가리킴)|0|`EINVAL`|수정 안 됨|  
|`NULL` 아님(유효한 버퍼를 가리킴)|0 < `numberOfElements` < 9|`EINVAL`|빈 문자열|  
|`NULL` 아님(유효한 버퍼를 가리킴)|`numberOfElements` >= 9|0|설명에 지정된 형식의 현재 날짜|  
  
## <a name="security-issues"></a>보안 문제  
 버퍼에 대해 `NULL`이 아닌 잘못된 값을 전달하는 경우 `numberOfElements` 매개 변수가 9보다 크면 액세스 위반이 발생합니다.  
  
 size에 대해 `buffer`의 실제 크기보다 큰 값을 전달하면 버퍼 오버런이 발생합니다.  
  
## <a name="remarks"></a>설명  
 이러한 함수는 `_strdate` 및 `_wstrdate`의 더 안전한 버전을 제공합니다. `_strdate_s` 함수는 `mm`/`dd`/`yy` 형식의 `buffer`가 가리키는 버퍼에 현재 시스템 날짜를 복사합니다. 여기서 `mm`은 월을 나타내는 두 자리 숫자, `dd`는 일을 나타내는 두 자리 숫자, `yy`는 연도의 마지막 두 자리 숫자입니다. 예를 들어 `12/05/99` 문자열은 1999년 12월 5일을 나타냅니다. 버퍼의 길이는 9자 이상이어야 합니다.  
  
 `_wstrdate_s`는 `_strdate_s`의 와이드 문자 버전이고, `_wstrdate_s`의 인수와 반환 값은 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.  
  
 `buffer`가 `NULL` 포인터이거나 `numberOfElements`가 9자보다 작으면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속하도록 허용하는 경우 이러한 함수는 -1을 반환하고 버퍼가 `NULL`이거나 `numberOfElements`가 0보다 작거나 같으면 `errno`를 `EINVAL`로 설정하며, `numberOfElements`가 9보다 작으면 `errno`를 `ERANGE`로 설정합니다.  
  
 C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.  
  
### <a name="generic-text-routine-mapping"></a>제네릭 텍스트 루틴 매핑:  
  
|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_strdate`|\<time.h>|  
|`_wstrdate`|\<time.h> 또는 \<wchar.h>|  
|`_strdate_s`|\<time.h>|  
  
## <a name="example"></a>예  
 [time](../../c-runtime-library/reference/time-time32-time64.md)의 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [시간 관리](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, _mktime32, _mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)