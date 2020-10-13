---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
api_name:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
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
ms.openlocfilehash: 006b0f84494466b5c23a8c86f586774b66839b03
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008831"
---
# <a name="sprintf_s-_sprintf_s_l-swprintf_s-_swprintf_s_l"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

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

*버퍼*<br/>
출력을 위한 스토리지 위치

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

기록 된 문자 수 이며, 오류가 발생 한 경우-1입니다. *버퍼* 또는 *형식이* null 포인터인 경우 **sprintf_s** 및 **swprintf_s** -1을 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

**sprintf_s** 는 종료 null 문자를 제외 하 고 *버퍼*에 저장 된 바이트 수를 반환 합니다. **swprintf_s** 는 종료 null 와이드 문자를 제외 하 고 *버퍼*에 저장 된 와이드 문자 수를 반환 합니다.

## <a name="remarks"></a>설명

**Sprintf_s** 함수는 일련의 문자 및 값의 형식을 지정 하 고 *버퍼*에 저장 합니다. 각 *인수* (있는 경우)는 *형식*의 해당 형식 사양에 따라 변환 되 고 출력 됩니다. 형식은 일반 문자로 구성 되며 [printf](printf-printf-l-wprintf-wprintf-l.md)의 *format* 인수와 동일한 폼 및 함수를 가집니다. 기록된 마지막 문자 뒤에 null 문자가 추가됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

**Sprintf_s** 와 [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 의 한 가지 주요 차이점은 **sprintf_s** 는 서식 문자열에서 유효한 형식 지정 문자를 확인 하는 것이 고, [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 는 형식 문자열 또는 버퍼가 **NULL** 포인터 인지 여부만 확인 한다는 것입니다. 검사에 실패할 경우 [Parameter Validation](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

**Sprintf_s** 와 [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 의 다른 주요 차이점은 **sprintf_s** 는 출력 버퍼의 크기를 문자 단위로 지정 하는 길이 매개 변수를 사용 한다는 것입니다. 종료 null을 포함 하 여 서식이 지정 된 텍스트에 대해 버퍼가 너무 작은 경우 버퍼 [0]에 null 문자를 배치 하 *여 버퍼를*빈 문자열로 설정 하면 잘못 된 매개 변수 처리기가 호출 됩니다. **_Snprintf**와 달리 **sprintf_s** 는 버퍼 크기가 0이 아닌 한 버퍼를 null로 종료 하도록 보장 합니다.

**swprintf_s** 은 **sprintf_s**의 와이드 문자 버전입니다. **swprintf_s** 에 대 한 포인터 인수는 와이드 문자 문자열입니다. **Swprintf_s** 의 인코딩 오류 검색은 **sprintf_s**와 다를 수 있습니다. **_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있어 크기 인수를 지정할 필요가 없으며, 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

버퍼가 너무 작은 경우 발생 하는 상황에 대 한 추가 제어를 제공 하는 **sprintf_s** 버전이 있습니다. 자세한 내용은 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C \<stdio.h><br /><br /> C + +: \<cstdio> 또는 \<stdio.h>|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio.h> 또는 \<wchar.h><br /><br /> C + +: \<cstdio> , \<cwchar> \<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example-use-sprintf_s-to-format-data"></a>예: sprintf_s을 사용 하 여 데이터 서식 지정

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

## <a name="example-error-code-handling"></a>예: 오류 코드 처리

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

## <a name="see-also"></a>참조

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
