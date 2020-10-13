---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 06/23/2020
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: da3c5b3660b481fd3a7140adbc236f44cd51f37e
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008824"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

문자열에 서식이 지정된 데이터를 씁니다. 이러한 함수 중 일부의 더 안전한 버전을 사용할 수 있습니다. [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)을 참조하세요. **Swprintf** 및 **_swprintf_l** 의 안전한 버전은 버퍼의 크기를 매개 변수로 사용 합니다.

## <a name="syntax"></a>구문

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치

*count*<br/>
이 함수의 유니코드 버전에 저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열

*argument*<br/>
선택적 인수

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

기록 된 문자 수 이며, 오류가 발생 한 경우-1입니다. *버퍼* 또는 *형식이* Null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

**sprintf** 는 null 종결 문자를 제외 하 고 *버퍼*에 저장 된 바이트 수를 반환 합니다. **swprintf** 는 종료 null 와이드 문자를 제외 하 고 *버퍼*에 저장 된 와이드 문자 수를 반환 합니다.

## <a name="remarks"></a>설명

**Sprintf** 함수는 일련의 문자 및 값의 형식을 지정 하 고 *버퍼*에 저장 합니다. 각 *인수* (있는 경우)는 *형식*의 해당 형식 사양에 따라 변환 되 고 출력 됩니다. 형식은 일반 문자로 구성 되며 [printf](printf-printf-l-wprintf-wprintf-l.md)의 *format* 인수와 동일한 폼 및 함수를 가집니다. 기록된 마지막 문자 뒤에 null 문자가 추가됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

> [!IMPORTANT]
> **Sprintf**를 사용 하는 경우 기록 되는 문자 수를 제한할 방법이 없습니다. 즉, **sprintf** 를 사용 하는 코드는 버퍼 오버런에 취약 합니다. *버퍼*에 쓸 최대 문자 수를 지정 하는 [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)관련 함수를 사용 하거나 [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) 를 사용 하 여 필요한 버퍼 크기를 결정 하십시오. 또한 *형식이* 사용자 정의 문자열이 아닌지 확인 합니다.

**swprintf** 는 **sprintf**의 와이드 문자 버전입니다. **swprintf** 에 대 한 포인터 인수는 와이드 문자 문자열입니다. **Swprintf** 의 인코딩 오류 검색은 **sprintf**와 다를 수 있습니다. **swprintf** 및 **Fwprintf** 는 형식이 **FILE**의 대상이 아니라 문자열에 출력을 쓰는 것 **을 제외 하 고 동일** 하 게 동작 하며 **swprintf** 는 *count* 매개 변수를 사용 하 여 기록할 최대 문자 수를 지정 해야 합니다. **_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 경우를 제외 하 고는 동일 합니다.

**swprintf** 는 **size_t**형식의 두 번째 매개 변수 *개수*를 필요로 하는 ISO C 표준을 준수 합니다. 이전의 비표준 동작을 강제 적용 하려면 **_CRT_NON_CONFORMING_SWPRINTFS**를 정의 합니다. 이후 버전에서 기존 동작이 제거될 수도 있으므로 새 준수 동작을 사용하도록 코드를 변경해야 합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example-use-sprintf-to-format-data"></a>예: sprintf를 사용 하 여 데이터 서식 지정

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
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
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
