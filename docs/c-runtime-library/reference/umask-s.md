---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362173"
---
# <a name="_umask_s"></a>_umask_s

기본 파일 사용 권한 마스크를 설정합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [_umask](umask.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>매개 변수

*모드*<br/>
기본 사용 권한 설정입니다.

*폴드 모드*<br/>
사용 권한 설정의 이전 값입니다.

## <a name="return-value"></a>Return Value

*모드가* 유효한 모드를 지정하지 않거나 *pOldMode* 포인터가 **NULL인**경우 오류 코드를 반환합니다.

### <a name="error-conditions"></a>오류 조건

|*모드*|*폴드 모드*|반환 값|*pOldMode의* 내용|
|------------|----------------|----------------------|--------------------------------|
|any|**Null**|**아인발 ()에인발 (것)**|수정 안 됨|
|잘못된 모드|any|**아인발 ()에인발 (것)**|수정 안 됨|

위의 오류 조건 중 하나가 발생하는 경우, [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속할 수 있는 경우 **_umask_s** **EINVAL을** 반환하고 **errno를** **EINVAL로**설정합니다.

## <a name="remarks"></a>설명

**_umask_s** 함수는 현재 프로세스의 파일 권한 마스크를 *모드로*지정된 모드로 설정합니다. 파일 권한 마스크는 **_creat**, **_open**또는 **_sopen**에서 만든 새 파일의 권한 설정을 수정합니다. 마스크의 비트가 1이면 파일의 요청된 사용 권한 값에서 해당하는 비트가 0(허용되지 않음)으로 설정됩니다. 마스크의 비트가 0이면 해당하는 비트는 변경되지 않고 그대로 유지됩니다. 새 파일에 대한 사용 권한 설정은 파일을 처음으로 닫을 때까지 설정되지 않습니다.

정수 식 *pmode* pmodeSS\STAT에 정의 된 다음 매니페스트 상 중 하나 또는 둘 모두를 포함 합니다. H:

|*Pmode*||
|-|-|
|**_S_IWRITE**|쓰기를 허용합니다.|
|**_S_IREAD**|읽기를 허용합니다.|
|**_S_IREAD** \| **_S_IWRITE**|읽기 및 쓰기를 허용합니다.|

두 상수가 모두 부여되면 비트와이즈-OR 연산자()와 **|** 결합됩니다. *모드* 인수가 **_S_IREAD**경우 읽기가 허용되지 않습니다(파일은 쓰기 전용). *모드* 인수가 **_S_IWRITE**경우 쓰기가 허용되지 않습니다(파일은 읽기 전용). 예를 들어 마스크에 쓰기 비트가 설정되어 있으면 모든 새 파일은 읽기 전용이 됩니다. MS-DOS 및 Windows 운영 체제에서는 모든 파일을 읽을 수는 있지만 쓰기 전용 권한을 부여할 수는 없습니다. 따라서 읽기 비트를 **_umask_s** 설정하면 파일의 모드에 영향을 주지 않습니다.

*pmode가* 매니페스트 상수 중 하나의 조합이 아니거나 대체 상수 집합을 통합하는 경우 함수는 단순히 무시합니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_umask_s**|\<io.h>, \<sys/stat.h> 및 \<sys/types.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
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
[_umask](umask.md)<br/>
