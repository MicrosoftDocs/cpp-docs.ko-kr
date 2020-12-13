---
description: '다음에 대 한 자세한 정보: _get_unexpected'
title: _get_unexpected
ms.date: 11/04/2016
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
ms.openlocfilehash: 9c8f21815aa465e1325ef0519ba21abb1e506db3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338941"
---
# <a name="_get_unexpected"></a>_get_unexpected

**예기치 않게** 호출할 종료 루틴을 반환 합니다.

## <a name="syntax"></a>구문

```C
unexpected_function _get_unexpected( void );
```

## <a name="return-value"></a>Return Value

[set_unexpected](set-unexpected-crt.md)로 등록된 함수에 대한 포인터를 반환합니다. 함수가 설정 되지 않은 경우 반환 값을 사용 하 여 기본 동작을 복원할 수 있습니다. 이 값은 **NULL** 일 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_unexpected**|\<eh.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[중단이](abort.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[끝나야](terminate-crt.md)<br/>
[없는](unexpected-crt.md)<br/>
