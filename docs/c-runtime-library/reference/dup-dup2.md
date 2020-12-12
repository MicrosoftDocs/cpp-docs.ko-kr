---
description: '자세히 알아보기: _dup, _dup2'
title: _dup, _dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: e9801cc11b6d7a8d4250f61780c5c9b23dd3e1ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327008"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

열려 있는 파일 (**_dup**)에 대 한 두 번째 파일 설명자를 만들거나 파일 설명자 (**_dup2**)를 다시 할당 합니다.

## <a name="syntax"></a>구문

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>매개 변수

*fd*, *f*<br/>
열려 있는 파일을 나타내는 파일 설명자입니다.

*fd2*<br/>
모든 파일 설명자입니다.

## <a name="return-value"></a>반환 값

**_dup** 새 파일 설명자를 반환 합니다. **_dup2** 는 성공을 나타내는 0을 반환 합니다. 오류가 발생 하는 경우 각 함수는-1을 반환 하 고, 파일 설명자가 잘못 된 경우 **errno** 를 **ebadf** 로 설정 하 고, 더 이상 파일 설명자를 사용할 수 없으면 **emfile** 로 설정 합니다. 잘못된 파일 설명자의 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 이 함수는 잘못된 매개 변수 처리기를 호출합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Dup** 및 **_dup2** 함수는 두 번째 파일 설명자를 현재 열려 있는 파일과 연결 합니다. 이러한 함수를 사용 하 여 **stdout** 의 경우와 같은 미리 정의 된 파일 설명자를 다른 파일로 연결할 수 있습니다. 파일 설명자 중 하나를 사용하여 파일 작업을 수행할 수 있습니다. 파일에 허용된 액세스 형식은 새 설명자 만들기의 영향을 받지 않습니다. **_dup** 는 지정 된 파일에 대해 사용 가능한 다음 파일 설명자를 반환 합니다. **_dup2** *fd2* 가 *f* 과 동일한 파일을 참조 하도록 합니다. 호출 시 열려 있는 파일과 연결 된 *fd2* 경우 해당 파일이 닫힙니다.

**_Dup** 및 **_dup2** 둘 다 파일 설명자를 매개 변수로 허용 합니다. 이러한 함수 중 하나에 스트림 ()을 전달 하려면 `FILE *` [_fileno](fileno.md)을 사용 합니다. **Fileno** 루틴은 지정 된 스트림과 현재 연결 된 파일 설명자를 반환 합니다. 다음 예제에서는 **stderr** (stdio.h에서로 정의 됨 `FILE *` )를 파일 설명자와 연결 하는 방법을 보여 줍니다.

```C
int cstderr = _dup( _fileno( stderr ));
```

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>참고 항목

[하위 수준 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
