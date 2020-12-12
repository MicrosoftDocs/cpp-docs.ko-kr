---
description: '자세히 알아보기: _execlpe, _wexeclpe'
title: _execlpe, _wexeclpe
ms.date: 11/04/2016
api_name:
- _execlpe
- _wexeclpe
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wexeclpe
- wexeclpe
- _execlpe
helpviewer_keywords:
- wexeclpe function
- _wexeclpe function
- _execlpe function
- execlpe function
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
ms.openlocfilehash: 22f484166b2b70b0d54cefa4f12da36f9af098fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304754"
---
# <a name="_execlpe-_wexeclpe"></a>_execlpe, _wexeclpe

새 자식 프로세스를 로드하고 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
intptr_t _execlpe(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wexeclpe(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>매개 변수

*cmdname*<br/>
실행할 파일의 경로입니다.

*arg0*, ... *argn*<br/>
매개 변수에 대한 포인터 목록입니다.

*envp*<br/>
환경 설정에 대한 포인터 배열입니다.

## <a name="return-value"></a>반환 값

성공하면 이러한 함수는 호출 프로세스에 값을 반환하지 않습니다. 반환 값-1은 오류를 나타내며,이 경우 **errno** 전역 변수가 설정 됩니다.

|**errno** 값|설명|
|-------------------|-----------------|
|**E2BIG**|인수 및 환경 설정에 필요한 공간의 크기가 32KB를 초과합니다.|
|**EACCES**|지정한 파일이 잠금 또는 공유 위반이 되었습니다.|
|**EINVAL**|잘못된 매개 변수입니다.|
|**EMFILE**|실행 파일인지 여부를 확인하려면 지정한 파일이 열려 있어야 하지만, 열려 있는 파일이 너무 많습니다.|
|**ENOENT (**|파일 또는 경로를 찾을 수 없습니다.|
|**ENOEXEC**|지정한 파일이 실행할 수 없거나 실행 파일 형식이 잘못되었습니다.|
|**ENOMEM**|메모리가 부족하여 새 프로세스를 실행할 수 없습니다. 사용 가능한 메모리가 손상되었거나 잘못된 블록이 있습니다. 이는 호출 프로세스가 제대로 할당되지 않았음을 나타냅니다.|

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 각각의 명령줄 인수를 별도의 매개 변수로 전달하고 포인터 배열을 환경 설정에 전달하는 새 프로세스를 로드하고 실행합니다. 이러한 함수는 **PATH** 환경 변수를 사용 하 여 실행할 파일을 찾습니다.

**_Execlpe** 함수는 해당 매개 변수의 유효성을 검사 합니다. *Cmdname* 또는 *arg0* 가 null 포인터 이거나 빈 문자열인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다. 새 프로세스가 시작되지 않습니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|---------------------|
|**_execlpe**|\<process.h>|\<errno.h>|
|**_wexeclpe**|\<process.h> 또는 \<wchar.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[중단이](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
