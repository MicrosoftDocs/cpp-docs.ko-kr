---
description: '자세한 정보: fputs, fputws'
title: fputs, fputws
ms.date: 4/2/2020
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
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
ms.openlocfilehash: bba51a6001d9ec27f39b590b2246a50409f5e47d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314115"
---
# <a name="fputs-fputws"></a>fputs, fputws

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

*str*<br/>
출력 문자열입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 성공할 경우 음수가 아닌 값을 반환합니다. 오류가 발생 하면 **fputs** 및 **fputws** 가 **EOF** 를 반환 합니다. *Str* 또는 *stream* 이 null 포인터인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **fputs** 은 **EOF** 를 반환 하며 **fputws** **는 weof** 를 반환 합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 *str* 을 현재 위치의 출력 *스트림으로* 복사 합니다. **fputws** 는 *스트림을* 텍스트 모드에서 열지 아니면 이진 모드로 *열지에 따라* 와이드 문자 인수 *str* 를 멀티 바이트 문자열 또는 와이드 문자열로 복사 합니다. 어떤 함수도 null 종결 문자를 복사하지 않습니다.

스트림이 ANSI 모드에서 열리는 경우 두 함수는 동일하게 작동합니다. **fputs** 은 현재 유니코드 스트림에 대 한 출력을 지원 하지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputts**|**fputs**|**fputs**|**fputws**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fputs**|\<stdio.h>|
|**fputws**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔에 연결 된 표준 스트림 핸들 (**stdin**, **stdout** 및 **stderr**)은 C 런타임 함수가 UWP 앱에서 사용할 수 있도록 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

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

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
