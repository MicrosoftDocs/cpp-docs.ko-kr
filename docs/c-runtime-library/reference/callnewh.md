---
description: '다음에 대 한 자세한 정보: _callnewh'
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: f75028a47bbdbb6c12617a79b07a2fb8f4c5a6bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209609"
---
# <a name="_callnewh"></a>_callnewh

현재 설치된 *새 처리기* 를 호출합니다.

## <a name="syntax"></a>구문

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>매개 변수

*size*<br/>
[new 연산자](../../cpp/new-operator-cpp.md)에서 할당하려고 시도한 메모리의 양입니다.

## <a name="return-value"></a>Return Value

|값|설명|
|-----------|-----------------|
|0|실패: 설치된 새 처리기가 없거나 새 처리기가 비활성 상태입니다.|
|1|성공: 새 처리기가 설치되었으며 활성 상태입니다. 메모리 할당을 다시 시도할 수 있습니다.|

## <a name="exceptions"></a>예외

이 함수는 *새 처리기* 를 찾을 수 없는 경우 [bad_alloc](../../standard-library/bad-alloc-class.md)을 throw합니다.

## <a name="remarks"></a>설명

[new 연산자](../../cpp/new-operator-cpp.md)가 메모리 할당에 실패하는 경우 *새 처리기* 가 호출됩니다. 그러면 후속 할당에 성공할 수 있도록 새 처리기가 메모리를 해제하는 등의 몇 가지 적절한 작업을 시작할 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>참고 항목

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
