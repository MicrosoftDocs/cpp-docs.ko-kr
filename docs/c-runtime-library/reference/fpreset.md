---
description: '다음에 대 한 자세한 정보: _fpreset'
title: _fpreset
ms.date: 04/05/2018
api_name:
- _fpreset
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fpreset
- fpreset
helpviewer_keywords:
- fpreset function
- floating-point numbers, resetting math package
- _fpreset function
ms.assetid: f31c6a04-b464-4f07-a7c4-42133360e328
ms.openlocfilehash: 7818e0f02f6165c5041245e342a81b1dde25b091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178695"
---
# <a name="_fpreset"></a>_fpreset

부동 소수점 패키지를 다시 설정합니다.

## <a name="syntax"></a>구문

```C
void _fpreset( void );
```

## <a name="remarks"></a>설명

**_Fpreset** 함수는 부동 소수점 수학 패키지를 다시 초기화 합니다. **_fpreset** 은 일반적으로 **신호**, **시스템** 또는 **_exec** 또는 **_spawn** 함수와 함께 사용 됩니다. 프로그램이 **신호** 를 사용 하 여 부동 소수점 오류 신호 (**SIGFPE**)를 트래핑 하는 경우 **_fpreset** 를 호출 하 고 고가를 사용 하 여 부동 소수점 오류를 안전 하 게 복구할 수 있습니다.

공용 언어 런타임이 기본 부동 소수점 전체 자릿수를 지원 하기 때문에 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일할 때이 함수는 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fpreset**|\<float.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fpreset.c
// This program uses signal to set up a
// routine for handling floating-point errors.

#include <stdio.h>
#include <signal.h>
#include <setjmp.h>
#include <stdlib.h>
#include <float.h>
#include <math.h>
#include <string.h>

jmp_buf mark;              // Address for long jump to jump to
int     fperr;             // Global error number

void __cdecl fphandler( int sig, int num );   // Prototypes
void fpcheck( void );

int main( void )
{
   double n1 = 5.0;
   double n2 = 0.0;
   double r;
   int jmpret;

   // Unmask all floating-point exceptions.
    _control87( 0, _MCW_EM );
   // Set up floating-point error handler. The compiler
   // will generate a warning because it expects
   // signal-handling functions to take only one argument.
   if( signal( SIGFPE, (void (__cdecl *)(int)) fphandler ) == SIG_ERR )
    {
       fprintf( stderr, "Couldn't set SIGFPE\n" );
       abort();
    }

   // Save stack environment for return in case of error. First
   // time through, jmpret is 0, so true conditional is executed.
   // If an error occurs, jmpret will be set to -1 and false
   // conditional will be executed.
   jmpret = setjmp( mark );
   if( jmpret == 0 )
   {
      printf( "Dividing %4.3g by %4.3g...\n", n1, n2 );
      r = n1 / n2;
      // This won't be reached if error occurs.
      printf( "\n\n%4.3g / %4.3g = %4.3g\n", n1, n2, r );

      r = n1 * n2;
      // This won't be reached if error occurs.
      printf( "\n\n%4.3g * %4.3g = %4.3g\n", n1, n2, r );
   }
   else
      fpcheck();
}
// fphandler handles SIGFPE (floating-point error) interrupt. Note
// that this prototype accepts two arguments and that the
// prototype for signal in the run-time library expects a signal
// handler to have only one argument.
//
// The second argument in this signal handler allows processing of
// _FPE_INVALID, _FPE_OVERFLOW, _FPE_UNDERFLOW, and
// _FPE_ZERODIVIDE, all of which are Microsoft-specific symbols
// that augment the information provided by SIGFPE. The compiler
// will generate a warning, which is harmless and expected.

void fphandler( int sig, int num )
{
   // Set global for outside check since we don't want
   // to do I/O in the handler.
   fperr = num;

   // Initialize floating-point package. */
   _fpreset();

   // Restore calling environment and jump back to setjmp. Return
   // -1 so that setjmp will return false for conditional test.
   longjmp( mark, -1 );
}

void fpcheck( void )
{
   char fpstr[30];
   switch( fperr )
   {
   case _FPE_INVALID:
       strcpy_s( fpstr, sizeof(fpstr), "Invalid number" );
       break;
   case _FPE_OVERFLOW:
       strcpy_s( fpstr, sizeof(fpstr), "Overflow" );

       break;
   case _FPE_UNDERFLOW:
       strcpy_s( fpstr, sizeof(fpstr), "Underflow" );
       break;
   case _FPE_ZERODIVIDE:
       strcpy_s( fpstr, sizeof(fpstr), "Divide by zero" );
       break;
   default:
       strcpy_s( fpstr, sizeof(fpstr), "Other floating point error" );
       break;
   }
   printf( "Error %d: %s\n", fperr, fpstr );
}
```

```Output
Dividing    5 by    0...
Error 131: Divide by zero
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
