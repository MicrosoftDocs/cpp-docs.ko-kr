---
description: '자세한 정보: 시스템, _wsystem'
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 3fb2045b932347669a756be1c8bc2f87694bd50d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326241"
---
# <a name="system-_wsystem"></a>system, _wsystem

명령을 실행합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>매개 변수

*command*<br/>
실행할 명령입니다.

## <a name="return-value"></a>반환 값

*Command* 가 **NULL** 이 고 명령 인터프리터가 발견 되 면 0이 아닌 값을 반환 합니다. 명령 인터프리터를 찾을 수 없는 경우는 0을 반환 하 고 **errno** 를 **enoent (** 로 설정 합니다. *Command* 가 **NULL** 이 아니면 **system** 은 명령 인터프리터에서 반환 된 값을 반환 합니다. 명령 인터프리터가 값 0을 반환할 때만 값 0을 반환합니다. 반환 값-1은 오류를 나타내고 **errno** 은 다음 값 중 하나로 설정 됩니다.

| 값 | 설명 |
|-|-|
| **E2BIG** | 인수 목록(시스템에 따라 다름)이 너무 큽니다. |
| **ENOENT (** | 명령 인터프리터를 찾을 수 없습니다. |
| **ENOEXEC** | 명령 인터프리터 파일 형식이 올바르지 않아서 실행할 수 없습니다. |
| **ENOMEM** | 메모리가 부족하여 명령을 실행할 수 없습니다. 사용 가능한 메모리가 손상되었거나 잘못된 블록이 있습니다. 이는 호출 프로세스가 제대로 할당되지 않았음을 나타냅니다. |

이러한 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**시스템** 함수 *는 명령을 명령 인터프리터에 전달 하며* ,이 명령은 문자열을 운영 체제 명령으로 실행 합니다. **시스템** 은 **COMSPEC** 및 **PATH** 환경 변수를 사용 하 여 CMD.exe 명령 인터프리터 파일을 찾습니다. *Command* 가 **NULL** 인 경우 함수는 명령 인터프리터가 있는지만 확인 합니다.

[Fflush](fflush.md) 또는 [_flushall](flushall.md)를 사용 하 여 명시적으로 플러시 하거나 **시스템** 을 호출 하기 전에 모든 스트림을 닫아야 합니다.

**_wsystem** 는 **시스템** 의 와이드 문자 버전입니다. **_wsystem** 에 대 한 *명령* 인수는 와이드 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**시스템**|**시스템**|**_wsystem**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**시스템**|\<process.h> 또는 \<stdlib.h>|
|**_wsystem**|\<process.h> 또는 \<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 예제에서는 **시스템** 을 사용 하 여 텍스트 파일을 입력 합니다.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>입력: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>출력

```Output
Line one.
Line two.
```

## <a name="see-also"></a>참조

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
