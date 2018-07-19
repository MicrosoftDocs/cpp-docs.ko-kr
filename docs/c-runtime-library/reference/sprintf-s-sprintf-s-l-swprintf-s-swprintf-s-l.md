---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs:
- C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0200740df3b41e356bcf83f0756b8a5267b38166
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417793"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

문자열에 서식이 지정된 데이터를 씁니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>매개 변수

*buffer*<br/>
출력을 위한 저장소 위치

*sizeOfBuffer*<br/>
저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열

*...*<br/>
서식을 지정할 선택적 인수

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

작성 된 문자 수 또는 오류가 발생 한 경우-1입니다. 경우 *버퍼* 또는 *형식* null 포인터가 **sprintf_s** 및 **swprintf_s** -1을 반환 하 고 설정할 **errno**를 **EINVAL**합니다.

**sprintf_s** 에 저장 된 바이트 수를 반환 *버퍼*, 종결 null 문자를 제외 합니다. **swprintf_s** 에 저장 된 와이드 문자 수를 반환 *버퍼*, 종료 null 와이드 문자를 제외 합니다.

## <a name="remarks"></a>설명

**sprintf_s** 포맷 하 고 일련의 문자 및 값을 저장 하는 함수 *버퍼*합니다. 각 *인수* (있는 경우)이 변환 되 고 해당 형식 사양에 따라 출력 *형식*합니다. 형식은 일반 문자로 구성 되어 있으며 동일한 형태와 기능을는 *형식* 에 대 한 인수 [printf](printf-printf-l-wprintf-wprintf-l.md)합니다. 기록된 마지막 문자 뒤에 null 문자가 추가됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

주요 차이점 **sprintf_s** 및 [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 은 **sprintf_s** 유효한 서식 문자에 대 한 형식 문자열 검사 하는 반면 [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 인지 여부만 검사 서식 문자열 또는 버퍼가 **NULL** 포인터입니다. 검사에 실패할 경우 [Parameter Validation](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 함수는-1 반환 하 고 집합을 계속 하려면 실행 허용 된 경우 **errno** 를 **EINVAL**합니다.

다른 주요 차이점 **sprintf_s** 및 [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 은 **sprintf_s** 문자 출력 버퍼의 크기를 지정 하는 길이 매개 변수를 사용 합니다. 종료 null을 포함 하 여 서식 있는 텍스트에 대 한 버퍼가 너무 작습니다. 경우에 null 문자를 배치 하 여 버퍼를 빈 문자열로 설정 되어 *버퍼*[0], 잘못 된 매개 변수 처리기가 호출 됩니다. 와 달리 **_snprintf**, **sprintf_s** 있는지 버퍼가 null로 종료 됩니다 버퍼 크기가 0이 아닌 한 보장 합니다.

**swprintf_s** 의 와이드 문자 버전이 **sprintf_s**;에 대 한 포인터 인수 **swprintf_s** 는 와이드 문자 문자열입니다. 인코딩 오류를 탐지 **swprintf_s** 에 다를 수 있습니다 **sprintf_s**합니다. 있는 이러한 함수 버전은 **_l** 은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 점을 제외 하 고 접미사는 동일 합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있어 크기 인수를 지정할 필요가 없으며, 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.

버전은 **sprintf_s** 버퍼가 너무 작습니다. 경우에 대 한 추가 제어를 제공 하는 합니다. 자세한 내용은 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio> 또는 \<stdio.h>|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio.h> 또는 \<wchar.h><br /><br /> C++: \<cstdio>, \<cwchar>, \<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>예제

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
