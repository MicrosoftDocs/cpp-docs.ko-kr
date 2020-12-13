---
description: '자세히 알아보기: _fgetchar, _fgetwchar'
title: _fgetchar, _fgetwchar
ms.date: 4/2/2020
api_name:
- _fgetchar
- _fgetwchar
- _o__fgetchar
- _o__fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 316948485e0ef024bc726da7f333fd4ee329c7f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151816"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

**Stdin** 에서 문자를 읽습니다.

## <a name="syntax"></a>구문

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Return Value

**\_ fgetchar** 는로 읽은 문자를 반환 **`int`** 하거나, `EOF` 오류 또는 파일의 끝을 나타내기 위해를 반환 합니다. **\_ fgetwchar** 는 [](../../c-runtime-library/standard-types.md) `WEOF` 파일의 오류 또는 끝을 나타내기 위해 읽기 또는 반환 된 문자에 해당 하는 와이드 문자를 wint_t 반환 합니다. 두 함수 모두에서 **feof** **ferror** 를 사용 하 여 오류와 파일 끝 조건을 구분 합니다.

## <a name="remarks"></a>설명

이러한 함수는 **stdin** 에서 단일 문자를 읽습니다. 그러고 나서 다음 문자를 가리킬 연결된 파일 포인터(정의된 경우)를 늘립니다. 스트림이 파일 끝에 있는 경우 스트림에 대한 파일 끝 표시기가 설정됩니다.

**_fgetchar** 는와 동일 `fgetc( stdin )` 합니다. **Getchar** 와 동일 하지만 함수 및 매크로가 아닌 함수로만 구현 됩니다. **_fgetwchar** 은 **_fgetchar** 의 와이드 문자 버전입니다.

이러한 함수는 ANSI 표준과 호환되지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔에 연결 된 표준 스트림 핸들 (**stdin**, **stdout** 및 **stderr**)은 C 런타임 함수가 UWP 앱에서 사용할 수 있도록 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
