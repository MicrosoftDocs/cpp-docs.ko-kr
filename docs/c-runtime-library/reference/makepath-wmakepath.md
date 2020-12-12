---
description: '자세히 알아보기: _makepath, _wmakepath'
title: _makepath, _wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: 2193c9fafdfea5fbacfef69256e5fd1fbfaf9828
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299841"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

구성 요소에서 경로 이름을 만듭니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>매개 변수

*path*<br/>
전체 경로 버퍼입니다.

*드라이브나*<br/>
원하는 드라이브에 따른 문자(A, B 등) 및 후행 콜론(선택 사항)을 포함합니다. **_makepath** 는 복합 경로에 콜론을 자동으로 삽입 합니다 (없는 경우). *드라이브가* **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 드라이브 문자가 나타나지 않습니다.

*dir*<br/>
드라이브 지정자 또는 실제 파일 이름을 제외한 디렉터리의 경로를 포함합니다. 후행 슬래시는 선택 사항이 며 슬래시 (/) 또는 백슬래시 () 중 하나 \\ 또는 둘 다를 단일 *dir* 인수에 사용할 수 있습니다. 후행 슬래시(/ 또는 \\)가 지정되지 않은 경우 자동으로 삽입됩니다. *Dir* 이 **NULL** 이거나 빈 문자열을 가리키는 경우에는 복합 *경로* 문자열에 디렉터리 경로가 삽입 되지 않습니다.

*fname*<br/>
파일 확장명 없이 기본 파일 이름을 포함합니다. *Fname* 이 **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 파일 이름이 삽입 되지 않습니다.

*확장*<br/>
앞에 마침표(.)가 있거나 없는 실제 파일 확장명을 포함합니다. **_makepath** 은 *ext* 에 표시 되지 않는 경우 자동으로 마침표를 삽입 합니다. *Ext* 가 **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 확장명이 삽입 되지 않습니다.

## <a name="remarks"></a>설명

**_Makepath** 함수는 개별 구성 요소에서 복합 경로 문자열을 만들어 *경로* 에 결과를 저장 합니다. *경로* 에는 드라이브 문자, 디렉터리 경로, 파일 이름 및 파일 이름 확장명이 포함 될 수 있습니다. **_wmakepath** 은 **_makepath** 의 와이드 문자 버전입니다. **_wmakepath** 인수는 와이드 문자 문자열입니다. **_wmakepath** 와 **_makepath** 는 동일 하 게 동작 합니다.

**보안 정보** null로 끝나는 문자열을 사용하세요. 버퍼 오버런을 방지 하려면 null로 끝나는 문자열이 *경로* 버퍼의 크기를 초과 하면 안 됩니다. **_makepath** 는 복합 경로 문자열의 길이가 **_MAX_PATH** 를 초과 하지 않는지 확인 하지 않습니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*경로* 인수는 전체 경로를 포함할 수 있을 만큼 크고 빈 버퍼를 가리켜야 합니다. 복합 *경로* 는 stdlib.h에 정의 된 **_MAX_PATH** 상수 보다 크지 않아야 합니다.

Path가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 또한 **errno** 는 **EINVAL** 로 설정 됩니다. 다른 모든 매개 변수에 **NULL** 값을 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
