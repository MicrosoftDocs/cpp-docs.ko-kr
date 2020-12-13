---
description: '자세히 알아보기: _dupenv_s_dbg, _wdupenv_s_dbg'
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
api_name:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: a12e5adc55cd69b8336b3f9f50d982f80ec1b070
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332901"
---
# <a name="_dupenv_s_dbg-_wdupenv_s_dbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

현재 환경에서 값을 가져옵니다.  추가 디버깅 정보를 제공하기 위해 [_malloc_dbg](malloc-dbg.md)를 통해 메모리를 할당하는 [_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
변수 값을 저장하는 버퍼입니다.

*이면 numberofelements 이벤트가*<br/>
*버퍼* 의 크기입니다.

*varname*<br/>
환경 변수 이름입니다.

*blockType*<br/>
메모리 블록의 요청 된 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

*filename*<br/>
소스 파일의 이름에 대 한 포인터 이거나 **NULL** 입니다.

*linenumber*<br/>
소스 파일의 줄 번호 또는 **NULL** 입니다.

## <a name="return-value"></a>반환 값

성공 시 0, 실패 시 오류 코드가 나타납니다.

이러한 함수는 해당 매개 변수의 유효성을 검사 합니다. *buffer* 또는 *varname* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

이러한 함수는 충분 한 메모리를 할당할 수 없는 경우 *버퍼* 를 **NULL** 로 설정 하 고 *numberofelements* 를 0으로 설정 하 고 **enomem** 을 반환 합니다.

## <a name="remarks"></a>설명

**_Dupenv_s_dbg** 및 **_wdupenv_s_dbg** 함수는 **_dupenv_s** 및 **_wdupenv_s** 와 동일 합니다. 단, **_DEBUG** 가 정의 되 면 이러한 함수는 [malloc](malloc.md), [_malloc_dbg](malloc-dbg.md)의 디버그 버전을 사용 하 여 환경 변수 값에 대 한 메모리를 할당 합니다. **_Malloc_dbg** 의 디버깅 기능에 대 한 자세한 내용은 [_malloc_dbg](malloc-dbg.md)을 참조 하세요.

대부분의 경우 이러한 함수를 명시적으로 호출할 필요가 없습니다. 대신 **_CRTDBG_MAP_ALLOC** 플래그를 정의할 수 있습니다. **_CRTDBG_MAP_ALLOC** 가 정의 되 면 **_dupenv_s** 및 **_wdupenv_s** 에 대 한 호출이 각각 **_Dupenv_s_dbg** 및 **_wdupenv_s_dbg** 다시 매핑되고, *블록 형식이* **_NORMAL_BLOCK** 로 설정 됩니다. 따라서 힙 블록을 **_CLIENT_BLOCK** 으로 표시 하려는 경우가 아니면 이러한 함수를 명시적으로 호출할 필요가 없습니다. 블록 형식에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[환경 상수](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
