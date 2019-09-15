---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 8eb22f3716102c1b63b483e493eb44ac99228004
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955227"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md) 함수의 디버그 버전입니다(디버그 중에만 사용 가능).

## <a name="syntax"></a>구문

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*drive*<br/>
디스크 드라이브의 이름입니다.

*buffer*<br/>
경로의 스토리지 위치입니다.

*maxlen*<br/>
경로의 최대 길이 (문자: **_getdcwd_dbg** 의 경우 **char** , **_wgetdcwd_dbg**의 경우 **wchar_t** )입니다.

*blockType*<br/>
메모리 블록의 요청 된 유형: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

*filename*<br/>
할당 작업 또는 **NULL**을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
할당 작업이 요청 되었거나 **NULL 인**소스 파일의 줄 번호입니다.

## <a name="return-value"></a>반환 값

*버퍼*에 대 한 포인터를 반환 합니다. **Null** 반환 값은 오류를 나타내고 **errno** 는 *maxlen* 바이트를 할당할 메모리가 부족 함을 나타내는 **enomem**( **null** 인수가 *버퍼로*지정 된 경우) 또는 ERANGE로 설정 됩니다. *maxlen* 자 보다 긴 경로를 나타내는입니다. 자세한 내용은 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**_Getdcwd_dbg** 및 **_wgetdcwd_dbg** 함수는 **_getdcwd** 및 **_wgetdcwd** 와 동일 합니다. 단, **_debug** 가 정의 되 면 이러한 함수는 **malloc** 및 **_malloc_dbg** 의 디버그 버전을 사용 합니다. **NULL** 이 *buffer* 매개 변수로 전달 되는 경우 메모리를 할당 합니다. 자세한 내용은 [_malloc_dbg](malloc-dbg.md)를 참조하세요.

대부분의 경우 이러한 함수를 명시적으로 호출할 필요가 없습니다. 대신 **_CRTDBG_MAP_ALLOC** 플래그를 정의할 수 있습니다. **_CRTDBG_MAP_ALLOC** 가 정의 되 면 **_getdcwd** 및 **_wgetdcwd** 호출은 각각 **_Getdcwd_dbg** 및 **_wgetdcwd_dbg**에 다시 매핑되고, *블록 형식은* **_NORMAL_BLOCK**로 설정 됩니다. 따라서 힙 블록을 **_CLIENT_BLOCK**로 표시 하려는 경우가 아니면 이러한 함수를 명시적으로 호출할 필요가 없습니다. 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
