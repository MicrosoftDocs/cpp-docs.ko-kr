---
description: Scanf, _scanf_l, wscanf, _wscanf_l에 대해 자세히 알아보세요.
title: scanf, _scanf_l, wscanf, _wscanf_l
ms.date: 10/21/2019
api_name:
- _wscanf_l
- scanf
- _scanf_l
- wscanf
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
- _tscanf
- _scanf_l
- wscanf
- _wscanf_l
- scanf
- _tscanf_l
helpviewer_keywords:
- tscanf_l function
- _tscanf_l function
- reading data [C++], from input streams
- _tscanf function
- data [C++], reading from input stream
- scanf_l function
- scanf function
- wscanf function
- _scanf_l function
- tscanf function
- formatted data [C++], from input streams
- wscanf_l function
- _wscanf_l function
ms.assetid: 73eac607-117f-4be4-9ff0-4afd9cf3c848
ms.openlocfilehash: 4f87ae7caf2dbc197834864bc43a04be48f5c466
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289038"
---
# <a name="scanf-_scanf_l-wscanf-_wscanf_l"></a>scanf, _scanf_l, wscanf, _wscanf_l

표준 입력 스트림에서 형식이 지정된 데이터를 읽습니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)을 참조하세요.

> [!NOTE]
> Visual Studio 2015에서 `printf` 및 `scanf` 함수 패밀리는로 선언 되었으며 **`inline`** `<stdio.h>` 및 헤더로 이동 되었습니다 `<conio.h>` . 이전 코드를 마이그레이션하는 경우 이러한 함수와의 연결에 *LNK2019* 가 표시 될 수 있습니다. 자세한 내용은 [Visual C++ change history 2003-2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio)를 참조 하세요.

## <a name="syntax"></a>구문

```C
int scanf(
   const char *format [,
   argument]...
);
int _scanf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf(
   const wchar_t *format [,
   argument]...
);
int _wscanf_l(
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

성공적으로 변환되고 할당된 필드 수를 반환합니다. 이때 읽혀졌지만 할당되지 않은 필드는 반환 값에 포함되지 않습니다. 반환 값이 0이면 할당된 필드가 없음을 나타냅니다.

*Format* 이 **NULL** 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **EOF** 를 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 내용은 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**Scanf** 함수는 표준 입력 스트림 **stdin** 에서 데이터를 읽고 *인수* 에 지정 된 위치에 데이터를 씁니다. 각 *인수* 는 *형식의 형식* 지정자에 해당 하는 형식의 변수에 대 한 포인터 여야 합니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

> [!IMPORTANT]
> **Scanf** 를 사용 하 여 문자열을 읽을 때 항상 **% s** 형식에 대 한 너비를 지정 합니다 (예: **"% s"** 대신 **"% 32s"** ). 그렇지 않으면 형식이 잘못 지정 된 입력으로 인해 버퍼 오버런이 발생할 수 있습니다. 또는 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)이나 [fgets](fgets-fgetws.md)를 사용하는 것이 좋습니다.

**wscanf** 는 **scanf** 의 와이드 문자 버전입니다. **wscanf** 에 대 한 *format* 인수는 와이드 문자열입니다. **wscanf** 및 **SCANF** 는 스트림이 ANSI 모드에서 열리는 경우 동일 하 게 동작 합니다. **scanf** 는 현재 유니코드 스트림의 입력을 지원 하지 않습니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf**|**scanf**|**scanf**|**wscanf**|
|**_tscanf_l**|**_scanf_l**|**_scanf_l**|**_wscanf_l**|

자세한 내용은 [형식 사양 필드 - scanf 함수 및 wscanf 함수](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**scanf**, **_scanf_l**|\<stdio.h>|
|**wscanf**, **_wscanf_l**|\<stdio.h> 또는 \<wchar.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_scanf.c
// compile with: /W3
// This program uses the scanf and wscanf functions
// to read formatted input.

#include <stdio.h>

int main( void )
{
   int   i, result;
   float fp;
   char  c, s[81];
   wchar_t wc, ws[81];
   result = scanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws ); // C4996
   // Note: scanf and wscanf are deprecated; consider using scanf_s and wscanf_s
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
   result = wscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws ); // C4996
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

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
