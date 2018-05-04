---
title: _fsopen, _wfsopen | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce69c6789ba65f61c54957dde3dfa6965bc32e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen

파일 공유를 사용한 스트림을 엽니다.

## <a name="syntax"></a>구문

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
열 파일의 이름입니다.

*모드*<br/>
허용되는 액세스 형식입니다.

*shflag*<br/>
허용되는 공유 유형입니다.

## <a name="return-value"></a>반환 값

각 함수는 스트림에 대한 포인터를 반환합니다. null 포인터 값은 오류를 나타냅니다. 경우 *filename* 또는 *모드* 은 **NULL** 빈 문자열인 경우 이러한 함수를 호출 하거나 잘못 된 매개 변수 처리기에 설명 된 대로 [매개 변수 유효성 검사 ](../../c-runtime-library/parameter-validation.md). 실행을 계속 허용 된 경우 이러한 함수가 반환 **NULL** 설정 **errno** 를 **EINVAL**합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_fsopen** 함수에서 지정한 파일을 열고 *filename* 스트림으로 모드에 의해 정의 된 대로 후속 공유 읽기 또는 쓰기를 위해 파일을 준비 및 *shflag*인수입니다. **_wfsopen** 의 와이드 문자 버전이 **_fsopen**; *filename* 및 *모드* 에 대 한 인수 **_wfsopen** 됩니다 와이드 문자 문자열입니다. **_wfsopen** 및 **_fsopen** 동일 하 게 작동 합니다.

문자열 *모드* 다음 표에 나와 있는 것 처럼 파일에 대해 요청 된 액세스의 유형을 지정 합니다.

|용어|정의|
|----------|----------------|
|**"r"**|읽기 위해 엽니다. 파일이 존재 하지 않거나 찾을 수 없는 경우는 **_fsopen** 호출이 실패 합니다.|
|**"w"**|쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다.|
|**"a"**|파일 끝에 쓰기(추가) 위해 엽니다. 파일이 존재하지 않는 경우 먼저 파일을 만듭니다.|
|**"r+"**|읽고 쓰기 위해 엽니다. 파일이 있어야 합니다.|
|**"w+"**|읽고 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다.|
|**"a+"**|읽기 및 추가를 위해 엽니다. 파일이 존재하지 않는 경우 먼저 파일을 만듭니다.|

사용 하 여는 **"w"** 및 **"w +"** 기존 파일을 제거할 수 있으므로 신중 하 게 입력 합니다.

와 파일이 열릴 때의 **"a"** 또는 **"a +"** 액세스 형식을 모든 쓰기 작업이 파일의 끝에서 발생 합니다. 파일 포인터 위치를 변경할 수를 사용 하 여 [fseek](fseek-fseeki64.md) 또는 [되감기](rewind.md), 항상 이동 다시 파일의 끝에 쓰기 작업을 수행 하기 전에 하지만 합니다. 따라서 기존 데이터를 덮어쓸 수 없습니다. 경우는 **"r +"**, **"w +"**, 또는 **"a +"** 액세스 형식을 지정한 경우 읽기와 쓰기가 모두 허용 됩니다 (업데이트에 대 한 열려 있어야 합니다, 파일이 업데이트용). 그러나 읽기와 쓰기를 전환할 때는 먼저 [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) 또는 [rewind](rewind.md) 작업이 있어야 합니다. 에 대 한 현재 위치를 지정할 수는 [fsetpos](fsetpos.md) 또는 [fseek](fseek-fseeki64.md) 작업을 원하는 경우. 위의 값 외에 다음 문자 중 하나에 포함 될 수 *모드* 새 줄에 대해 및 파일 관리에 대 한 변환 모드를 지정할 수 있습니다.

|용어|정의|
|----------|----------------|
|**t**|파일을 텍스트(변환됨) 모드에서 엽니다. 이 모드에서 캐리지 리턴-줄 바꿈된 (CR-LF) 조합은 입력 시 단일 lf (줄)으로 변환 됩니다 및 LF 문자는 출력 시 CR-LF 조합으로 변환 합니다. 또한 CTRL+Z는 입력 시 파일 끝 문자로 변환됩니다. 읽기 또는 읽기/쓰기 위해 열려 있는 파일에서 **_fsopen** 파일의 끝에 CTRL + Z가 있는지 확인 하 고 가능한 경우이 제거 합니다. 사용 하 여 때문에 이렇게 [fseek](fseek-fseeki64.md) 및 [ftell](ftell-ftelli64.md) CTRL + Z로 끝나는 않을 파일 내에서 이동할 [fseek](fseek-fseeki64.md) 파일의 끝 부분에서 제대로 동작 하지 합니다.|
|**b**|이진(변환되지 않은) 모드에서 파일을 엽니다. 위에서 설명한 변환은 표시되지 않습니다.|
|**S**|캐싱이 디스크에서 순차적 액세스를 위해 최적화되며 이에 제한되지 않습니다.|
|**R**|캐싱이 디스크에서 임의 액세스를 위해 최적화되며 이에 제한되지 않습니다.|
|**T**|파일을 임시 파일로 지정합니다. 가능하면 디스크에 플러시되지 않습니다.|
|**D**|파일을 임시 파일로 지정합니다. 마지막 파일 포인터를 닫을 때 삭제됩니다.|

*mode*에 **t** 또는 **b**가 지정되지 않은 경우 변환 모드는 기본 모드 변수 **_fmode**로 정의됩니다. 경우 **t** 또는 **b** 맨 앞에 인수, 함수 실패 및 반환 **NULL**합니다. 텍스트 모드와 이진 모드에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)를 참조하세요.

인수 *shflag* 는 Share.h에 정의 된 다음 매니페스트 상수 중 하나로 구성 된 상수 식입니다.

|용어|정의|
|----------|----------------|
|**_SH_COMPAT**|16비트 응용 프로그램에 대한 호환성 모드를 설정합니다.|
|**_SH_DENYNO**|읽기 및 쓰기 액세스 권한을 허용합니다.|
|**_SH_DENYRD**|파일에 대한 읽기 권한을 거부합니다.|
|**_SH_DENYRW**|파일에 대한 읽기 및 쓰기 권한을 거부합니다.|
|**_SH_DENYWR**|파일에 대한 쓰기 권한을 거부합니다.|

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> 에 대 한 매니페스트 상수에 대 한 *shflag* 매개 변수입니다.|
|**_wfsopen**|\<stdio.h> 또는 \<wchar.h>|\<share.h><br /><br /> 에 대 한 매니페스트 상수에 대 한 *shflag* 매개 변수입니다.|

## <a name="example"></a>예제

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
