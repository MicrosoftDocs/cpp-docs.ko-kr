---
description: '다음에 대 한 자세한 정보: _set_doserrno'
title: _set_doserrno
ms.date: 4/2/2020
api_name:
- _set_doserrno
- _o__set_doserrno
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
- _set_doserrno
- set_doserrno
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
ms.openlocfilehash: c4b7860764505ab7d3388bace6fa86b0726851e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334107"
---
# <a name="_set_doserrno"></a>_set_doserrno

[_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 전역 변수의 값을 설정합니다.

## <a name="syntax"></a>구문

```C
errno_t _set_doserrno( int error_value );
```

### <a name="parameters"></a>매개 변수

*error_value*<br/>
**_Doserrno** 의 새 값입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환합니다.

## <a name="remarks"></a>설명

가능한 값은 Errno.h에서 정의됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_set_doserrno**|\<stdlib.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_get_doserrno](get-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
