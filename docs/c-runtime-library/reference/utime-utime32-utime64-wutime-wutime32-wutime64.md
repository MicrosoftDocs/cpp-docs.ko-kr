---
description: '자세한 정보: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64'
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 4/2/2020
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
- _o__utime32
- _o__utime64
- _o__wutime32
- _o__wutime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: 7ec25f60c508464abf8232419f8867bc3f0a20fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299347"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

파일 수정 시간을 설정합니다.

## <a name="syntax"></a>구문

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
경로 또는 파일 이름을 포함하는 문자열에 대한 포인터입니다.

*times*<br/>
저장된 시간 값에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

파일 수정 시간을 변경한 경우 이러한 각 함수는 0을 반환합니다. 반환 값-1은 오류를 나타냅니다. 잘못된 매개 변수를 전달하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 는 다음 값 중 하나로 설정 됩니다.

|errno 값|조건|
|-|-|
| **EACCES** | 경로가 디렉터리 또는 읽기 전용 파일을 지정함 |
| **EINVAL** | 잘못 된 *시간* 인수 |
| **EMFILE** | 파일이 너무 많이 열려 있음(수정 시간을 변경하려면 파일을 열어야 함) |
| **ENOENT (** | 경로 또는 파일 이름을 찾을 수 없음 |

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

변경 날짜가 1970년 1월 1일 자정 이후이고 사용한 함수의 종료 날짜 이전이면 파일의 날짜를 변경할 수 있습니다. **_utime** 및 **_wutime** 64 비트 시간 값을 사용 하므로 종료 날짜는 23:59:59 년 12 월 31 일 3000, UTC입니다. 이전 동작을 강제 하도록 **_USE_32BIT_TIME_T** 정의 된 경우 종료 날짜는 2038 년 1 월 18 일 23:59:59입니다. **_utime32** 또는 **_wutime32** **_USE_32BIT_TIME_T** 정의 여부에 관계 없이 32 비트 시간 형식을 사용 하 고 항상 이전 종료 날짜를 사용 합니다. **_utime64** 또는 **_wutime64** 는 항상 64 비트 시간 형식을 사용 하므로 이러한 함수는 항상 이후 종료 날짜를 지원 합니다.

## <a name="remarks"></a>설명

**_Utime** 함수는 *filename* 에 지정 된 파일의 수정 시간을 설정 합니다. 시간을 변경하려면 프로세스에 파일에 대한 쓰기 권한이 있어야 합니다. Windows 운영 체제에서 **_utimbuf** 구조의 액세스 시간 및 수정 시간을 변경할 수 있습니다. *Times* 가 **NULL** 포인터인 경우에는 수정 시간이 현재 현지 시간으로 설정 됩니다. 그렇지 않으면 *시간은* SYS\UTIME.H.에 정의 된 **_utimbuf** 형식의 구조체를 가리켜야 합니다.

**_Utimbuf** 구조는 **_utime** 에서 파일 수정 날짜를 변경 하는 데 사용 되는 파일 액세스 및 수정 시간을 저장 합니다. 구조에는 다음과 같은 필드가 있습니다. 이러한 필드는 모두 **time_t** 형식입니다.

| 필드 |   |
|-------|---|
| **actime** | 파일 액세스 시간 |
| **modtime** | 파일 수정 시간 |

특정 버전의 **_utimbuf** 구조 (**_utimebuf32** 및 **__utimbuf64**)는 시간 형식의 32 비트 및 64 비트 버전을 사용 하 여 정의 됩니다. 이러한 구조체는 이 함수의 32비트 및 64비트별 버전에서 사용됩니다. **_USE_32BIT_TIME_T** 정의 되지 않은 경우 기본적으로 **_utimbuf** 자체는 64 비트 시간 형식을 사용 합니다.

**_utime** 은 **_futime** 와 동일 합니다. 단, **_utime** *의 파일 이름 인수는* 열려 있는 파일의 파일 설명자가 아니라 파일 이름 또는 파일 경로입니다.

**_wutime** 은 **_utime** 의 와이드 문자 버전입니다. **_wutime** 에 대 한 *파일 이름* 인수는 와이드 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> 또는 \<wchar.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램은 **_utime** 를 사용 하 여 파일 수정 시간을 현재 시간으로 설정 합니다.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>샘플 출력

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat 함수](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
