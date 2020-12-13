---
description: '자세히 알아보기: _fullpath, _wfullpath'
title: _fullpath, _wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: e9c02d100abc175f24194ce71627502544085f9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334152"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath, _wfullpath

지정된 상대 경로 이름의 절대 또는 전체 경로 이름을 만듭니다.

## <a name="syntax"></a>구문

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>매개 변수

*absPath*<br/>
절대 또는 전체 경로 이름이 나 **NULL** 을 포함 하는 버퍼에 대 한 포인터입니다.

*relPath*<br/>
상대 경로 이름입니다.

*maxLength*<br/>
절대 경로 이름 버퍼의 최대 길이 (*absPath*)입니다. 이 길이는 **_fullpath** 에 대 한 바이트 단위 이지만 **`wchar_t`** **_wfullpath** 의 경우 와이드 문자 ()입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 절대 경로 이름 (*absPath*)을 포함 하는 버퍼에 대 한 포인터를 반환 합니다. 오류가 있는 경우 (예: *relPath* 에 전달 된 값에 잘못 되었거나 찾을 수 없는 드라이브 문자가 포함 된 경우 또는 생성 된 절대 경로 이름 (*absPath*)의 길이가 *maxLength* 보다 큰 경우) 함수는 **NULL** 을 반환 합니다.

## <a name="remarks"></a>설명

**_Fullpath** 함수는 *relPath* 의 상대 경로 이름을 정규화 된 경로 또는 절대 경로로 확장 하 고이 이름을 *absPath* 에 저장 합니다. *AbsPath* 가 **NULL** 이면 **malloc** 를 사용 하 여 경로 이름을 저장할 수 있는 충분 한 길이의 버퍼를 할당 합니다. 호출자가 이 버퍼를 해제해야 합니다. 상대 경로 이름은 현재 위치에서 시작되는 또 다른 위치에 대한 경로를 지정합니다(예: 현재 작업 디렉터리: "."). 절대 경로 이름은 파일 시스템의 루트에서 원하는 위치에 도달하는 데 필요한 전체 경로를 설명하는 상태 경로 이름의 확장입니다. **_Makepath** 와 달리 **_fullpath** 를 사용 하 여 "./" 또는 "."가 포함 된 상대 경로 (*relPath*)의 절대 경로 이름을 가져올 수 있습니다. /"을 (를) 이름으로 합니다.

예를 들어 C 런타임 루틴을 사용하려면 루틴 선언이 들어 있는 헤더 파일을 애플리케이션에 포함해야 합니다. 각 헤더 파일의 include 문은 애플리케이션 작업 디렉터리를 기준으로 한 상대적 방식으로 파일 위치를 참조합니다.

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

파일의 절대 경로(실제 파일 시스템 위치)가 다음과 같을 경우:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** 는 멀티 바이트 문자열 인수를 자동으로 적절 하 게 처리 하 여 현재 사용 중인 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wfullpath** 은 **_fullpath** 의 와이드 문자 버전입니다. **_wfullpath** 에 대 한 문자열 인수는 와이드 문자 문자열입니다. **_wfullpath** 및 **_fullpath** 는 **_wfullpath** 에서 멀티 바이트 문자열을 처리 하지 않는다는 점만 제외 하 고 동일 하 게 동작 합니다.

**_DEBUG** 및 **_CRTDBG_MAP_ALLOC** 모두 정의 되 면 **_fullpath** 및 **_wfullpath** 에 대 한 호출이 **_fullpath_dbg** 및 **_wfullpath_dbg** 호출로 대체 되어 메모리 할당 디버깅을 허용 합니다. 자세한 내용은 [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)를 참조하세요.

*Maxlen* 가 0 보다 작거나 같으면이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **NULL** 을 반환 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

*AbsPath* 버퍼가 **NULL** 인 경우 **_fullpath** 는 [malloc](malloc.md) 를 호출 하 여 버퍼를 할당 하 고 *maxLength* 인수를 무시 합니다. 호출자는 [free](free.md)를 사용하여 이 버퍼를 적절하게 할당 해제해야 합니다. *RelPath* 인수가 디스크 드라이브를 지정 하는 경우이 드라이브의 현재 디렉터리는 경로와 결합 됩니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
