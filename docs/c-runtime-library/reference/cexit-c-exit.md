---
description: '자세히 알아보기: _cexit, _c_exit'
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: e901e7d7e37c8702efaae8b3b70e98a400f48ef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275102"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

정리 작업을 수행하고 프로세스 종료 없이 반환합니다.

## <a name="syntax"></a>구문

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>설명

**_Cexit** 함수는 **atexit** 및 **_onexit** 에 의해 등록 된 함수를 LIFO (last in) 순서로 호출 합니다. 그런 다음를 반환 하기 전에 모든 i/o 버퍼를 플러시하고 열려 있는 모든 스트림을 닫습니다 **_cexit** 합니다. **_c_exit** 은 **_exit** 와 동일 하지만 **atexit** 를 처리 하거나 **_onexit** 하거나 스트림 버퍼를 플러시하는 대신 호출 프로세스로 돌아갑니다. **Exit**, **_exit**, **_cexit** 및 **_c_exit** 의 동작은 다음 표에 나와 있습니다.

|함수|동작|
|--------------|--------------|
|**exit**|전체 C 라이브러리 종료 절차를 수행하고, 프로세스를 종료하고, 제공된 상태 코드와 함께 종료됩니다.|
|**_exit**|빠른 C 라이브러리 종료 절차를 수행하고, 프로세스를 종료하고, 제공된 상태 코드와 함께 종료됩니다.|
|**_cexit**|전체 C 라이브러리 종료 절차를 수행하고 호출자에게 반환하지만, 프로세스를 종료하지 않습니다.|
|**_c_exit**|빠른 C 라이브러리 종료 절차를 수행하고 호출자에게 반환하지만, 프로세스를 종료하지 않습니다.|

**_Cexit** 또는 **_c_exit** 함수를 호출 하는 경우 호출 시 존재 하는 임시 또는 자동 개체에 대 한 소멸자가 호출 되지 않습니다. 자동 개체는 개체가 정적으로 선언되지 않은 함수에서 정의된 개체입니다. 임시 개체는 컴파일러에 의해 생성된 개체입니다. **_Cexit** 또는 **_c_exit** 를 호출 하기 전에 자동 개체를 삭제 하려면 다음과 같이 개체에 대 한 소멸자를 명시적으로 호출 합니다.

```cpp
myObject.myClass::~myClass( );
```

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

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
