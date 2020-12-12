---
description: '다음에 대 한 자세한 정보: _CrtGetDumpClient'
title: _CrtGetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtGetDumpClient
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
- CrtGetDumpClient
- _CrtGetDumpClient
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
ms.openlocfilehash: b4163e6f4f252eddd304f2704c3f5a9aa62b5371
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319754"
---
# <a name="_crtgetdumpclient"></a>_CrtGetDumpClient

**_CLIENT_BLOCK** 형식 메모리 블록을 덤프 하기 위해 현재 응용 프로그램 정의 함수를 검색 합니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );
```

## <a name="return-value"></a>Return Value

현재 덤프 루틴을 반환합니다.

## <a name="remarks"></a>설명

**_CrtGetDumpClient** 함수는 C 런타임 디버그 메모리 덤프 프로세스에 대 한 **_CLIENT_BLOCK** 메모리 블록에 저장 된 개체를 덤프 하기 위해 현재 후크 함수를 검색 합니다.

다른 후크 가능 런타임 함수를 사용하고 고유한 클라이언트 정의 후크 함수를 작성하는 방법에 대한 자세한 내용은 [디버그 후크 함수 작성](/visualstudio/debugger/debug-hook-function-writing)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtGetDumpClient**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
