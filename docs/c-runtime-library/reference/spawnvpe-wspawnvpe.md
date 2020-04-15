---
title: _spawnvpe, _wspawnvpe
ms.date: 4/2/2020
api_name:
- _spawnvpe
- _wspawnvpe
- _o__spawnvpe
- _o__wspawnvpe
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawnvpe
- wspawnvpe
- _wspawnvpe
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
ms.openlocfilehash: c8a97e99711a2053a26ae850c09c82a4342cda3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355709"
---
# <a name="_spawnvpe-_wspawnvpe"></a>_spawnvpe, _wspawnvpe

새 프로세스를 만들고 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>매개 변수

*모드*<br/>
호출 프로세스의 실행 모드입니다.

*Cmdname*<br/>
실행할 파일의 경로입니다.

*Argv*<br/>
인수에 대한 포인터 배열입니다. 인수 *argv*[0]은 일반적으로 실제 모드또는 보호 모드의 프로그램 이름에 대한 포인터이며 *argv*[n]을 통해 *argv***[1]은**새 인수 목록을 형성하는 문자 문자열에 대한 포인터입니다. 인수 *argv***[n** +1]은 인수 목록의 끝을 표시하는 **NULL** 포인터여야 합니다.

*Envp*<br/>
환경 설정에 대한 포인터 배열입니다.

## <a name="return-value"></a>Return Value

동기 **_spawnvpe** 또는 *_wspawnvpe(모드에* **_wspawnvpe** _P_WAIT **_P_WAIT** 지정됨)의 반환 값은 새 프로세스의 종료 상태입니다. 비동기 **_spawnvpe** 또는 **_wspawnvpe(_P_NOWAIT** **_wspawnvpe** **또는** _P_NOWAITO *모드로*지정)의 반환 값은 프로세스 핸들입니다. 프로세스가 정상적으로 종료되는 경우 종료 상태는 0입니다. 생성된 프로세스가 특히 0이 아닌 인수로 **종료** 루틴을 호출하는 경우 종료 상태를 비영값으로 설정할 수 있습니다. 새 프로세스가 양수 값의 종료 상태를 명시적으로 설정하지 않은 경우, 양수 값의 종료 상태는 중단되거나 인터럽트된 비정상적인 종료를 나타냅니다. 반환 값 -1은 오류를 나타냅니다(새 프로세스가 시작되지 않음). 이 경우 **errno는** 다음 값 중 하나로 설정됩니다.

|||
|-|-|
| **E2BIG** | 인수 목록이 1024바이트를 초과합니다. |
| **아인발 ()에인발 (것)** | *모드* 인수가 잘못되었습니다. |
| **이노엔트 (이노엔트 주)** | 파일 또는 경로를 찾을 수 없습니다. |
| **ENOEXEC** | 지정한 파일이 실행할 수 없거나 실행 파일 형식이 잘못되었습니다. |
| **이노임 (주)** | 메모리가 부족하여 새 프로세스를 실행할 수 없습니다. |

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 새 프로세스를 작성 및 실행하고, 명령줄 인수에 대한 포인터 배열 및 환경 설정에 대한 포인터 배열을 전달합니다. 이러한 함수는 **PATH** 환경 변수를 사용하여 실행할 파일을 찾습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *cmdname* 또는 *argv가* null 포인터이거나 *argv가* null 포인터를 가리키거나 *argv*[0]이 빈 문자열인 경우 [매개 변수 유효성 검사에](../../c-runtime-library/parameter-validation.md) 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속할 수 있는 경우 이러한 함수는 **errno를** **EINVAL로**설정하고 -1을 반환합니다. 새로운 프로세스가 생성되지 않습니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> 또는 \<process.h>|
|**_wspawnvpe**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[중단](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec 기능](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
