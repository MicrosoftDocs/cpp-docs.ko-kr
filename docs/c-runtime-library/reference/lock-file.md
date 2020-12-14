---
description: '다음에 대 한 자세한 정보: _lock_file'
title: _lock_file
ms.date: 4/2/2020
api_name:
- _lock_file
- _o__lock_file
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
- _lock_file
- lock_file
helpviewer_keywords:
- file locking [C++]
- _lock_file function
- lock_file function
ms.assetid: 75c7e0e6-efff-4747-b6ed-9bcf2b0894c3
ms.openlocfilehash: 1eba161b5083235c1ef0724284e74e6f0f7df0cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198832"
---
# <a name="_lock_file"></a>_lock_file

파일 개체에 동시에 액세스 **하는 스레드에** 대 한 일관성을 유지 하기 위해 **파일** 개체를 잠급니다.

## <a name="syntax"></a>구문

```C
void _lock_file( FILE* file );
```

### <a name="parameters"></a>매개 변수

*file*<br/>
파일 핸들입니다.

## <a name="remarks"></a>설명

**_Lock_file** 함수는 *file* 에서 지정 된 **파일** 개체를 잠급니다. 기본 파일이 **_lock_file** 에 의해 잠겨 있지 않습니다. 파일에 대한 잠금을 해제하려면 [_unlock_file](unlock-file.md)을 사용합니다. **_Lock_file** 및 **_unlock_file** 에 대 한 호출은 스레드에서 일치 해야 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_lock_file**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_lock_file.c
// This example creates multiple threads that write to standard output
// concurrently, first with _file_lock, then without.

#include <stdio.h>
#include <process.h>// _beginthread
#include <windows.h>// HANDLE

void Task_locked( void* str )
{
    for( int i=0; i<1000; ++i )
    {
        _lock_file( stdout );
        for( char* cp = (char*)str; *cp; ++cp )
        {
            _fputc_nolock( *cp, stdout );
        }
        _unlock_file( stdout );
    }
}

void Task_unlocked( void* str )
{
    for( int i=0; i<1000; ++i )
    {
        for( char* cp = (char*)str; *cp; ++cp )
        {
            fputc( *cp, stdout );
        }
    }
}

int main()
{
    HANDLE h[3];
    h[0] = (HANDLE)_beginthread( &Task_locked, 0, "First\n" );
    h[1] = (HANDLE)_beginthread( &Task_locked, 0, "Second\n" );
    h[2] = (HANDLE)_beginthread( &Task_locked, 0, "Third\n" );

    WaitForMultipleObjects( 3, h, true, INFINITE );

    h[0] = (HANDLE)_beginthread( &Task_unlocked, 0, "First\n" );
    h[1] = (HANDLE)_beginthread( &Task_unlocked, 0, "Second\n" );
    h[2] = (HANDLE)_beginthread( &Task_unlocked, 0, "Third\n" );

    WaitForMultipleObjects( 3, h, true, INFINITE );
}
```

```Output
...
First
Second
First
Second
Third
Second
Third
Second
...
FSiercsotn
dF
iSrescto
nFdi
rSsetc
oFnidr
sSte
cFoinrds
tS
eFciornsdt
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlock_file](unlock-file.md)<br/>
