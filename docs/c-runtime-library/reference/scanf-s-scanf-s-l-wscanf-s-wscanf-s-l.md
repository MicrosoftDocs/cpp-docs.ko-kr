---
description: '자세한 정보: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l'
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: f7044a5f0a29e9421b7105ac177228e7fad3ab30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289103"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

표준 입력 스트림에서 형식이 지정된 데이터를 읽습니다. 이러한 버전의 [scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

## <a name="syntax"></a>구문

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>매개 변수

*format*<br/>
형식 컨트롤 문자열입니다.

*argument*<br/>
선택적 인수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공적으로 변환 되 고 할당 된 필드 수를 반환 합니다. 읽은 필드가 있지만 할당 되지 않은 필드는 반환 값에 포함 되지 않습니다. 반환 값이 0 이면 할당 된 필드가 없음을 나타냅니다. 반환 값은 오류에 대 한 **EOF** 이거나 파일 끝 문자 또는 문자열 끝 문자가 문자를 읽으려고 하는 첫 번째 시도에서 발견 된 경우입니다. *Format* 이 **NULL** 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 **scanf_s** 해 서 실행 하도록 허용한 경우 **EOF** 를 반환 하 고 **errno** 를 **EINVAL** 로 설정 **wscanf_s** 합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist, 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**Scanf_s** 함수는 표준 입력 스트림 **stdin** 에서 데이터를 읽고 *인수* 에 씁니다. 각 *인수* *는 형식 지정자* 에 해당 하는 변수 형식에 대 한 포인터 여야 합니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

**wscanf_s** 은 **scanf_s** 의 와이드 문자 버전입니다. **wscanf_s** 에 대 한 *format* 인수는 와이드 문자 문자열입니다. **wscanf_s** 및 **SCANF_S** 는 스트림이 ANSI 모드에서 열리는 경우 동일 하 게 동작 합니다. **scanf_s** 는 현재 유니코드 스트림의 입력을 지원 하지 않습니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 *로캘* 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

**Scanf** 및 **wscanf** 와 달리 **scanf_s** 및 **wscanf_s** 에는 일부 매개 변수에 대해 버퍼 크기를 지정 해야 합니다. 모든 **c**, **c**, **s**, **s** 또는 문자열 컨트롤 집합 **[]** 매개 변수의 크기를 지정 합니다. 문자에서 버퍼 크기는 추가 매개 변수로 전달 됩니다. 버퍼 또는 변수에 대 한 포인터 바로 다음에 옵니다. 예를 들어 문자열을 읽는 경우 해당 문자열에 대 한 버퍼 크기가 다음과 같이 전달 됩니다.

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

버퍼 크기에는 터미널 null이 포함 됩니다. 너비 사양 필드를 사용 하 여 읽은 토큰이 버퍼에 맞는지 확인할 수 있습니다. 토큰이 너무 커서에 맞지 않는 경우에는 너비 사양이 없으면 버퍼에 아무 것도 쓰여지지 않습니다.

> [!NOTE]
> Size 매개 변수는 size_t이 **`unsigned`** 아니라 형식 입니다. 64 비트 빌드 구성의 경우 정적 캐스트를 사용 하 여 **size_t** 값을로 변환 **`unsigned`** 합니다.

버퍼 크기 매개 변수는 바이트가 아닌 문자의 최대 수를 설명 합니다. 이 예제에서는 버퍼 형식의 너비가 서식 지정자의 너비와 일치 하지 않습니다.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S** 형식 지정자는 함수에서 지 원하는 기본 너비의 "반대" 문자 너비를 사용 함을 의미 합니다. 문자 너비는 싱글바이트 이지만 함수는 더블 바이트 문자를 지원 합니다. 이 예에서는 최대 9 개의 싱글바이트 와이드 문자로 이루어진 문자열을 읽고 더블 바이트 와이드 문자 버퍼에 넣습니다. 문자는 싱글바이트 값으로 처리됩니다. 처음 두 문자는 `ws[0]`에 저장되고, 두 번째 두 문자는 `ws[1]`에 저장되는 방식입니다.

이 예제에서는 단일 문자를 읽습니다.

```C
char c;
scanf_s("%c", &c, 1);
```

Null로 종료 되는 문자열에 대 한 여러 문자를 읽을 때 정수는 너비 사양과 버퍼 크기 모두에 사용 됩니다.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

자세한 내용은 [scanf 너비 사양](../../c-runtime-library/scanf-width-specification.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

자세한 내용은 [서식 지정 필드: scanf 함수 및 wscanf 함수](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 표준 스트림이 **stdin**, **stdout** 및 **stderr** 을 처리 해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

이 프로그램을 실행하면 이 입력이 제공될 때 다음 출력이 생성됩니다.

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
