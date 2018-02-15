---
title: "_memicmp, _memicmp_l | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _memicmp_l
- _memicmp
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
dev_langs:
- C++
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b79c36bc665d1d7a32ef50984a75b48811985d1e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="memicmp-memicmpl"></a>_memicmp, _memicmp_l
두 개의 버퍼에서 문자를 비교합니다(소문자).  
  
## <a name="syntax"></a>구문  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `buf1`  
 첫 번째 버퍼입니다.  
  
 `buf2`  
 두 번째 버퍼입니다.  
  
 `count`  
 문자 수입니다.  
  
 `locale`  
 사용할 로캘입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 값은 부분 문자열 간의 관계를 나타냅니다.  
  
|반환 값|buf1 및 buf2의 첫 번째 count 바이트의 관계|  
|------------------|--------------------------------------------------------|  
|< 0|`buf1`이 `buf2`보다 작은 경우|  
|0|`buf1`이 `buf2`와 동일한 경우|  
|> 0|`buf1`이 `buf2`보다 큽니다.|  
|`_NLSCMPERROR`|오류가 발생했습니다.|  
  
## <a name="remarks"></a>설명  
 `_memicmp` 함수는 두 버퍼 `count` 및 `buf1`의 첫 번째 `buf2` 문자를 바이트 단위로 비교합니다. 대/소문자를 구분하지 않고 비교합니다.  
  
 `buf1` 또는 `buf2`가 null 포인터인 경우 이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용된 경우 함수가 `_NLSCMPERROR`를 반환하며 `errno`를 `EINVAL`로 설정합니다.  
  
 `_memicmp`는 로캘 종속 동작의 현재 로캘을 사용하고 `_memicmp_l`은 전달된 로캘을 사용한다는 점을 제외하고 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_memicmp`|\<memory.h> 또는 \<string.h>|  
|`_memicmp_l`|\<memory.h> 또는 \<string.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
```Output  
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'  
First is equal to second.  
```  
  
## <a name="see-also"></a>참고 항목  
 [버퍼 조작](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)