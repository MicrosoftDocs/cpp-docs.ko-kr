---
description: '자세한 정보: set_terminate (CRT)'
title: set_terminate(CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 6b25e141bc9299389c80e629ff6eb03d7deba23c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211104"
---
# <a name="set_terminate-crt"></a>set_terminate(CRT)

**종료** 에 의해 호출 되는 자체 종료 루틴을 설치 합니다.

## <a name="syntax"></a>구문

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>매개 변수

*termFunction*<br/>
작성하는 terminate 함수에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이전 함수를 나중에 복원할 수 있도록 **set_terminate** 로 등록 된 이전 함수에 대 한 포인터를 반환 합니다. 이전 함수를 설정 하지 않은 경우 반환 값을 사용 하 여 기본 동작을 복원할 수 있습니다. 이 값은 **NULL** 일 수 있습니다.

## <a name="remarks"></a>설명

**Set_terminate** 함수는 *termFunction* 를 **terminate** 에 의해 호출 된 함수로 설치 합니다. **set_terminate** 은 c + + 예외 처리와 함께 사용 되며, 예외가 throw 되기 전에 프로그램의 특정 지점에서 호출 될 수 있습니다. **종료** 호출은 기본적으로 [중단](abort.md) 됩니다. 사용자 고유의 종료 함수를 작성 하 고 함수 이름을 인수로 사용 하 여 **set_terminate** 를 호출 하 여이 기본값을 변경할 수 있습니다. **terminate** 는 **set_terminate** 에 대 한 인수로 지정 된 마지막 함수를 호출 합니다. 원하는 정리 작업을 수행한 후 *termFunction* 는 프로그램을 종료 해야 합니다. 종료 되지 않은 경우 (호출자에 게 반환 되는 경우) [abort](abort.md) 가 호출 됩니다.

다중 스레드 환경에서 terminate 함수는 각 스레드에 대해 개별적으로 유지 관리됩니다. 각 새 스레드는 자체 terminate 함수를 설치해야 합니다. 따라서 각 스레드는 자체 종료 처리를 담당합니다.

**Terminate_function** 형식은 EH로 정의 됩니다. H는을 반환 하는 *termFunction* 사용자 정의 종료 함수에 대 한 포인터입니다 **`void`** . 사용자 지정 함수 *termFunction* 는 인수를 사용할 수 없으며 해당 호출자로 반환 되어서는 안 됩니다. 이 경우 [abort](abort.md) 가 호출 됩니다. *TermFunction* 내에서 예외를 throw 할 수 없습니다.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate** 함수는 디버거 외부 에서만 작동 합니다.

동적으로 연결 된 모든 Dll 또는 Exe에 대해 단일 **set_terminate** 처리기가 있습니다. **set_terminate** 호출 하는 경우에도 처리기가 다른로 대체 되거나 다른 DLL 또는 EXE에 의해 설정 된 처리기를 대체할 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[terminate](terminate-crt.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[중단이](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[끝나야](terminate-crt.md)<br/>
[없는](unexpected-crt.md)<br/>
