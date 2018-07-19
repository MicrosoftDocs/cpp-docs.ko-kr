---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
apilocation:
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
apitype: DLLExport
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
dev_langs:
- C++
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08cdc1b3fe2d190bdc4a6cbb3d505378e6dcf6ae
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451825"
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

문자열에서 형식이 지정된 데이터를 읽습니다. 이러한 버전의 [sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

## <a name="syntax"></a>구문

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>매개 변수

*buffer*<br/>
저장된 데이터

*format*<br/>
형식 컨트롤 문자열입니다. 자세한 내용은 [서식 지정 필드: scanf 함수 및 wscanf 함수](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)를 참조하세요.

*argument*<br/>
선택적 인수

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 모두 성공적으로 변환되고 할당된 필드 수를 반환합니다. 이때 읽혀졌지만 할당되지 않은 필드는 반환 값에 포함되지 않습니다. 반환 값이 0이면 할당된 필드가 없음을 나타냅니다. 반환 값은 **EOF** 오류에 대 한 첫 번째 변환 하기 전에 문자열의 끝에 도달 하는 경우.

경우 *버퍼* 또는 *형식* 는 **NULL** 에 설명 된 대로 포인터, 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된, 하는 경우 이러한 함수가-1을 반환 하 고 설정 **errno** 를 **EINVAL**

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist, 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**sscanf_s** 함수에서 데이터를 읽는 *버퍼* 위치를 지정 하 여 각에 *인수*합니다. 형식 지정자에 해당 하는 형식이 포함 된 변수에 대 한 포인터를 지정 하는 형식 문자열 뒤에 오는 인수 *형식*합니다. 덜 안전한 버전을 달리 [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md), 버퍼 크기 매개 변수는 형식 필드 문자를 사용할 때 필요한 **c**, **C**, **s**, **S**, 또는 컨트롤 집합에 포함 된 문자열 **[]** 합니다. 문자의 버퍼 크기는 해당 크기를 필요로 하는 각 버퍼 매개 변수 바로 뒤에 추가 매개 변수로 제공해야 합니다. 예를 들어 문자열을 읽고 있는 경우 해당 문자열에 대한 버퍼 크기가 다음과 같이 전달됩니다.

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

버퍼 크기에는 종료 null이 포함되어 있습니다. 너비 사양 필드를 사용하면 읽은 토큰이 버퍼에 맞는지 확인할 수 있습니다. 너비 지정 필드가 사용되지 않으며 읽은 토큰이 너무 커서 버퍼에 맞지 않는 경우 버퍼에는 아무것도 기록되지 않습니다.

문자의 경우 다음과 같이 단일 문자를 읽을 수 있습니다.

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

이 예제에서는 입력 문자열에서 문자 하나를 읽은 다음 와이드 문자 버퍼에 저장합니다. null로 종료되지 않는 문자열의 여러 문자를 읽을 때는 너비 사양 및 버퍼 크기로 부호 없는 정수를 사용합니다.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

자세한 내용은 참조 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 및 [scanf 형식 필드 문자](../../c-runtime-library/scanf-type-field-characters.md)를 참조하세요.

> [!NOTE]
> 크기 매개 변수는 형식 **서명 되지 않은**이 아니라 **size_t**합니다. 를 64 비트 대상에 대해 컴파일할 때 정적 캐스팅을 사용 하 여 변환할 **_countof** 또는 **sizeof** 정확한 크기 결과입니다.

*형식* 인수 컨트롤 입력의 해석은 필드 및 동일한 형태와 기능을 *형식* 에 대 한 인수는 **scanf_s** 함수입니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

**swscanf_s** 의 와이드 문자 버전이 **sscanf_s**;에 대 한 인수 **swscanf_s** 는 와이드 문자 문자열입니다. **sscanf_s** 멀티 바이트 16 진수 문자를 처리 하지 않습니다. **swscanf_s** 유니코드 전자 16 진수 또는 "호환성 영역" 문자를 처리 하지 않습니다. 그렇지 않으면 **swscanf_s** 및 **sscanf_s** 동일 하 게 작동 합니다.

있는 이러한 함수 버전은 **_l** 제외은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하 고 접미사는 동일 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
