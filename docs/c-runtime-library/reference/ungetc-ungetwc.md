---
description: '자세한 정보: ungetc, ungetwc'
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: c212f67bb72253bf37428d494e33bef0eedc2550
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186586"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

스트림에 문자를 다시 푸시합니다.

## <a name="syntax"></a>구문

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
푸시할 문자 수입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

성공 하는 경우 이러한 각 함수는 문자 인수 *c* 를 반환 합니다. *C* 를 다시 푸시할 수 없거나 문자를 읽지 않은 경우 입력 스트림은 변경 되지 않으며 **Ungetc** 는 **EOF** 를 반환 합니다. **Ungetwc** **는 weof를** 반환 합니다. *Stream* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **EOF** 또는 **weof** 가 반환 되 고 **errno** 가 **EINVAL** 로 설정 됩니다.

이러한 오류 코드 및 기타 오류 코드에 대한 내용은 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**Ungetc** 함수는 *c* 문자를 다시 *스트림으로* 푸시하고 파일 끝 표시기를 지웁니다. 이때 스트림이 읽기를 위해 열려 있어야 합니다. *스트림에서* 후속 읽기 작업은 *c* 로 시작 합니다. **Ungetc** 를 사용 하는 스트림으로 **EOF** 를 푸시하는 시도는 무시 됩니다.

스트림에서 문자를 읽기 전에 **fflush**, [fseek](fseek-fseeki64.md), **fsetpos** 또는 [되감기](rewind.md) 가 호출 되 면 **ungetc** 에 의해 스트림에 배치 된 문자가 지워질 수 있습니다. 파일 위치 표시기에는 문자가 다시 푸시되기 전의 값이 지정됩니다. 스트림에 해당하는 외부 스토리지는 변경되지 않습니다. 텍스트 스트림에 대해 성공한 **getc** 호출에서 모든 푸시 문자를 읽거나 삭제할 때까지 파일 위치 표시기는 지정 되지 않습니다. 이진 스트림에 대해 각 성공한 **getc** 호출에서 파일 위치 표시기가 감소 합니다. 호출 전에 해당 값이 0 이면 호출 후에 값이 정의 되지 않습니다.

두 호출 사이에 읽기 또는 파일 위치 지정 작업 없이 **ungetc** 를 두 번 호출 하는 경우 결과를 예측할 수 없습니다. **Fscanf** 를 호출한 후에는 다른 읽기 작업 (예: **getc**)을 수행 하지 않으면 **ungetc** 에 대 한 호출이 실패할 수 있습니다. **Fscanf** 자체가 **ungetc** 를 호출 하기 때문입니다.

**ungetwc** 는 **ungetc** 의 와이드 문자 버전입니다. 그러나 텍스트 또는 이진 스트림에 대해 성공한 각 **ungetwc** 호출에서는 모든 푸시 문자를 읽거나 삭제할 때까지 파일 위치 표시기의 값이 지정 되지 않습니다.

이러한 함수는 스레드로부터 안전하며, 실행 중에 중요한 데이터를 잠급니다. 데이터를 잠그지 않는 버전은 [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
