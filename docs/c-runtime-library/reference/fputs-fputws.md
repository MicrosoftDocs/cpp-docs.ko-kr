---
description: '자세한 정보: fputs, fputws'
title: fputs, fputws
ms.date: 03/02/2021
api_name:
- fputs
- fputws
- _o_fputs
- _o_fputws
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
- fputs
- fputws
- _fputts
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.openlocfilehash: 3b38f3c369a567c00f17a0f4d905de324100a3d4
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236792"
---
# <a name="fputs-fputws"></a>`fputs`, `fputws`

스트림에 문자열을 씁니다.

## <a name="syntax"></a>구문

```C
int fputs(
   const char *str,
   FILE *stream
);
int fputws(
   const wchar_t *str,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*`str`*\
출력 문자열입니다.

*`stream`*\
구조체에 대 한 포인터 **`FILE`** 입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 성공할 경우 음수가 아닌 값을 반환합니다. 오류가 발생 **`fputs`** 하 고를 **`fputws`** 반환 **`EOF`** 합니다. *`str`* 또는 *`stream`* 가 null 포인터인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **`errno`** 를로 설정 하 **`EINVAL`** 고를 반환 **`EOF`** 합니다.

오류 코드에 대 한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 *`str`* *`stream`* 현재 위치에서 출력으로 복사 됩니다. **`fputws`***`str`* *`stream`* *`stream`* 는를 텍스트 모드에서 열지 아니면 이진 모드로 열지에 따라 와이드 문자 인수를 멀티 바이트 문자열 또는 와이드 문자열로 복사 합니다. 어떤 함수도 null 종결 문자를 복사하지 않습니다.

스트림이 ANSI 모드에서 열리는 경우 두 함수는 동일하게 작동합니다. **`fputs`** 는 현재 UNICODE 스트림에 대 한 출력을 지원 하지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT에서 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>일반 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_fputts`**|**`fputs`**|**`fputs`**|**`fputws`**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**`fputs`**|\<stdio.h>|
|**`fputws`**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔에 연결 된 표준 스트림 핸들 **`stdin`** , **`stdout`** 및은 **`stderr`** UWP 앱에서 C 런타임 함수를 사용 하려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fputs.c
// This program uses fputs to write
// a single line to the stdout stream.

#include <stdio.h>

int main( void )
{
   fputs( "Hello world from fputs.\n", stdout );
}
```

```Output
Hello world from fputs.
```

## <a name="see-also"></a>참고 항목

[스트림 i/o](../../c-runtime-library/stream-i-o.md)\
[`fgets`, `fgetws`](fgets-fgetws.md)\
[`gets`, `_getws`](../../c-runtime-library/gets-getws.md)\
[`puts`, `_putws`](puts-putws.md)
