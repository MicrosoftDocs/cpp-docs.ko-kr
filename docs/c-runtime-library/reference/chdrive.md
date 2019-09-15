---
title: _chdrive
ms.date: 11/04/2016
api_name:
- _chdrive
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 3ee292c03c9d31944e0a555c2159d7a5dd2cd0eb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939238"
---
# <a name="_chdrive"></a>_chdrive

현재 작업 드라이브를 변경합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>매개 변수

*drive*<br/>
현재 작업 드라이브를 지정하는 1부터 26까지의 정수입니다(1 = A, 2 = B 등).

## <a name="return-value"></a>반환 값

현재 작업 드라이브가 변경된 경우 0이고, 변경되지 않으면 -1입니다.

## <a name="remarks"></a>설명

*드라이브가* 1에서 26 사이에 있지 않은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용 된 경우 **_chdrive** 함수는-1을 반환 하 고, **errno** 을 **eacces**로 설정 하 고, **_doserrno** 는 **ERROR_INVALID_DRIVE**로 설정 합니다.

**_chdrive** 함수는 그 자체가 스레드로부터 안전하지 않은 **SetCurrentDirectory** 함수에 종속되므로 스레드로부터 안전하지 않습니다. 다중 스레드 애플리케이션에서 **_chdrive**를 안전하게 사용하려면 고유한 스레드 동기화를 제공해야 합니다. 자세한 내용은 [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)를 참조 하세요.

**_chdrive** 함수는 현재 작업 드라이브만 변경합니다. **_chdir** 함수는 현재 작업 디렉터리를 변경합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_getdrive](getdrive.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고자료

[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
