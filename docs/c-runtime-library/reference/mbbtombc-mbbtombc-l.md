---
title: "_mbbtombc, _mbbtombc_l | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbbtombc_l
- _mbbtombc
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
dev_langs:
- C++
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0cfa6c4162eee1422def2343f38745183e1b4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="mbbtombc-mbbtombcl"></a>_mbbtombc, _mbbtombc_l
싱글바이트 멀티바이트 문자를 해당 더블바이트 멀티바이트 문자로 변환합니다.  
  
> [!IMPORTANT]
>  이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 참조 [CRT 함수는 유니버설 Windows 플랫폼 앱에서 지원 되지 않습니다](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned int _mbbtombc(  
   unsigned int c   
);  
unsigned int _mbbtombc_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `c`  
 변환할 싱글바이트 문자입니다.  
  
 `locale`  
 사용할 로캘입니다.  
  
## <a name="return-value"></a>반환 값  
 `_mbbtombc`가 `c`를 성공적으로 변환한 경우 멀티바이트 문자를 반환합니다. 그렇지 않으면 `c`를 반환합니다.  
  
## <a name="remarks"></a>설명  
 `_mbbtombc` 함수는 지정된 싱글바이트 멀티바이트 문자를 해당 더블바이트 멀티바이트 문자로 변환합니다. 문자 변환 될 0xDF 0x20-0x7E 또는 0xA1-범위 사이 여야 합니다.  
  
 출력값은 로캘의 `LC_CTYPE` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. 이 버전의 함수는 `_mbbtombc`가 이 로캘 종속 동작의 현재 로캘을 사용하고 `_mbbtombc_l`은 전달된 로캘 매개 변수를 사용한다는 점을 제외하고는 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.  
  
 이전 버전에서 `_mbbtombc`의 이름은 `hantozen`입니다. 새 코드의 경우 `_mbbtombc`를 사용합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_mbbtombc`|\<mbstring.h>|  
|`_mbbtombc_l`|\<mbstring.h>|  
  
 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 변환](../../c-runtime-library/data-conversion.md)   
 [_mbctombb, _mbctombb_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)