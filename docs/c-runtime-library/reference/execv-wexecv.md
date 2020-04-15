---
title: _execv, _wexecv
ms.date: 4/2/2020
api_name:
- _wexecv
- _execv
- _o__execv
- _o__wexecv
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
- _execv
- _wexecv
- wexecv
helpviewer_keywords:
- _wexecv function
- _execv function
- wexecv function
- execv function
ms.assetid: 8dbaf7bc-9040-4316-a0c1-db7e866b52af
ms.openlocfilehash: 638364afa75fa1b04b598370473dee48964c5763
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347898"
---
# <a name="_execv-_wexecv"></a>_execv, _wexecv

새 자식 프로세스를 로드하고 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
intptr_t _execv(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecv(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>매개 변수

*Cmdname*<br/>
실행할 파일의 경로입니다.

*Argv*<br/>
매개 변수에 대한 포인터 배열입니다.

## <a name="return-value"></a>Return Value

성공하면 이러한 함수는 호출 프로세스에 값을 반환하지 않습니다. 반환 값 -1은 오류를 나타내며, 이 경우 **errno** 전역 변수가 설정됩니다.

|**에르노** 값|Description|
|-------------------|-----------------|
|**E2BIG**|인수 및 환경 설정에 필요한 공간의 크기가 32KB를 초과합니다.|
|**EACCES**|지정한 파일이 잠금 또는 공유 위반이 되었습니다.|
|**아인발 ()에인발 (것)**|잘못된 매개 변수입니다.|
|**EMFILE**|실행 파일인지 여부를 확인하려면 지정한 파일이 열려 있어야 하지만, 열려 있는 파일이 너무 많습니다.|
|**이노엔트 (이노엔트 주)**|파일 또는 경로를 찾을 수 없습니다.|
|**ENOEXEC**|지정한 파일이 실행할 수 없거나 실행 파일 형식이 잘못되었습니다.|
|**이노임 (주)**|메모리가 부족하여 새 프로세스를 실행할 수 없습니다. 사용 가능한 메모리가 손상되었거나 잘못된 블록이 있습니다. 이는 호출 프로세스가 제대로 할당되지 않았음을 나타냅니다.|

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 새 프로세스를 로드하고 실행하여 포인터 배열을 명령줄 인수에 전달합니다.

**_execv** 함수는 매개 변수의 유효성을 검사합니다. *cmdname이* null 포인터이거나 *argv가* null 포인터인 경우 빈 배열에 대한 포인터 또는 배열에 빈 문자열이 첫 번째 인수로 포함된 경우 **_execv** 함수는 [Parameter Validation에](../../c-runtime-library/parameter-validation.md)설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 실행을 계속할 수 있는 경우 이러한 함수는 **errno를** **EINVAL로** 설정하고 -1을 반환합니다. 프로세스가 시작되지 않습니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|---------------------|
|**_execv**|\<process.h>|\<errno.h>|
|**_wexecv**|\<process.h> 또는 \<wchar.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec 기능](../../c-runtime-library/exec-wexec-functions.md)<br/>
[중단](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn 기능](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
