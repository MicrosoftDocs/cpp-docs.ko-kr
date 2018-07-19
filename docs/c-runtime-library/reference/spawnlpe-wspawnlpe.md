---
title: _spawnlpe, _wspawnlpe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _spawnlpe
- _wspawnlpe
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- spawnlpe
- _wspawnlpe
- _spawnlpe
- wspawnlpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be8e86ddb6405c39f877bd9065a931b66238c2b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413310"
---
# <a name="spawnlpe-wspawnlpe"></a>_spawnlpe, _wspawnlpe

새 프로세스를 만들고 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>매개 변수

*모드*<br/>
호출 프로세스의 실행 모드입니다.

*cmdname*<br/>
실행할 파일의 경로입니다.

*arg0*, *arg1*,... *argn*<br/>
인수에 대한 포인터 목록입니다. *arg0* 인수에 대 한 포인터는 일반적으로 *cmdname*합니다. 인수 *arg1* 통해 *argn* 은 새로운 인수 목록을 구성 하는 문자열을 가리키는 포인터입니다. 다음 *argn*, 있어야는 **NULL** 인수 목록의 끝을 표시 하는 포인터입니다.

*envp*<br/>
환경 설정에 대한 포인터 배열입니다.

## <a name="return-value"></a>반환 값

반환 값을 동기 **_spawnlpe** 또는 **_wspawnlpe** (**_P_WAIT** 에 대해 지정 된 *모드*) 새 종료 상태 프로세스입니다. 반환 값을 비동기 **_spawnlpe** 또는 **_wspawnlpe** (**_P_NOWAIT** 또는 **_P_NOWAITO** 에 대해 지정 된  *모드*)은 프로세스 핸들입니다. 프로세스가 정상적으로 종료되는 경우 종료 상태는 0입니다. 생성된 된 프로세스를 사용 하 여 0이 아닌 인수를 호출 하는 경우 종료 상태 0이 아닌 값으로 설정할 수 있습니다는 **종료** 루틴입니다. 새 프로세스가 양수 값의 종료 상태를 명시적으로 설정하지 않은 경우, 양수 값의 종료 상태는 중단 또는 인터럽트로 인한 비정상적인 종료를 나타냅니다. 반환 값이-1 (새 프로세스가 시작 되지 않습니다.) 오류를 나타냅니다. 이 경우 **errno** 다음 값 중 하나로 설정 됩니다.

|||
|-|-|
**E2BIG**|인수 목록이 1024바이트를 초과합니다.
**EINVAL**|*모드* 인수가 잘못 되었습니다.
**ENOENT**|파일 또는 경로를 찾을 수 없습니다.
**ENOEXEC**|지정한 파일이 실행할 수 없거나 실행 파일 형식이 잘못되었습니다.
**ENOMEM**|메모리가 부족하여 새 프로세스를 실행할 수 없습니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 새 프로세스를 만들어 실행하고, 각 명령줄 인수를 별도의 매개 변수로 전달하고, 포인터 배열을 환경 설정으로 전달합니다. 사용 하 여 이러한 함수는 **경로** 환경 변수를 실행할 파일을 찾습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. 어느 경우 *cmdname* 또는 *arg0* 은 빈 문자열 또는 null 포인터 이면 잘못 된 매개 변수 처리기가 호출 됩니다에 설명 된 대로 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된, 이러한 함수 설정 **errno** 를 **EINVAL**,-1을 반환 하 고 있습니다. 새로운 프로세스가 생성되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_spawnlpe**|\<process.h>|
|**_wspawnlpe**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고자료

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
