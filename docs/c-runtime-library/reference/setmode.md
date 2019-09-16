---
title: _setmode
ms.date: 11/04/2016
api_name:
- _setmode
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 7f14cc9451b93a9077916b8c650645990ba654a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948582"
---
# <a name="_setmode"></a>_setmode

파일 변환 모드를 설정합니다.

## <a name="syntax"></a>구문

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
파일 설명자입니다.

*mode*<br/>
새 변환 모드입니다.

## <a name="return-value"></a>반환 값

성공하면 이전 변환 모드를 반환합니다.

함수에 잘못된 매개 변수를 전달하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는-1을 반환 하 고 **errno** 를 **ebadf**로 설정 합니다 .이는 잘못 된 파일 설명자를 나타내는 EINVAL 이거나 잘못 된 *모드* 인수를 나타내는입니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하십시오.

## <a name="remarks"></a>설명

**_Setmode** 함수는 *fd*에서 지정 된 파일의 변환 모드를 *mode* 로 설정 합니다. **_O_text** 를 *모드로* 전달 하면 텍스트 (즉, 변환 된) 모드가 설정 됩니다. 입력 시 캐리지 리턴-줄 바꿈 (CR-LF) 조합이 단일 줄 바꿈 문자로 변환 됩니다. 줄 바꿈 문자는 출력 시 CR-LF 조합으로 변환됩니다. **_O_binary** 를 전달 하면 이러한 변환이 억제 되는 이진 (변환 되지 않은) 모드가 설정 됩니다.

이 문서의 뒷부분에 나오는 두 번째 예제에서 설명 하는 것 처럼 유니코드 모드를 사용 하도록 설정 하려면 **_O_u16text**, **_o_u16text**또는 **_o_wtext** 를 전달할 수도 있습니다.

> [!CAUTION]
> 유니코드 모드는 와이드 인쇄 기능 (예: `wprintf`)을 위한 것 이며 좁은 인쇄 함수에는 지원 되지 않습니다. 유니코드 모드 스트림에서 좁은 인쇄 함수를 사용 하면 어설션이 트리거됩니다.

**_setmode** 는 일반적으로 **stdin** 및 **stdout**의 기본 변환 모드를 수정 하는 데 사용 되지만 모든 파일에서 사용할 수 있습니다. 스트림의 파일 설명자에 **_setmode** 를 적용 하는 경우 스트림에 대 한 입력 또는 출력 작업을 수행 하기 전에 **_setmode** 를 호출 합니다.

> [!CAUTION]
> 파일 스트림에 데이터를 쓰는 경우 **_setmode** 를 사용 하 여 모드를 변경 하기 전에 [fflush](fflush.md) 를 사용 하 여 코드를 명시적으로 플러시합니다. 코드를 플러시하지 않은 경우 예기치 않은 동작이 발생할 수 있습니다. 스트림에 데이터를 쓰지 않을 경우 코드를 플러시할 필요가 없습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>예제

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>참고자료

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
