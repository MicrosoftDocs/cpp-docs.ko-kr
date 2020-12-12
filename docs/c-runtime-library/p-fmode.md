---
description: '다음에 대 한 자세한 정보: __p__fmode'
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: da7cae9c881ebe042aa5d6003b50c09c65ea02d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213522"
---
# <a name="__p__fmode"></a>__p__fmode

파일 I/O 연산에 대한 기본 *파일 변환 모드* 를 지정하는 `_fmode` 전역 변수에 대한 포인터입니다.

## <a name="syntax"></a>구문

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Return Value

`_fmode` 전역 변수에 대한 포인터입니다.

## <a name="remarks"></a>설명

`__p__fmode` 함수는 내부용이며 사용자 코드에서 호출할 수 없습니다.

파일 변환 모드는 [_open](../c-runtime-library/reference/open-wopen.md) 및 [_pipe](../c-runtime-library/reference/pipe.md) I/O 연산에 대한 `binary` 또는 `text` 변환을 지정합니다. 자세한 내용은 [_fmode](../c-runtime-library/fmode.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
