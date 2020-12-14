---
description: '자세히 알아보기: _chmod, _wchmod'
title: _chmod, _wchmod
ms.date: 4/2/2020
api_name:
- _chmod
- _wchmod
- _o__chmod
- _o__wchmod
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
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: 601510c1f326282d48d2824b055ee3e80d9db0ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275037"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

파일 권한 설정을 변경합니다.

## <a name="syntax"></a>구문

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
기존 파일의 이름입니다.

*pmode*<br/>
파일에 대한 권한 설정입니다.

## <a name="return-value"></a>반환 값

권한 설정을 성공적으로 변경한 경우 이러한 함수는 0을 반환합니다. 반환 값-1은 실패를 나타냅니다. 지정 된 파일을 찾을 수 없는 경우 **errno** 는 **enoent (** 로 설정 됩니다. 매개 변수가 잘못 된 경우 **errno** 는 **EINVAL** 로 설정 됩니다.

## <a name="remarks"></a>설명

**_Chmod** 함수는 *filename* 에 지정 된 파일의 사용 권한 설정을 변경 합니다. 권한 설정은 파일에 대한 읽기 및 쓰기 액세스를 제어합니다. 정수 식 *pmode* 에는 다음 매니페스트 상수 중 하나 또는 둘 다가 포함 됩니다.

| *pmode* | 의미 |
|-|-|
| **\_S \_ IREAD** | 읽기만 허용합니다. |
| **\_S \_ IWRITE** | 쓰기를 허용합니다. 실제로는 읽기 및 쓰기를 모두 허용합니다. |
| **\_ S \_ iread** &#124; **\_ s- \_ write** | 읽기 및 쓰기를 허용합니다. |

두 상수가 모두 지정 된 경우 비트 or 연산자 ()와 조인 됩니다 **\|** . 쓰기 권한이 부여되지 않은 경우 파일은 읽기 전용입니다. 모든 파일을 항상 읽을 수 있으므로 쓰기 전용 권한을 부여할 수 없습니다. 따라서 **_S_IWRITE** 모드와 **_S_IREAD** \| **_S_IWRITE** 는 동일 합니다.

**_wchmod** 은 **_chmod** 의 와이드 문자 버전입니다. **_wchmod** 에 대 한 *파일 이름* 인수는 와이드 문자열입니다. **_wchmod** 와 **_chmod** 는 동일 하 게 동작 합니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Pmode* 가 매니페스트 상수 중 하나의 조합이 아니거나 대체 상수 집합을 통합 하는 경우 함수는 단순히 무시 합니다. *Filename* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는-1을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> 또는 \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat 함수](stat-functions.md)<br/>
