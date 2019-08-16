---
title: _getdcwd, _wgetdcwd
ms.date: 11/04/2016
apiname:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 9f6ae99ae74bb21c9462abcb37e466d63b86f8af
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501025"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

지정한 드라이브의 현재 작업 디렉터리의 전체 경로를 가져옵니다.

## <a name="syntax"></a>구문

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>매개 변수

*drive*<br/>
드라이브를 지정하는 음수가 아닌 정수입니다(0 = 기본 드라이브, 1 = A, 2 = B 등).

지정 된 드라이브를 사용할 수 없거나 드라이브 유형 (예: 이동식, 고정, CD-ROM, RAM 디스크 또는 네트워크 드라이브)을 확인할 수 없는 경우 잘못 된 매개 변수 처리기가 호출 됩니다. 자세한 내용은 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)를 참조하세요.

*buffer*<br/>
경로에 대한 스토리지 위치 또는 **NULL**입니다.

**NULL** 이 지정 된 경우이 함수는 **malloc**를 사용 하 여 최소 *maxlen* 크기의 버퍼를 할당 하 고, **_getdcwd** 의 반환 값은 할당 된 버퍼에 대 한 포인터입니다. **Free** 를 호출 하 고 포인터를 전달 하 여 버퍼를 해제할 수 있습니다.

*maxlen*<br/>
경로의 최대 길이를 지정 하는 0이 아닌 양의 정수 (문자: **_getdcwd** 의 경우 **char** , **_wgetdcwd**의 경우 **wchar_t** )입니다.

*Maxlen* 가 0 보다 작거나 같으면 잘못 된 매개 변수 처리기가 호출 됩니다. 자세한 내용은 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)를 참조하세요.

## <a name="return-value"></a>반환 값

지정 된 드라이브에 있는 현재 작업 디렉터리의 전체 경로를 나타내는 문자열에 대 한 포인터 또는 오류를 나타내는 **NULL**입니다.

*Buffer* 가 **NULL** 로 지정 되 고 *maxlen* 문자를 할당할 메모리가 부족 한 경우 오류가 발생 하 고 **errno** 가 **enomem**으로 설정 됩니다. 종료 null 문자를 포함 하는 경로 길이가 *maxlen*을 초과 하면 오류가 발생 하 고 **errno** 가 **ERANGE**로 설정 됩니다. 이러한 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Getdcwd** 함수는 지정 된 드라이브에 있는 현재 작업 디렉터리의 전체 경로를 가져와 *버퍼*에 저장 합니다. 현재 작업 디렉터리가 루트로 설정되는 경우 문자열이 백슬래시(\\)로 끝납니다. 현재 작업 디렉터리가 루트 이외의 디렉터리로 설정되는 경우 문자열은 백슬래시가 아닌 디렉터리의 이름으로 끝납니다.

**_wgetdcwd** 는 **_getdcwd**의 와이드 문자 버전 이며, 해당 *버퍼* 매개 변수와 반환 값은 와이드 문자열입니다. 그렇지 않으면 **_wgetdcwd** 및 **_getdcwd** 가 동일 하 게 동작 합니다.

이 함수는 자체적으로 스레드로부터 안전하지 않는 **GetFullPathName**에 의존하지만 스레드로부터 안전합니다. 그러나 다중 스레드 애플리케이션에서 이 함수와 [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)을 모두 호출하는 경우 스레드 안전성을 위반할 수 있습니다.

_Nolock 접미사가 있는이 함수의 버전 은 스레드로부터 안전 하지 않으며 다른 스레드의 간섭 으로부터 보호 되지 않는다는 점을 제외 하 고이 함수와 동일 하 게 작동 합니다. 자세한 내용은 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)을 참조하세요.

**_Debug** 및 **_CRTDBG_MAP_ALLOC** 가 정의 된 경우 **_getdcwd** 및 **_wgetdcwd** 호출은 **_getdcwd_dbg** 및 **_wgetdcwd_dbg** 에 대 한 호출로 대체 되므로 메모리 할당을 디버그할 수 있습니다. 자세한 내용은[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_getdrive](getdrive.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고자료

[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
