---
description: '다음에 대 한 자세한 정보: _query_new_mode'
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 90c7355f4babc4726c8b52d61309eb1ceb23c9a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137139"
---
# <a name="_query_new_mode"></a>_query_new_mode

**Malloc** 에 대 한 **_set_new_mode** 에 의해 설정 된 새 처리기 모드를 나타내는 정수를 반환 합니다.

## <a name="syntax"></a>구문

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Return Value

**Malloc** 에 대 한 현재 새 처리기 모드 (0 또는 1)를 반환 합니다. 반환 값이 1 이면 메모리를 할당 하지 못할 때 **malloc** 이 새 처리기 루틴을 호출 함을 나타냅니다. 반환 값이 0 이면 그렇지 않음을 나타냅니다.

## <a name="remarks"></a>설명

C + + **_query_new_mode** 함수는 [malloc](malloc.md)에 대 한 c + + [_set_new_mode](set-new-mode.md) 함수에 의해 설정 되는 새 처리기 모드를 나타내는 정수를 반환 합니다. 새 처리기 모드는 메모리를 할당 하지 못할 때 **malloc** 이 [_set_new_handler](set-new-handler.md)에 의해 설정 된 대로 새 처리기 루틴을 호출 하는지 여부를 나타냅니다. 기본적으로 **malloc** 은 오류 발생 시 새 처리기 루틴을 호출 하지 않습니다. **_Set_new_mode** 를 사용 하 여이 동작을 재정의할 수 있습니다. 그러면 실패 한 경우 연산자가 메모리 할당에 실패 했을 때와 동일한 방식으로 새 처리기 루틴 **을 호출 합니다** **`new`** . 자세한 내용은 C++ 언어 참조의 [new 및 delete 연산자](../../cpp/new-and-delete-operators.md)에 대한 설명을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
