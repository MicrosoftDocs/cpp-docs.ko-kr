---
description: '다음에 대 한 자세한 정보: _setmaxstdio'
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: ef34c3cf69f9664e5af593e4f0fa1e1046faff9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342233"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

스트림 I/O 수준에서 동시에 열려 있는 파일 수의 최댓값을 설정합니다.

## <a name="syntax"></a>구문

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>매개 변수

*new_max*<br/>
스트림 I/O 수준에서 동시에 열려 있는 파일 수에 대한 새로운 최댓값.

## <a name="return-value"></a>반환 값

정상적으로 실행되면 *new_max* 를 반환하고, 그렇지 않으면 -1을 반환합니다.

*new_max* 가 **_IOB_ENTRIES** 보다 작거나 운영 체제에서 사용 가능한 최대 핸들 수보다 많으면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속해서 실행하도록 허용된 경우 이 함수는 -1을 반환하고 **errno** 를 **EINVAL** 로 설정합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**_setmaxstdio** 함수는 스트림 I/O 수준에서 동시에 열 수 있는 파일 수의 최댓값을 변경합니다.

C 런타임 I/O는 이제 [낮은 I/O 수준](../../c-runtime-library/low-level-i-o.md)에서 동시에 열리는 최대 8,192개의 파일을 지원합니다. 이 수준에는 I/O 함수의 **_open**, **_read** 및 **_write** 패밀리를 사용하여 열고 액세스하는 파일이 포함됩니다. 기본적으로 [스트림 I/O 수준](../../c-runtime-library/stream-i-o.md)에서 최대 512개의 파일을 동시에 열 수 있습니다. 이 수준에는 함수의 **fopen**, **fgetc** 및 **fputc** 패밀리를 사용하여 열고 액세스하는 파일이 포함됩니다. 스트림 I/O 수준에서 열 수 있는 파일 수에 대한 제한(512개)은 **_setmaxstdio** 함수를 사용하여 최대 8,192개까지 늘릴 수 있습니다.

**fopen** 과 같은 스트림 I/O 수준 함수는 낮은 I/O 함수를 기반으로 빌드되므로 최댓값 8,192는 C 런타임 라이브러리를 통해 액세스하는 동시에 열 수 있는 파일 수에 대한 하드 상한입니다.

> [!NOTE]
> 이 상한은 특정 Win32 플랫폼 및 구성에서 지원하는 수를 초과할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

**_setmaxstdio** 를 사용하는 예제는 [_getmaxstdio](getmaxstdio.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
