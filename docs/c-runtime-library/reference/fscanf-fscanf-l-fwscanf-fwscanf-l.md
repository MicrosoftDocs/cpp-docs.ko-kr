---
title: fscanf, _fscanf_l, fwscanf, _fwscanf_l | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
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
apitype: DLLExport
f1_keywords:
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
dev_langs:
- C++
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72ed322c78723826615e1264642eb53f6f9eb14d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404076"
---
# <a name="fscanf-fscanfl-fwscanf-fwscanfl"></a>fscanf, _fscanf_l, fwscanf, _fwscanf_l

스트림에서 형식 지정된 데이터를 읽습니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)을 참조하세요.

## <a name="syntax"></a>구문

```C
int fscanf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

*format*<br/>
형식 컨트롤 문자열입니다.

*argument*<br/>
선택적 인수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 모두 성공적으로 변환되고 할당된 필드 수를 반환합니다. 이때 읽혀졌지만 할당되지 않은 필드는 반환 값에 포함되지 않습니다. 반환 값이 0이면 할당된 필드가 없음을 나타냅니다. 오류가 발생 했거나 반환 값은 첫 번째 변환 하기 전에 파일 스트림의 끝에 도달 하는 경우 **EOF** 에 대 한 **fscanf** 및 **fwscanf**합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. 경우 *스트림* 또는 *형식* 가 null 포인터에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된 경우 이러한 함수가 반환 **EOF** 설정 **errno** 를 **EINVAL**합니다.

## <a name="remarks"></a>설명

**fscanf** 함수의 현재 위치에서 데이터를 읽고 *스트림* 에 의해 지정 된 위치로 *인수* (있는 경우). 각 *인수* 의 형식 지정자에 해당 하는 형식의 변수에 대 한 포인터 여야 *형식*합니다. *형식* 컨트롤 입력의 해석은 필드 및 동일한 형태와 기능을 *형식* 에 대 한 인수 **scanf**; 참조 [scanf](scanf-scanf-l-wscanf-wscanf-l.md) 에 에 대 한 설명 *형식*합니다.

**fwscanf** 의 와이드 문자 버전이 **fscanf**; format 인수를 **fwscanf** 는 와이드 문자 문자열입니다. 스트림이 ANSI 모드에서 열리는 경우 이러한 함수는 동일하게 작동합니다. **fscanf** 현재 UNICODE 스트림에서의 입력을 지원 하지 않습니다.

있는 이러한 함수 버전은 **_l** 은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 점을 제외 하 고 접미사는 동일 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf**|**fscanf**|**fscanf**|**fwscanf**|
|**_ftscanf_l**|**_fscanf_l**|**_fscanf_l**|**_fwscanf_l**|

자세한 내용은 참조 [형식 사양 필드-scanf 함수 및 wscanf 함수](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)합니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fscanf**, **_fscanf_l**|\<stdio.h>|
|**fwscanf**, **_fwscanf_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )
      printf( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Security caution!
      // Beware loading data from a file without confirming its size,
      // as it may lead to a buffer overrun situation.

      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf( stream, "%s", s );   // C4996
      fscanf( stream, "%ld", &l ); // C4996

      fscanf( stream, "%f", &fp ); // C4996
      fscanf( stream, "%c", &c );  // C4996
      // Note: fscanf is deprecated; consider using fscanf_s instead

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
