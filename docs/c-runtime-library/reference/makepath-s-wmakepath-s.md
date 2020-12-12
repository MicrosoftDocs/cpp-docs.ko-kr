---
description: '자세히 알아보기: _makepath_s, _wmakepath_s'
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 8096061c80c2cfb7da3148e1ba8e7a0d2f193c4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299906"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

구성 요소에서 경로 이름을 만듭니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [_makepath, _wmakepath](makepath-wmakepath.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>매개 변수

*path*<br/>
전체 경로 버퍼입니다.

*sizeInWords*<br/>
버퍼의 크기(워드)입니다.

*sizeInBytes*<br/>
버퍼의 크기(바이트)입니다.

*드라이브나*<br/>
원하는 드라이브에 따른 문자(A, B 등) 및 후행 콜론(선택 사항)을 포함합니다. **_makepath_s** 는 복합 경로에 콜론을 자동으로 삽입 합니다 (없는 경우). *드라이브가* **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 드라이브 문자가 나타나지 않습니다.

*dir*<br/>
드라이브 지정자 또는 실제 파일 이름을 제외한 디렉터리의 경로를 포함합니다. 후행 슬래시는 선택 사항이 며 슬래시 (/) 또는 백슬래시 () 중 하나 \\ 또는 둘 다를 단일 *dir* 인수에 사용할 수 있습니다. 후행 슬래시(/ 또는 \\)가 지정되지 않은 경우 자동으로 삽입됩니다. *Dir* 이 **NULL** 이거나 빈 문자열을 가리키는 경우에는 복합 *경로* 문자열에 디렉터리 경로가 삽입 되지 않습니다.

*fname*<br/>
파일 확장명 없이 기본 파일 이름을 포함합니다. *Fname* 이 **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 파일 이름이 삽입 되지 않습니다.

*확장*<br/>
앞에 마침표(.)가 있거나 없는 실제 파일 확장명을 포함합니다. **_makepath_s** 은 *ext* 에 표시 되지 않는 경우 자동으로 마침표를 삽입 합니다. *Ext* 가 **NULL** 이거나 빈 문자열을 가리키는 경우 복합 *경로* 문자열에 확장명이 삽입 되지 않습니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다.

### <a name="error-conditions"></a>오류 조건

|*path*|*Sizeinwords*  /  *Sizeinbytes*|반환 값|*경로의* 내용|
|------------|------------------------------------|------------|------------------------|
|**NULL**|any|**EINVAL**|수정 안 됨|
|any|<= 0|**EINVAL**|수정 안 됨|

위의 오류 조건이 발생하는 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **EINVAL** 로 설정 되 고 함수는 **EINVAL** 를 반환 합니다. *Drive*, *fname* 및 *ext* 매개 변수에는 **NULL** 을 사용할 수 있습니다. 이러한 매개 변수가 null 포인터 이거나 빈 문자열인 경우의 동작에 대 한 자세한 내용은 설명 부분을 참조 하세요.

## <a name="remarks"></a>설명

**_Makepath_s** 함수는 개별 구성 요소에서 복합 경로 문자열을 만들어 *경로* 에 결과를 저장 합니다. *경로* 에는 드라이브 문자, 디렉터리 경로, 파일 이름 및 파일 이름 확장명이 포함 될 수 있습니다. **_wmakepath_s** 은 **_makepath_s** 의 와이드 문자 버전입니다. **_wmakepath_s** 인수는 와이드 문자 문자열입니다. **_wmakepath_s** 와 **_makepath_s** 는 동일 하 게 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*경로* 인수는 전체 경로를 포함할 수 있을 만큼 크고 빈 버퍼를 가리켜야 합니다. 복합 *경로* 는 stdlib.h에 정의 된 **_MAX_PATH** 상수 보다 크지 않아야 합니다.

Path가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 또한 **errno** 는 **EINVAL** 로 설정 됩니다. 다른 모든 매개 변수에 **NULL** 값을 사용할 수 있습니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
