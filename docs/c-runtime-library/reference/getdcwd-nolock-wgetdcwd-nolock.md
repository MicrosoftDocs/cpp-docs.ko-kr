---
description: '자세히 알아보기: _getdcwd_nolock, _wgetdcwd_nolock'
title: _getdcwd_nolock, _wgetdcwd_nolock
ms.date: 11/04/2016
api_name:
- _wgetdcwd_nolock
- _getdcwd_nolock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wgetdcwd_nolock
- tgetdcwd_nolock
- wgetdcwd_nolock
- _getdcwd_nolock
- _tgetdcwd_nolock
- getdcwd_nolock
helpviewer_keywords:
- getdcwd_nolock function
- _tgetdcwd_nolock function
- working directory
- tgetdcwd_nolock function
- _getdcwd_nolock function
- current working directory
- wgetdcwd_nolock function
- _wgetdcwd_nolock function
- directories [C++], current working
ms.assetid: d9bdf712-43f8-4173-8f9a-844e82beaa97
ms.openlocfilehash: d40bd7a3cf8d666ad7ba108fc71e443ea262c13f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256564"
---
# <a name="_getdcwd_nolock-_wgetdcwd_nolock"></a>_getdcwd_nolock, _wgetdcwd_nolock

지정한 드라이브의 현재 작업 디렉터리의 전체 경로를 가져옵니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *_getdcwd_nolock(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd_nolock(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>매개 변수

*드라이브나*<br/>
디스크 드라이브입니다.

*버퍼*<br/>
경로의 스토리지 위치입니다.

*maxlen*<br/>
경로의 최대 길이 (문자): **`char`** **_getdcwd** 및 **`wchar_t`** **_wgetdcwd** 의 최대 길이입니다.

## <a name="return-value"></a>반환 값

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)를 참조하세요.

## <a name="remarks"></a>설명

**_getdcwd_nolock** 및 **_wgetdcwd_nolock** 는 다른 스레드의 간섭 으로부터 보호 되지 않는다는 점을 제외 하 고 각각 **_getdcwd** 및 **_wgetdcwd** 와 동일 합니다. 이들은 다른 스레드를 잠그는 오버헤드를 유발하지 않으므로 속도가 더 빠를 수 있습니다. 단일 스레드 애플리케이션과 같은 스레드로부터 안전한 컨텍스트 또는 이미 스레드 격리를 처리한 호출 범위에서만 이러한 함수를 사용합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_nolock**|**_getdcwd_nolock**|**_getdcwd_nolock**|**_wgetdcwd_nolock**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getdcwd_nolock**|\<direct.h>|
|**_wgetdcwd_nolock**|\<direct.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
