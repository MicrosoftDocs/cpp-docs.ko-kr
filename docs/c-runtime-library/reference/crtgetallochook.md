---
description: '다음에 대 한 자세한 정보: _CrtGetAllocHook'
title: _CrtGetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtGetAllocHook
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
- CrtGetAllocHook
- _CrtGetAllocHook
helpviewer_keywords:
- _CrtGetAllocHook function
- CrtGetAllocHook function
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
ms.openlocfilehash: 997e3a03f0c9b56fda3a0fd89daf606a652136c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319767"
---
# <a name="_crtgetallochook"></a>_CrtGetAllocHook

C 런타임 디버그 메모리 할당 프로세스에 연결하기 위해 현재 클라이언트 정의 할당 함수를 검색합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );
```

## <a name="return-value"></a>Return Value

현재 정의된 할당 후크 함수를 반환합니다.

## <a name="remarks"></a>설명

**_CrtGetAllocHook** 는 C 런타임 디버그 라이브러리 메모리 할당 프로세스에 대 한 현재 클라이언트 정의 응용 프로그램 후크 함수를 검색 합니다.

다른 후크 가능 런타임 함수를 사용하고 고유한 클라이언트 정의 후크 함수를 작성하는 방법에 대한 자세한 내용은 [디버그 후크 함수 작성](/visualstudio/debugger/debug-hook-function-writing)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtGetAllocHook**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetAllocHook](crtsetallochook.md)<br/>
