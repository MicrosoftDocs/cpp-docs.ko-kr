---
description: '다음에 대 한 자세한 정보: _unlock'
title: _unlock
ms.date: 11/04/2016
api_name:
- _unlock
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unlock
- _unlock
helpviewer_keywords:
- unlock function
- _unlock function
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
ms.openlocfilehash: ca3b31dd2b1ff12f5dd98d93e12e76c3cc4f0864
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162153"
---
# <a name="_unlock"></a>_unlock

다중 스레드 잠금을 해제합니다.

> [!IMPORTANT]
> 이 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
void __cdecl _unlock(
   int locknum
);
```

#### <a name="parameters"></a>매개 변수

*locknum*<br/>
[in] 해제할 잠금의 식별자입니다.

## <a name="requirements"></a>요구 사항

**소스:** mlock.c

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_lock](../c-runtime-library/lock.md)
