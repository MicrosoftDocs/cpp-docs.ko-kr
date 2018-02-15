---
title: "_fgetc_nolock, _fgetwc_nolock | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fgetc_nolock
- _fgetwc_nolock
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
- _fgetwc_nolock
- fgettc_nolock
- fgetwc_nolock
- _fgetc_nolock
- _fgettc_nolock
- fgetc_nolock
dev_langs:
- C++
helpviewer_keywords:
- fgetc_nolock function
- fgetwc_nolock function
- _fgetwc_nolock function
- characters, reading
- _fgetc_nolock function
- streams, reading characters from
- fgettc_nolock function
- reading characters from streams
- _fgettc_nolock function
ms.assetid: fb8e7c5b-4503-493a-879e-6a1db75aa114
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 475693126cbc33b16710bf260d342c5c5f079540
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="fgetcnolock-fgetwcnolock"></a>_fgetc_nolock, _fgetwc_nolock
스레드를 잠그지 않고 스트림에서 문자를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```  
int _fgetc_nolock(   
   FILE *stream   
);  
wint_t _fgetwc_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `stream`  
 `FILE` 구조체에 대한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)를 참조하세요.  
  
## <a name="remarks"></a>설명  
 `_fgetc_nolock` 및 `_fgetwc_nolock` 함수는 다른 스레드의 간섭으로부터 보호되지 않는다는 점을 제외하고 `fgetc` 및 `fgetwc`와 동일합니다. 이들은 다른 스레드를 잠그는 오버헤드를 유발하지 않으므로 속도가 더 빠를 수 있습니다. 단일 스레드 응용 프로그램과 같은 스레드로부터 안전한 컨텍스트 또는 이미 스레드 격리를 처리한 호출 범위에서만 이러한 함수를 사용합니다.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑  
  
|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_fgettc_nolock`|`_fgetc_nolock`|`_fgetc_nolock`|`_fgetwc_nolock`|  
  
## <a name="requirements"></a>요구 사항  
  
|함수|필수 헤더|  
|--------------|---------------------|  
|`_fgetc_nolock`|\<stdio.h>|  
|`_fgetwc_nolock`|\<stdio.h> 또는 \<wchar.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_fgetc_nolock.c  
// This program uses getc to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   char buffer[81];  
   int  i, ch;  
  
   // Open file to read line from:   
   if( fopen_s( &stream, "crt_fgetc_nolock.txt", "r" ) != 0 )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetc_nolock( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfgetcnolocktxt"></a>입력: crt_fgetc_nolock.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>출력  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>참고 항목  
 [스트림 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)