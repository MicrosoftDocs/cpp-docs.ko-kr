---
title: _popen, _wpopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _popen
- _wpopen
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
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
dev_langs:
- C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a0dd4f32f8c7b3a9e859e23fcc26e668fa87cdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726364"
---
# <a name="popen-wpopen"></a>_popen, _wpopen

파이프를 만들고 명령을 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>매개 변수

*command*<br/>
실행할 명령입니다.

*모드*<br/>
반환된 스트림의 모드입니다.

## <a name="return-value"></a>반환 값

생성된 파이프의 한쪽 끝와 연결된 스트림을 반환합니다. 파이프의 반대쪽은 생성된 명령의 표준 입력 또는 표준 출력에 연결됩니다. 오류가 발생하면 함수는 **NULL**을 반환합니다. 오류 경우와 같이 잘못 된 매개 변수 이면 *명령* 하거나 *모드* 가 null 포인터인 경우 또는 *모드* 올바른 모드가 아닙니다 **errno** 로 설정 되어 **EINVAL**합니다. 올바른 모드는 설명 섹션을 참조하세요.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

합니다 **_popen** 함수는 파이프를 만들고 지정된 된 문자열을 사용 하 여 명령 프로세서의 생성된 된 복사본을 비동기적으로 실행 *명령*입니다. 문자열의 *mode*는 다음과 같이 요청된 액세스의 유형을 지정합니다.

|액세스 모드|설명|
|-|-|
|**"r"**|호출 프로세스가 반환된 스트림을 사용하여 생성된 명령의 표준 출력을 읽을 수 있습니다.|
|**"w"**|호출 프로세스가 반환된 스트림을 사용하여 생성된 명령의 표준 입력에 쓸 수 있습니다.|
|**"b"**|이진 모드에서 엽니다.|
|**"t"**|텍스트 모드에서 엽니다.|

> [!NOTE]
> Windows 프로그램에서 사용 하는 경우는 **_popen** 함수는 프로그램이 무기한 응답을 중지 하는 잘못 된 파일 포인터를 반환 합니다. **_popen** 콘솔 응용 프로그램에서 제대로 작동 합니다. 입력 및 출력을 리디렉션하는 Windows 응용 프로그램을 참조 하세요 [리디렉션된 입력 및 출력을 사용 하 여 자식 프로세스 만들기](/windows/desktop/ProcThread/creating-a-child-process-with-redirected-input-and-output) Windows SDK에 있습니다.

**_wpopen** 의 와이드 문자 버전이 **_popen**; *경로* 인수 **_wpopen** 는 와이드 문자 문자열입니다. **_wpopen** 하 고 **_popen** 동일 하 게 작동 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      printf(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

### <a name="sample-output"></a>샘플 출력

이 출력에서는 현재 디렉터리에 .c 파일 이름 확장명의 파일이 하나만 있다고 가정합니다.

```Output
 Volume in drive C is CDRIVE
 Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

 07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>참고자료

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
