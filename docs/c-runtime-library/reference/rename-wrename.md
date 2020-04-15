---
title: rename, _wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- _wrename
- _trename
- Rename
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338112"
---
# <a name="rename-_wrename"></a>rename, _wrename

파일 또는 디렉터리의 이름을 바꿉니다.

## <a name="syntax"></a>구문

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>매개 변수

*oldname*<br/>
이전 이름에 대한 포인터입니다.

*newname*<br/>
새 이름에 대한 포인터입니다.

## <a name="return-value"></a>Return Value

이러한 각 함수는 정상적으로 실행되는 경우 0을 반환합니다. 오류에서 함수는 zero가 아닌 값을 반환하고 **errno를** 다음 값 중 하나로 설정합니다.

|errno 값|조건|
|-|-|
| **EACCES** | *newname*으로 지정된 파일/디렉터리가 이미 있거나 만들 수 없는 상태입니다(잘못된 경로). 또는 *oldname*이 디렉터리인데 *newname*은 다른 경로를 지정합니다. |
| **이노엔트 (이노엔트 주)** | *oldname*로 지정된 파일 또는 경로를 찾을 수 없습니다. |
| **아인발 ()에인발 (것)** | 이름에 잘못된 문자가 포함되어 있습니다. |

사용 가능한 다른 반환 값은 [_doserrno, _errno, syserrlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**rename** 함수는 *oldname*으로 지정된 파일이나 디렉터리의 이름을 *newname*으로 지정된 이름으로 바꿉니다. 이전 이름은 기존 파일이나 디렉터리의 경로여야 합니다. 새 이름은 기존 파일 또는 디렉터리의 이름이 아니어야 합니다. **rename**을 사용하면 *newname* 인수에 다른 경로를 제공하여 디렉터리나 디바이스 간에 파일을 이동할 수 있습니다. 그러나 **rename**을 사용하여 디렉터리를 이동할 수는 없습니다. 디렉터리는 이름을 바꿀 수는 있지만 이동할 수는 없습니다.

**_wrename** **_rename**와이드 문자 버전입니다. **_wrename** 인수는 와이드 문자 문자열입니다. **_wrename** **_rename** 다르게 동일하게 행동합니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**이름을 바꿀**|**이름을 바꿀**|**_wrename**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**이름을 바꿀**|\<io.h> 또는 \<stdio.h>|
|**_wrename**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>출력

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
