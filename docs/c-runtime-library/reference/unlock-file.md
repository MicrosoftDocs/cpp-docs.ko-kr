---
description: '다음에 대 한 자세한 정보: _unlock_file'
title: _unlock_file
ms.date: 4/2/2020
api_name:
- _unlock_file
- _o__unlock_file
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: 6b639ca178f9cb397e9ec14f383b952e94400e7c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299360"
---
# <a name="_unlock_file"></a>_unlock_file

다른 프로세스에서 파일에 액세스할 수 있도록 파일의 잠금을 해제합니다.

## <a name="syntax"></a>구문

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>매개 변수

*file*<br/>
파일 핸들입니다.

## <a name="remarks"></a>설명

**_Unlock_file** 함수는 *파일* 에 지정 된 파일의 잠금을 해제 합니다. 파일의 잠금을 해제하면 다른 프로세스에서 파일에 액세스할 수 있습니다. **_Lock_file** 이전에 *파일* 포인터에서 호출 된 경우가 아니면이 함수를 호출 하면 안 됩니다. 잠기지 않은 파일에 대해 **_unlock_file** 를 호출 하면 교착 상태가 발생할 수 있습니다. 관련 예제는 [_lock_file](lock-file.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
