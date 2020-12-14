---
description: '자세히 알아보기: getchar, getwchar'
title: getchar, getwchar
ms.date: 06/23/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: d8480d179cc31d30d68c07fbe92bf389226ccd53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256759"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

표준 입력에서 문자를 읽습니다.

## <a name="syntax"></a>구문

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Return Value

읽은 문자를 반환합니다. 이러한 함수는 입력을 대기 하 고 입력을 사용할 수 있을 때까지 반환 되지 않습니다.

읽기 오류 또는 파일 끝 조건을 나타내려면 **getchar** 은 **EOF** 를 반환 하 고 **getwchar** 는 **weof** 를 반환 합니다. **Getchar** 의 경우 **ferror** 또는 **feof** 를 사용 하 여 오류 또는 파일 끝을 확인 합니다.

## <a name="remarks"></a>설명

각 루틴은 **stdin** 에서 단일 문자를 읽고 다음 문자를 가리키도록 연결 된 파일 포인터를 증가 시킵니다. **getchar** 는 [_fgetchar](fgetc-fgetwc.md)와 동일 하지만 함수 및 매크로로 구현 됩니다.

이러한 함수는 또한 호출 스레드를 잠그고 스레드로부터 안전 합니다. 잠기지 않는 버전의 경우 [_getchar_nolock, _getwchar_nolock](getchar-nolock-getwchar-nolock.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**getchar**|**getchar**|**getwchar**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**getchar**|\<stdio.h>|
|**getwchar**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
