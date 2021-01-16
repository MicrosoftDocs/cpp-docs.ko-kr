---
description: '다음에 대 한 자세한 정보: _get_unexpected'
title: _get_unexpected
ms.date: 1/14/2021
api_name:
- _get_unexpected
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
- __get_unexpected
- _get_unexpected
- get_unexpected
helpviewer_keywords:
- __get_unexpected function
- get_unexpected function
- _get_unexpected function
ms.assetid: a5f7a7a0-18e0-485e-953d-db291068a1e8
ms.openlocfilehash: fb23aa9eee66a4ed981e5575e5a36ad4bbb39f84
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242620"
---
# `_get_unexpected`

에서 호출할 종료 루틴을 반환 합니다 **`unexpected`** .

## <a name="syntax"></a>구문

```C
unexpected_function _get_unexpected( void );
```

## <a name="return-value"></a>Return Value

에 의해 등록 된 함수에 대 한 포인터를 반환 [`set_unexpected`](set-unexpected-crt.md) 합니다. 함수가 설정 되지 않은 경우 반환 값을 사용 하 여 기본 동작을 복원할 수 있습니다. 이 값은 일 수 있습니다 **`NULL`** .

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`_get_unexpected`**|\<eh.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[`abort`](abort.md)<br/>
[`set_terminate`](set-terminate-crt.md)<br/>
[`terminate`](terminate-crt.md)<br/>
[`unexpected`](unexpected-crt.md)<br/>
