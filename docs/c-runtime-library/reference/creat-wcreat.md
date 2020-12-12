---
description: '자세히 알아보기: _creat, _wcreat'
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 716f0d11af408ba30cb91744fd770300272dc26b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269044"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

새 파일을 만듭니다. **_creat** 및 **_wcreat** 사용 되지 않습니다. 대신 [_sopen_s _wsopen_s를](sopen-s-wsopen-s.md) 사용 하세요.

## <a name="syntax"></a>구문

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
새 파일의 이름입니다.

*pmode*<br/>
권한 설정

## <a name="return-value"></a>반환 값

이러한 함수는 성공하는 경우 생성된 파일에 파일 설명자를 반환합니다. 그렇지 않으면 함수는 다음 표에 나와 있는 것 처럼-1을 반환 하 고 **errno** 를 설정 합니다.

|**errno** 설정|설명|
|---------------------|-----------------|
|**EACCES**|*filename* 은 기존 읽기 전용 파일을 지정 하거나 파일 대신 디렉터리를 지정 합니다.|
|**EMFILE**|사용 가능한 추가 파일 설명자가 없습니다.|
|**ENOENT (**|지정된 파일을 찾을 수 없습니다.|

*Filename* 이 **NULL** 인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Creat** 함수는 새 파일을 만들거나 기존 파일을 열어 자릅니다. **_wcreat** 은 **_creat** 의 와이드 문자 버전입니다. **_wcreat** 에 대 한 *파일 이름* 인수는 와이드 문자열입니다. **_wcreat** 와 **_creat** 는 동일 하 게 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

*Filename* 으로 지정 된 파일이 없는 경우 지정 된 사용 권한 설정을 사용 하 여 새 파일이 만들어지고 쓰기용으로 열립니다. 파일이 이미 존재 하 고 해당 권한 설정으로 쓰기를 허용 하는 경우, **_creat** 파일을 길이가 0으로 잘리고 이전 내용을 삭제 한 다음 쓰기 위해 엽니다. 권한 설정인 *pmode* 는 새로 만든 파일에만 적용 됩니다. 새 파일은 처음으로 닫힌 이후 지정된 권한 설정을 받습니다. 정수 식 *pmode* 에는 Sys\sti\stvhs에 정의 된 매니페스트 상수 **_S_IWRITE** 및 **_S_IREAD** 중 하나 또는 둘 다가 포함 됩니다. 두 상수가 모두 지정 된 경우 비트 or 연산자 ( **&#124;** )를 사용 하 여 조인 됩니다. *Pmode* 매개 변수는 다음 값 중 하나로 설정 됩니다.

|값|정의|
|-----------|----------------|
|**_S_IWRITE**|쓰기를 허용합니다.|
|**_S_IREAD**|읽기를 허용합니다.|
|**_S_IREAD** &#124; **_S_IWRITE**|읽기 및 쓰기를 허용합니다.|

쓰기 권한이 부여되지 않은 경우 파일은 읽기 전용입니다. 모든 파일을 항상 읽을 수 있으므로 쓰기 전용 권한을 부여할 수 없습니다. 그런 다음 **_S_IWRITE** 및 **_S_IREAD**  |  **_S_IWRITE** 모드가 동일 합니다. **_Creat** 를 사용 하 여 연 파일은 항상 호환 모드로 열립니다 ( [_sopen](sopen-wsopen.md)참조) **_SH_DENYNO**.

**_creat** 사용 권한을 설정 하기 전에 *pmode* 에 현재 파일 사용 권한 마스크를 적용 합니다 ( [_umask](umask.md)참조). **_creat** 는 주로 이전 라이브러리와의 호환성을 위해 제공 됩니다. *Oflag* 매개 변수에서 **_O_CREAT** 및 **_O_TRUNC** 를 사용 하는 **_open** 호출은 **_creat** 와 같으며 새 코드에 사용 하는 것이 좋습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> 또는 \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>참고 항목

[하위 수준 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
