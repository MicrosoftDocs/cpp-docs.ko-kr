---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs:
- C++
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5e6f77960cb0beca886ec18125e47cd929a9dfe
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l
문자를 소문자로 변환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `c`  
 변환할 문자입니다.  
  
 [in] `locale`  
 로캘별 변환에 사용할 로캘입니다.  
  
## <a name="return-value"></a>반환 값  
 이러한 각 루틴은 변환이 가능한 경우 `c`의 복사본을 소문자로 변환하고 결과를 반환합니다. 오류를 나타내기 위해 예약된 반환 값은 없습니다.  
  
## <a name="remarks"></a>설명  
 이러한 각 루틴은 가능하며 관련성이 있는 경우 지정된 대문자를 소문자로 변환합니다. `towlower`의 대/소문자 변환은 로캘에 따라 다릅니다. 현재 로캘에서 유효한 문자의 대/소문자만 변경됩니다. `_l` 접미사가 없는 함수는 현재 설정된 로캘을 사용합니다. 이러한 함수의 `_l` 접미사가 있는 버전은 로캘을 매개 변수로 사용하며 현재 설정된 로캘 대신 해당 로캘을 사용합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.  
  
 `_tolower`가 필요한 값을 제공하려면 [__isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 및 [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)가 둘 다 0이 아닌 값을 반환해야 합니다.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑  
  
|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l` 및 `_towlower_l`은 로캘에 종속되지 않으며 직접 호출할 수 없습니다. 이 두 항목은 `_totlower_l` 내부에서 사용하도록 제공됩니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`tolower`|\<ctype.h>|  
|`_tolower`|\<ctype.h>|  
|`towlower`|\<ctype.h> 또는 \<wchar.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하십시오.  
  
## <a name="example"></a>예  
 [to 함수](../../c-runtime-library/to-functions.md)의 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 변환](../../c-runtime-library/data-conversion.md)   
 [is, isw 루틴](../../c-runtime-library/is-isw-routines.md)   
 [to 함수](../../c-runtime-library/to-functions.md)   
 [로캘](../../c-runtime-library/locale.md)   
 [멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)