---
description: '자세한 정보: 파일 처리'
title: 파일 처리
ms.date: 11/04/2016
f1_keywords:
- c.files
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
ms.openlocfilehash: 5727f2c4f1d0d79a471b8ec5a76ed719380e2d83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135774"
---
# <a name="file-handling"></a>파일 처리

이러한 루틴을 사용하여 파일을 만들고 삭제하고 조작하며 파일 액세스 권한을 설정하고 확인합니다.

C 런타임 라이브러리에서는 한 번에 열 수 있는 파일의 수가 512개로 제한됩니다. 최대 파일 수보다 많이 열려고 하면 설명자 또는 파일 스트림에서 프로그램 오류가 발생합니다. [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 를 사용하여 이 숫자를 변경합니다.

## <a name="file-handling-routines-file-descriptor"></a>파일 처리 루틴(파일 설명자)

다음 루틴은 파일 설명자에 지정된 파일에서 작동합니다.

|루틴에서 반환된 값|기능|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md),[_chsize_s](../c-runtime-library/reference/chsize-s.md)|파일 크기 변경|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|파일 길이 가져오기|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|설명자에서 파일 상태 정보 가져오기|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|기존 C 런타임 파일 설명자와 연결된 운영 체제 파일 핸들 반환|
|[_isatty](../c-runtime-library/reference/isatty.md)|문자 입출력 디바이스 확인|
|[_locking](../c-runtime-library/reference/locking.md)|파일의 잠금 영역|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|기존 운영 체제 파일 핸들에 C 런타임 파일 설명자 연결|
|[_setmode](../c-runtime-library/reference/setmode.md)|파일 변환 모드 설정|

## <a name="file-handling-routines-path-or-filename"></a>파일 처리 루틴(경로 또는 파일 이름)

다음 루틴은 경로 또는 파일 이름으로 지정된 파일에서 작동합니다.

|루틴에서 반환된 값|기능|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|파일 권한 설정 확인|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|파일 사용 권한 설정 변경|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|상대 경로를 절대 경로 이름으로 확장|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|경로 구성 요소를 단일 전체 경로에 병합|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|고유한 파일 이름 만들기|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|파일 삭제|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|파일 이름 바꾸기|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|구성 요소로 경로 구문 분석|
|[_stat, _stat64, _stati64, _wstat, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|명명된 파일에서 파일 상태 정보 가져오기|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|프로그램에서 만든 새 파일에 대해 기본 사용 권한 마스크 설정|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|파일 삭제|

## <a name="file-handling-routines-open-file"></a>파일 처리 루틴(파일 열기)

다음 루틴은 파일을 엽니다.

|루틴에서 반환된 값|기능|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|파일을 열고 열린 파일에 대한 포인터를 반환합니다.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|파일 공유로 스트림을 열고 열린 파일에 대한 포인터를 반환합니다.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|파일을 열고 열린 파일에 대한 파일 설명자를 반환합니다.|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|파일 공유로 파일을 열고 열린 파일에 대한 파일 설명자를 반환합니다.|
|[_pipe](../c-runtime-library/reference/pipe.md)|읽기 및 쓰기용 파이프를 만듭니다.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|파일 포인터를 다시 할당합니다.|

다음 루틴은 `FILE` 구조체, 파일 설명자 및 Win32 파일 핸들 사이에서 파일의 표현을 변경하는 방법을 제공합니다.

|루틴에서 반환된 값|기능|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|하위 수준 I/O를 위해 이전에 연 파일에 스트림을 연결하고 열린 스트림에 대한 포인터를 반환합니다.|
|[_fileno](../c-runtime-library/reference/fileno.md)|스트림에 연결된 파일 설명자를 가져옵니다.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|기존 C 런타임 파일 설명자와 연결된 운영 체제 파일 핸들 반환|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|C 런타임 파일 설명자를 기존 운영 체제 파일 핸들에 연결합니다.|

다음 Win32 함수도 파일 및 파이프를 엽니다.

- [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)

- [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)

- [CreateNamedPipe](/windows/win32/api/winbase/nf-winbase-createnamedpipea)

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
[디렉터리 제어](../c-runtime-library/directory-control.md)<br/>
[시스템 호출](../c-runtime-library/system-calls.md)<br/>
