---
description: '자세한 정보: fgets, fgetws'
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 21c360f621ed19f076af129f618e80aa27102e86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329301"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

스트림에서 문자열을 가져옵니다.

## <a name="syntax"></a>구문

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
데이터의 스토리지 위치입니다.

*numChars*<br/>
읽을 최대 문자 수입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 *str* 을 반환 합니다. 오류 또는 파일 끝 조건을 나타내기 위해 **NULL** 이 반환 됩니다. **Feof** **ferror** 를 사용 하 여 오류가 발생 했는지 여부를 확인 합니다. *Str* 또는 *stream* 이 null 포인터 이거나 *numChars* 가 0 보다 작거나 같으면이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **NULL** 을 반환 합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**Fgets** 함수는 입력 *스트림* 인수에서 문자열을 읽어 *str* 에 저장 합니다. **fgets** 는 현재 스트림 위치에서 첫 번째 줄 바꿈 문자를 포함 하 여 스트림의 끝까지 또는 읽은 문자 수가 *numChars* -1과 같을 때까지 (둘 중 먼저 도달할 때까지) 문자를 가져옵니다. *Str* 에 저장 된 결과는 null 문자와 함께 추가 됩니다. 줄 바꿈 문자는 읽을 경우 문자열에 포함됩니다.

**fgetws** 는 **fto** 의 와이드 문자 버전입니다.

**fgetws** 는 *스트림을* 텍스트 모드에서 열지 아니면 이진 모드로 열지에 따라 와이드 문자 인수 *str* 를 멀티 바이트 문자열 또는 와이드 문자열로 읽습니다. 텍스트 및 이진 모드를 유니코드 및 멀티바이트 스트림 I/O에서 사용하는 방법에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 및 [텍스트 및 이진 모드의 유니코드 스트림 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>입력 crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>출력

```Output
Line one.
```

## <a name="see-also"></a>참조

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
