---
description: '자세히 알아보기: _getcwd_dbg, _wgetcwd_dbg'
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: e470402cc258bf0fa0512136229eeace5bac466e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256603"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg, _wgetcwd_dbg

[_getcwd, _wgetcwd](getcwd-wgetcwd.md) 함수의 디버그 버전입니다(디버그 중에만 사용 가능).

## <a name="syntax"></a>구문

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
경로의 스토리지 위치입니다.

*maxlen*<br/>
경로의 최대 길이 (문자): **`char`** **_getcwd_dbg** 및 **`wchar_t`** **_wgetcwd_dbg** 의 최대 길이입니다.

*blockType*<br/>
메모리 블록의 요청 된 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

*filename*<br/>
할당 작업 또는 **NULL** 을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
할당 작업이 요청 되었거나 **NULL 인** 소스 파일의 줄 번호입니다.

## <a name="return-value"></a>반환 값

*버퍼* 에 대 한 포인터를 반환 합니다. **Null** 반환 값은 오류를 나타내며, **errno** 는 *maxlen* 바이트를 할당할 메모리가 부족 함을 나타내는 **enomem**( **null** 인수가 *버퍼로* 지정 된 경우) 또는 **ERANGE**()로 설정 되어 경로가 *maxlen* 자 보다 긴 것을 나타냅니다.

자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Getcwd_dbg** 및 **_wgetcwd_dbg** 함수는 **_getcwd** 및 **_wgetcwd** 와 동일 합니다. 단, **_DEBUG** 정의 될 때 이러한 함수는 **NULL** 이 첫 번째 매개 변수로 전달 되는 경우 **malloc** 및 **_malloc_dbg** 의 디버그 버전을 사용 하 여 메모리를 할당 합니다. 자세한 내용은 [_malloc_dbg](malloc-dbg.md)를 참조하세요.

대부분의 경우 이러한 함수를 명시적으로 호출할 필요가 없습니다. 대신 **_CRTDBG_MAP_ALLOC** 플래그를 정의할 수 있습니다. **_CRTDBG_MAP_ALLOC** 가 정의 되 면 **_getcwd** 및 **_wgetcwd** 에 대 한 호출이 각각 **_Getcwd_dbg** 및 **_wgetcwd_dbg** 다시 매핑되고, *블록 형식이* **_NORMAL_BLOCK** 로 설정 됩니다. 따라서 힙 블록을 **_CLIENT_BLOCK** 으로 표시 하려는 경우가 아니면 이러한 함수를 명시적으로 호출할 필요가 없습니다. 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조 하세요.

## <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[디렉터리 제어](../../c-runtime-library/directory-control.md)<br/>
[힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
