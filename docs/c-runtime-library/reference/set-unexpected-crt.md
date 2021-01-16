---
description: '자세한 정보: set_unexpected (CRT)'
title: set_unexpected(CRT)
ms.date: 1/14/2021
api_name:
- set_unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: b9918e152a5d27c853aef7769b932ee4efedeef8
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242633"
---
# <a name="set_unexpected-crt"></a>`set_unexpected` CRT

에서 호출 하는 자체 종료 함수를 설치 **`unexpected`** 합니다.

## <a name="syntax"></a>구문

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>매개 변수

*`unexpFunction`*\
함수를 바꾸기 위해 작성 하는 함수에 대 한 포인터 **`unexpected`** 입니다.

## <a name="return-value"></a>반환 값

**`_set_unexpected`** 이전 함수를 나중에 복원할 수 있도록에서 등록 한 이전 종료 함수에 대 한 포인터를 반환 합니다. 이전 함수를 설정 하지 않은 경우 반환 값을 사용 하 여 기본 동작을 복원할 수 있습니다. 이 값은 일 수 있습니다 **`NULL`** .

## <a name="remarks"></a>설명

**`set_unexpected`** 함수는에서 호출 하는 함수로 *unexpfunction* 을 설치 **`unexpected`** 합니다. **`unexpected`** 는 현재 c + + 예외 처리 구현에서 사용 되지 않습니다. **`unexpected_function`** 형식은 EH로 정의 됩니다. H는 사용자 정의 예기치 않은 함수에 대 한 포인터로 서 반환 하는 *함수* 를 반환 **`void`** 합니다. 사용자 지정 *함수* 함수는 해당 호출자에 게 반환 되어서는 안 됩니다.

```cpp
typedef void ( *unexpected_function )( );
```

기본적으로는를 **`unexpected`** 호출 **`terminate`** 합니다. 사용자 고유의 종료 함수를 작성 하 고 **`set_unexpected`** 함수 이름을 인수로 사용 하 여를 호출 하 여이 기본 동작을 변경할 수 있습니다. **`unexpected`** 에 대 한 인수로 지정 된 마지막 함수를 호출 **`set_unexpected`** 합니다.

에 대 한 호출로 설치 된 사용자 지정 종료 함수와 달리에서 **`set_terminate`** 예외가 throw 될 수 있습니다 **`unexpFunction`** .

다중 스레드 환경에서 unexpected 함수는 각 스레드에 대해 개별적으로 유지 관리됩니다. 각 새 스레드는 자체 unexpected 함수를 설치해야 합니다. 따라서 각 스레드는 자체 unexpected 처리를 담당합니다.

현재 c + + 예외 처리의 Microsoft 구현에서 **`unexpected`** 는 **`terminate`** 기본적으로를 호출 하 고 예외 처리 런타임 라이브러리에 의해 호출 되지 않습니다. Term'inate가 아닌를 호출 하는 경우에는 특별 한 이점이 없습니다 **`unexpected`** . 

**`set_unexpected`** 동적으로 연결 된 모든 dll 또는 exe에 대 한 단일 처리기가 있습니다 .를 호출 하는 경우에도 **`set_unexpected`** 처리기를 다른 것으로 바꾸거나 다른 DLL 또는 EXE로 설정한 처리기를 바꿀 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`set_unexpected`**|`<eh.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)\
[`abort`](abort.md)\
[`_get_unexpected`](get-unexpected.md)\
[`set_terminate`](set-terminate-crt.md)\
[`terminate`](terminate-crt.md)\
[`unexpected`](unexpected-crt.md)\
