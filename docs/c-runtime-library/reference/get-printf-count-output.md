---
title: "_get_printf_count_output | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05184838f9ac68e697cc7ff326c33c266f865875
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output
[printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 패밀리 함수가 `%n` 형식을 지원하는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
int _get_printf_count_output();  
```  
  
## <a name="return-value"></a>반환 값  
 `%n`이 지원되는 경우 0이 아니고 `%n`이 지원되지 않는 경우 0입니다.  
  
## <a name="remarks"></a>설명  
 `%n`이 지원되지 않는 경우(기본값) `printf` 함수의 형식 문자열에서 `%n`이 나타나면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 경우 `%n` 지원이 활성화 된 (참조 [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)) 다음 `%n` 에 설명 된 대로 동작 [형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하십시오.  
  
## <a name="example"></a>예  
 [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)의 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)  
