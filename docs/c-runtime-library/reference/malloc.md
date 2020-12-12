---
description: '자세히 알아보기: malloc'
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: 8026cf24ee49999026c58787b83b2c8c0a238a2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299789"
---
# <a name="malloc"></a>malloc

메모리 블록을 할당합니다.

## <a name="syntax"></a>구문

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
할당할 바이트입니다.

## <a name="return-value"></a>반환 값

**malloc** 은 할당 된 공간에 대 한 void 포인터를 반환 하거나 사용 가능한 메모리가 부족 한 경우 **NULL** 을 반환 합니다. 이외의 형식에 대 한 포인터를 반환 하려면 **`void`** 반환 값에 형식 캐스팅을 사용 합니다. 반환 값이 가리키는 스토리지 공간은 맞춤 요구 사항이 기본 맞춤보다 작거나 같은 모든 형식의 개체 스토리지에 적절하게 맞춰지도록 보장됩니다. Visual C++ 기본 맞춤은 또는 8 바이트에 필요한 맞춤입니다 **`double`** . 64 비트 플랫폼을 대상으로 하는 코드에서는 16 바이트입니다. [_Aligned_malloc](aligned-malloc.md) 를 사용 하 여 맞춤 요구 사항이 더 큰 개체에 대 한 저장소를 할당 합니다. 예를 들어, 및의 SSE [__m128](../../cpp/m128.md) 형식과 **`__m256`** 를 사용 하 여 선언 된 형식 ( `__declspec(align( n ))` 여기서 **n** 은 8 보다 큼)이 있습니다. *Size* 가 0 인 경우 **malloc** 는 힙에서 길이가 0 인 항목을 할당 하 고 해당 항목에 대 한 유효한 포인터를 반환 합니다. 요청 된 메모리 양이 적은 경우에도 항상 **malloc** 에서 반환을 확인 합니다.

## <a name="remarks"></a>설명

**Malloc** 함수는 최소 *크기* 바이트의 메모리 블록을 할당 합니다. 맞춤 및 유지 관리 정보에 필요한 공간 때문에 블록은 *크기* 바이트 보다 클 수 있습니다.

메모리 할당이 실패 하거나 요청 된 메모리 양이 **_HEAP_MAXREQ** 을 초과 하는 경우 **malloc** 은 **errno** 를 **enomem** 으로 설정 합니다. 이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

시작 코드는 **malloc** 를 사용 하 여 **_environ**, *envp* 및 *argv* 변수에 대 한 저장소를 할당 합니다. 다음 함수와 해당 와이드 문자는 **malloc** 도 호출 합니다.

:::row:::
   :::column span="":::
      [calloc](calloc.md)\
      [_exec 함수](../../c-runtime-library/exec-wexec-functions.md)\
      [fgetc](fgetc-fgetwc.md)\
      [_fgetchar](fgetc-fgetwc.md)\
      [fgets](fgets-fgetws.md)\
      [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)\
      [fputc](fputc-fputwc.md)\
      [_fputchar](fputc-fputwc.md)\
      [fputs](fputs-fputws.md)\
      [fread](fread.md)
   :::column-end:::
   :::column span="":::
      [fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)\
      [fseek](fseek-fseeki64.md)\
      [fsetpos](fsetpos.md)\
      [_fullpath](fullpath-wfullpath.md)\
      [fwrite](fwrite.md)\
      [getc](getc-getwc.md)\
      [getchar](getc-getwc.md)\
      [_getcwd](getcwd-wgetcwd.md)\
      [_getdcwd](getcwd-wgetcwd.md)\
      [가져옵니다](../../c-runtime-library/gets-getws.md)
   :::column-end:::
   :::column span="":::
      [_getw](getw.md)\
      [_popen](popen-wpopen.md)\
      [printf](printf-printf-l-wprintf-wprintf-l.md)\
      [putc](putc-putwc.md)\
      [putchar](putc-putwc.md)\
      [_putenv](putenv-wputenv.md)\
      [설정](puts-putws.md)\
      [_putw](putw.md)\
      [scanf](scanf-scanf-l-wscanf-wscanf-l.md)
   :::column-end:::
   :::column span="":::
      [_searchenv](searchenv-wsearchenv.md)\
      [setvbuf](setvbuf.md)\
      [_spawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)\
      [_strdup](strdup-wcsdup-mbsdup.md)\
      [컴퓨터](system-wsystem.md)\
      [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)\
      [ungetc](ungetc-ungetwc.md)\
      [vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
      [vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)
   :::column-end:::
:::row-end:::

C++ [_set_new_mode](set-new-mode.md) 함수는 **malloc** 에 대한 새 처리기 모드를 설정합니다. 새 처리기 모드는 실패 시 **malloc** 가 [_set_new_handler](set-new-handler.md)에 의해 설정 된 대로 새 처리기 루틴을 호출 하는지 여부를 나타냅니다. 기본적으로 **malloc** 은 메모리 할당 실패 시 새 처리기 루틴을 호출 하지 않습니다. 이 기본 동작을 재정의 하 여 **malloc** 에서 메모리를 할당 하지 못할 때 **malloc** 이 **`new`** 연산자가 같은 이유로 실패 했을 때와 동일한 방식으로 새 처리기 루틴을 호출 하도록 할 수 있습니다. 기본값을 재정의 하려면 `_set_new_mode(1)` 프로그램에서 조기에 호출 하거나 NEWMODE를 사용 하 여 연결 합니다. OBJ ( [링크 옵션](../../c-runtime-library/link-options.md)참조).

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **malloc** 는 [_malloc_dbg](malloc-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

**malloc** 는 및로 표시 됩니다 `__declspec(noalias)` `__declspec(restrict)` .이는 함수가 전역 변수를 수정 하지 않도록 보장 하 고 반환 된 포인터에 별칭이 지정 되지 않음을 의미 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**malloc**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_malloc.c
// This program allocates memory with
// malloc, then frees the memory with free.

#include <stdlib.h>   // For _MAX_PATH definition
#include <stdio.h>
#include <malloc.h>

int main( void )
{
   char *string;

   // Allocate space for a path name
   string = malloc( _MAX_PATH );

   // In a C++ file, explicitly cast malloc's return.  For example,
   // string = (char *)malloc( _MAX_PATH );

   if( string == NULL )
      printf( "Insufficient memory available\n" );
   else
   {
      printf( "Memory space allocated for path name\n" );
      free( string );
      printf( "Memory freed\n" );
   }
}
```

```Output
Memory space allocated for path name
Memory freed
```

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
