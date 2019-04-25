---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: 22dd01a0b2558c83ca1e25875a2ace7dd4ee15c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176189"
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

현재 로캘 또는 전달된 지정한 로캘을 사용하여 문자열의 다음 토큰을 찾습니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)을 참조하세요.

> [!IMPORTANT]
> **_mbstok** 하 고 **_mbstok_l** Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*strToken*<br/>
토큰을 하나 이상 포함하는 문자열입니다.

*strDelimit*<br/>
구분 기호 문자 집합입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

다음 토큰에 대 한 포인터를 반환 *strToken*합니다. 이 함수는 반환 **NULL** 더 이상 토큰이 검색 되 면 합니다. 각 호출을 수정 *strToken* 반환된 된 토큰 뒤에 오는 첫 번째 구분 기호에 대 한 null 문자를 대체 하 여 합니다.

## <a name="remarks"></a>설명

합니다 **strtok** 함수에서 다음 토큰을 찾습니다 *strToken*합니다. 문자 집합이 *strDelimit* 에서 찾을 토큰의 사용 가능한 구분 기호를 지정 *strToken* 현재 호출 합니다. **wcstok** 하 고 **_mbstok** 와이드 문자 및 멀티 바이트 문자 버전입니다 **strtok**합니다. 인수 및 반환 값 **wcstok** 은 와이드 문자열이 고 **_mbstok** 는 멀티 바이트 문자 문자열입니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

> [!IMPORTANT]
> 이러한 함수는 버퍼 오버런 문제로 인해 발생하는 잠재적인 위협을 일으킵니다. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/desktop/SecBP/avoiding-buffer-overruns)를 참조하세요.

첫 번째 호출에서 **strtok**, 함수는 선행 구분 기호를 건너뛰고 및 첫 번째 토큰에 대 한 포인터를 반환 합니다. *strToken*, null 문자로 토큰을 종료 합니다. 더 많은 토큰의 나머지 부분으로 분할할 수 있습니다 *strToken* 일련의 호출에 의해 **strtok**합니다. 호출할 때마다 **strtok** 수정 *strToken* 뒤에 null 문자를 삽입 하 여 합니다 **토큰** 해당 호출에서 반환 합니다. 다음 토큰을 읽어올 *strToken*, 호출 **strtok** 사용 하 여는 **NULL** 에 대 한 값을 *strToken* 인수. 합니다 **NULL** *strToken* 인수를 사용 하면 **strtok** 에서 수정 된 다음 토큰을 검색할 *strToken*합니다. 합니다 *strDelimit* 인수 구분 기호 집합이 달라질 수 있도록 다음에 대 한 호출에서 값을 사용할 수 있습니다.

출력 값의 설정이 적용 됩니다는 **LC_CTYPE** 로캘 범주 설정 합니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요.

없는 이러한 함수의 버전은 **_l** 접미사가 로캘 종속 동작에 대 한 현재 로캘을 사용 합니다. 사용 하 여 버전 합니다 **_l** 접미사 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하면 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

> [!NOTE]
> 각 함수는 스레드 로컬 정적 변수를 사용하여 문자열을 토큰으로 구문 분석합니다. 따라서 여러 스레드가 부적절한 영향을 주지 않고 이러한 함수를 동시에 호출할 수 있습니다. 그러나 단일 스레드 내에서 이러한 함수 중 하나로 호출을 인터리빙하면 데이터가 손상되고 부정확한 결과가 생성될 가능성이 높습니다. 다른 문자열을 구문 분석할 때는 문자열 하나의 구문 분석을 완료한 후에 다음 문자열의 구문 분석을 시작하세요. 또한 다른 함수가 호출되는 루프 내에서 이러한 함수 중 하나를 호출할 때의 위험 가능성도 고려하세요. 다른 함수가 이러한 함수 중 하나를 사용하게 되면 인터리빙된 호출 시퀀스가 수행되어 데이터가 손상됩니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> 또는 \<wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>참고자료

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
