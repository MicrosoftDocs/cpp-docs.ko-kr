---
description: '다음에 대 한 자세한 정보: quick_exit'
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 85640af902092d5cc60a1c718dfd8999c41406b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137100"
---
# <a name="quick_exit"></a>quick_exit

프로그램이 정상 종료되게 합니다.

## <a name="syntax"></a>구문

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>매개 변수

*status*<br/>
호스트 환경에 반환될 상태 코드입니다.

## <a name="return-value"></a>반환 값

**Quick_exit** 함수는 호출자에 게 반환할 수 없습니다.

## <a name="remarks"></a>설명

**Quick_exit** 함수는 정상적인 프로그램 종료를 발생 시킵니다. **신호** 함수에서 등록 한 **atexit**, **_onexit** 또는 신호 처리기에 의해 등록 된 함수를 호출 하지 않습니다. **Quick_exit** 를 두 번 이상 호출 하거나 **종료** 함수를 호출 하는 경우 동작이 정의 되지 않습니다.

**Quick_exit** 함수는 함수가 등록 될 때 이미 호출 된 함수를 제외 하 고 **at_quick_exit** 에 의해 등록 된 함수를 LIFO (last in, 선입 out) 순서로 호출 합니다.  함수 호출을 종료하는 등록된 함수를 호출하는 동안 [longjmp](longjmp.md) 가 호출되면 동작이 정의되지 않습니다.

등록 된 함수가 호출 된 후 **quick_exit** 는 *상태* 값을 사용 하 여 호스트 환경으로 제어를 반환 하 여 **_Exit** 를 호출 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**quick_exit**|\<process.h> 또는 \<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[중단이](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
