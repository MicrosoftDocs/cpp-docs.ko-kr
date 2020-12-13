---
description: '다음에 대 한 자세한 정보: _query_new_handler'
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 8479ad1ffc6ec03d3cff82df645255fc69b16257
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137152"
---
# <a name="_query_new_handler"></a>_query_new_handler

현재 새 처리기 루틴의 주소를 반환합니다.

## <a name="syntax"></a>구문

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Return Value

**_Set_new_handler** 에서 설정한 대로 현재 새 처리기 루틴의 주소를 반환 합니다.

## <a name="remarks"></a>설명

C + + **_query_new_handler** 함수는 c + + [_set_new_handler](set-new-handler.md) 함수로 설정 된 현재 예외 처리 함수의 주소를 반환 합니다. **_set_new_handler** 는 **`new`** 연산자가 메모리 할당에 실패 하는 경우 제어를 얻기 위한 예외 처리 함수를 지정 하는 데 사용 됩니다. 자세한 내용은 C++ 언어 참조의 [new 및 delete 연산자](../../cpp/new-and-delete-operators.md)에 대한 설명을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
