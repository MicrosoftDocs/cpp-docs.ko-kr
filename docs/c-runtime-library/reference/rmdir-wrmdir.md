---
description: '자세히 알아보기: _rmdir, _wrmdir'
title: _rmdir, _wrmdir
ms.date: 4/2/2020
api_name:
- _wrmdir
- _rmdir
- _o__rmdir
- _o__wrmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: c17324d5d2125f4f664140684c4f082181742700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250310"
---
# <a name="_rmdir-_wrmdir"></a>_rmdir, _wrmdir

디렉터리를 삭제합니다.

## <a name="syntax"></a>구문

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>매개 변수

*dirname*<br/>
제거할 디렉터리의 경로입니다.

## <a name="return-value"></a>반환 값

디렉터리가 정상적으로 삭제되면 이러한 각 함수는 0을 반환합니다. 반환 값-1은 오류를 나타내고 **errno** 은 다음 값 중 하나로 설정 됩니다.

|errno 값|조건|
|-|-|
| **ENOTEMPTY** | 지정된 경로가 디렉터리가 아니거나, 디렉터리가 비어 있지 않거나, 디렉터리가 현재 작업 디렉터리 또는 루트 디렉터리입니다. |
| **ENOENT (** | 경로가 잘못되었습니다. |
| **EACCES** | 프로그램에 디렉터리에 대한 열린 핸들이 있습니다. |

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Rmdir** 함수는 *이름* 으로 지정 된 디렉터리를 삭제 합니다. 디렉터리는 비어 있어야 하고, 현재 작업 디렉터리나 루트 디렉터리가 아니어야 합니다.

**_wrmdir** 은 **_rmdir** 의 와이드 문자 버전입니다. **_wrmdir** 에 대 한 대상 *이름* 인수는 와이드 문자열입니다. **_wrmdir** 와 **_rmdir** 는 동일 하 게 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

[_mkdir](mkdir-wmkdir.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
