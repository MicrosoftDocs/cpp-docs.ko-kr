---
description: '자세히 알아보기: ___setlc_active_func, ___unguarded_readlc_active_add_func'
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
api_name:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 85273b52102e9cca2e42ba4401da60b1d292560c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277090"
---
# <a name="___setlc_active_func-___unguarded_readlc_active_add_func"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

사용되지 않습니다. CRT는 이진 호환성을 유지하기 위해서만 내부 함수를 내보냅니다.

## <a name="syntax"></a>구문

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Return Value

반환되는 값은 중요하지 않습니다.

## <a name="remarks"></a>설명

내부 CRT 함수인 `___setlc_active_func` 및 `___unguarded_readlc_active_add_func`가 더 이상 사용되지 않더라도 이진 호환성을 유지하기 위해 CRT에서는 이러한 함수를 내보냅니다. `___setlc_active_func`의 원래 용도는 현재 활성 호출 수를 `setlocale` 함수로 반환하는 것입니다. `___unguarded_readlc_active_add_func`의 원래 용도는 로캘을 잠그지 않고 로캘을 참조하는 함수의 수를 반환하는 것이었습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|없음|

## <a name="see-also"></a>참고 항목

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
