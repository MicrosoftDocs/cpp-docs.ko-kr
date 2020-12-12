---
description: '자세히 알아보기: _fputchar, _fputwchar'
title: _fputchar, _fputwchar
ms.date: 4/2/2020
api_name:
- _fputchar
- _fputwchar
- _o__fputchar
- _o__fputwchar
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
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- _fputchar
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
ms.openlocfilehash: f682f134c3435392176155865f4808a6178ce35a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314193"
---
# <a name="_fputchar-_fputwchar"></a>_fputchar, _fputwchar

**stdout** 에 문자를 씁니다.

## <a name="syntax"></a>구문

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
쓸 문자입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 기록된 문자를 반환합니다. **_Fputchar** 의 경우 **EOF** 의 반환 값은 오류를 나타냅니다. **_Fputwchar** 의 경우 **weof** 반환 값은 오류를 나타냅니다. C가 **NULL** 인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 예외를 생성 합니다. 계속 해 서 실행 하도록 허용한 경우 **EOF** (또는 **weof**)를 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

이 두 함수는 단일 문자 *c* 를 **stdout** 에 쓰고 표시기를 적절히 앞으로 이동 합니다. **_fputchar** 는와 동일 `fputc( stdout )` 합니다. **Putchar** 와 동일 하지만 함수 및 매크로가 아닌 함수로만 구현 됩니다. **Fputc** 및 **putchar** 와 달리 이러한 함수는 ANSI 표준과 호환 되지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fputchar**|\<stdio.h>|
|**_fputwchar**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔에 연결 된 표준 스트림 핸들 (**stdin**, **stdout** 및 **stderr**)은 C 런타임 함수가 UWP 앱에서 사용할 수 있도록 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
