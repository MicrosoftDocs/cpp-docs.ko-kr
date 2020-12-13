---
description: '다음에 대 한 자세한 정보: _get_wpgmptr'
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: fdc2f17a2c4d43a762f9fbab6629e2524742f0ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338931"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

**_Wpgmptr** 전역 변수의 현재 값을 가져옵니다.

## <a name="syntax"></a>구문

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>매개 변수

*pValue*<br/>
**_Wpgmptr** 변수의 현재 값으로 채울 문자열에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

성공하는 경우 0을 반환하고, 실패하는 경우 오류 코드를 반환합니다. *Pvalue* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

## <a name="remarks"></a>설명

프로그램에 **wmain ()** 또는 **wwinmain ()** 과 같은 넓은 진입점이 있는 경우에만 **_get_wpgmptr** 를 호출 합니다. **_Wpgmptr** 전역 변수는 프로세스와 연결 된 실행 파일의 전체 경로를 와이드 문자열로 포함 합니다. 자세한 내용은 [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_get_pgmptr](get-pgmptr.md)<br/>
