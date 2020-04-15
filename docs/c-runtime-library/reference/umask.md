---
title: _umask
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: b451f979f2925a31f5baaac52351c5d2c0a76da0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362026"
---
# <a name="_umask"></a>_umask

기본 파일 사용 권한 마스크를 설정합니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [_umask_s](umask-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _umask( int pmode );
```

### <a name="parameters"></a>매개 변수

*Pmode*<br/>
기본 사용 권한 설정입니다.

## <a name="return-value"></a>Return Value

**_umask** *pmode의*이전 값을 반환합니다. 반환되는 오류가 없습니다.

## <a name="remarks"></a>설명

**_umask** 함수는 현재 프로세스의 파일 권한 마스크를 *pmode로*지정된 모드로 설정합니다. 파일 권한 마스크는 **_creat**, **_open**또는 **_sopen**에서 만든 새 파일의 권한 설정을 수정합니다. 마스크의 비트가 1이면 파일의 요청된 사용 권한 값에서 해당하는 비트가 0(허용되지 않음)으로 설정됩니다. 마스크의 비트가 0이면 해당하는 비트는 변경되지 않고 그대로 유지됩니다. 새 파일에 대한 사용 권한 설정은 파일을 처음으로 닫을 때까지 설정되지 않습니다.

정수 식 *pmode* pmodeSS\STAT에 정의 된 다음 매니페스트 상 중 하나 또는 둘 모두를 포함 합니다. H:

|*Pmode*| |
|-|-|
| **_S_IWRITE** | 쓰기를 허용합니다. |
| **_S_IREAD** | 읽기를 허용합니다. |
| **_S_IREAD** &#124; **_S_IWRITE** | 읽기 및 쓰기를 허용합니다. |

두 상수가 모두 부여되면 비트와이즈 OR 연산자(&#124;)와 결합됩니다. **&#124;** *pmode* 인수가 **_S_IREAD**경우 읽기가 허용되지 않습니다(파일은 쓰기 전용). *pmode* 인수가 **_S_IWRITE**경우 쓰기가 허용되지 않습니다(파일은 읽기 전용). 예를 들어 마스크에 쓰기 비트가 설정되어 있으면 모든 새 파일은 읽기 전용이 됩니다. MS-DOS 및 Windows 운영 체제에서는 모든 파일을 읽을 수는 있지만 쓰기 전용 권한을 부여할 수는 없습니다. 따라서 **_umask** 읽기 비트를 설정하면 파일의 모드에 영향을 주지 않습니다.

*pmode가* 매니페스트 상수 중 하나의 조합이 아니거나 대체 상수 집합을 통합하는 경우 함수는 단순히 무시합니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[하위 수준 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
