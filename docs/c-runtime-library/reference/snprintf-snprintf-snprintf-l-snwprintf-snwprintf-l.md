---
title: snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l
description: Snprintf, _snprintf, _snprintf_l, _snwprintf 및 _snwprintf_ 에 대 한 API 참조 문자열에 형식이 지정 된 데이터를 씁니다.
ms.date: 3/9/2021
api_name:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
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
- _snprintf
- snprintf_l
- snwprintf_l
- sntprintf
- snprintf
- _sntprintf
- _sntprintf_l
- sntprintf_l
- snwprintf
- _snprintf_l
- _snwprintf
- _snwprintf_l
helpviewer_keywords:
- snwprintf_l function
- sntprintf_l function
- snprintf_l function
- _snwprintf_l function
- _sntprintf_l function
- _snwprintf function
- _snprintf function
- _sntprintf function
- _snprintf_l function
- snwprintf function
- snprintf function
- sntprintf function
- formatted text [C++]
ms.openlocfilehash: c36b7e480b2025c605d46128418c73e7b6887fc3
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621661"
---
# <a name="snprintf-_snprintf-_snprintf_l-_snwprintf-_snwprintf_l"></a>snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l

문자열에 서식이 지정된 데이터를 씁니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치입니다.

*count*<br/>
저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열입니다.

*argument*<br/>
선택적 인수입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)를 참조하세요.

## <a name="return-value"></a>반환 값

**Len** 은 종결 null을 포함 하지 않고 서식이 지정 된 데이터 문자열의 길이입니다. **Len** 및 **count** 는 모두 **snprintf** 와 **_snprintf** 에 대 한 문자 수와 **_snwprintf** 에 대 한 와이드 문자 수입니다.

모든 함수에서 **len**  <  *수가* *버퍼* 에 저장  되는 경우 null 종결자가 추가 되 고 **len** 이 반환 됩니다.

**Snprintf** 함수는에 null 종결자를 배치 하 여 **len** 이 *count* 보다 크거나 같은 경우 출력을 자릅니다 `buffer[count-1]` . 반환 되는 값은 **len**, *개수가* 충분히 클 경우 출력 될 문자 수입니다. **Snprintf** 함수는 인코딩 오류가 발생 하는 경우 음수 값을 반환 합니다.

**Snprintf** 이외의 모든 함수에서, **len**  =  *수가* *버퍼* 에 저장  되는 경우 null 종결자가 추가 되지 않고 **len** 이 반환 됩니다. **Len**  >  *개수*, *count* 문자가 *버퍼* 에 저장 되는 경우 null 종결자가 추가 되지 않고 음수 값이 반환 됩니다.

*Buffer* 가 null 포인터이 고 *개수가* 0 인 경우에는 종료 null을 포함 하지 않고 출력 형식을 지정 하는 데 필요한 문자 수로 **len** 이 반환 됩니다. 동일한 *인수* 및 *로캘* 매개 변수를 사용 하 여 성공적으로 호출 하려면 **len** + 1 자 이상을 보유 하는 버퍼를 할당 합니다.

*Buffer* 가 null 포인터이 고 *개수가* 0이 아닌 경우 또는 *Format* 이 Null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist, 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**Snprintf** 함수와 **_snprintf** 함수 패밀리는 *버퍼* 의 *개수 또는 개수* 를 저장 합니다. **Snprintf** 함수는 항상 종료 null 문자를 저장 하 고, 필요한 경우 출력을 자릅니다. 형식이 지정 된 문자열 길이가 *개수* 문자 보다 엄격 하 게 작은 경우 **_snprintf** 함수 패밀리는 null 종결 문자만 추가 합니다. 각 *인수* (있는 경우)는 변환 되며 *형식의* 해당 형식 지정에 따라 출력 됩니다. 형식은 일반 문자로 구성 되며 [printf](printf-printf-l-wprintf-wprintf-l.md)의 *format* 인수와 동일한 폼 및 함수를 가집니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

> [!IMPORTANT]
> *format* 이 사용자 정의 문자열이 아닌지 확인하세요. **_Snprintf** 함수는 null 종료를 보장 하지 않습니다. 특히 반환 값이 *count* 인 경우에는 null 종결자를 추가 하는 코드가 뒤에와 야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.
>
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면를 사용 하 여 연결 [`legacy_stdio_float_rounding.obj`](../link-options.md) 합니다.

Visual Studio 2015 및 Windows 10의 버전에서 시작 하 여 **snprintf** 는 더 이상 **_snprintf** 와 동일 하지 않습니다. **Snprintf** 함수 동작은 이제 C99 표준 규격을 준수 합니다.

**_snwprintf** 은 **_snprintf** 의 와이드 문자 버전입니다. **_snwprintf** 에 대 한 포인터 인수는 와이드 문자 문자열입니다. **_Snwprintf** 인코딩 오류 검색은 **_snprintf** 와 다를 수 있습니다. **swprintf** 와 마찬가지로 **_Snwprintf** 은 형식 **파일** 의 대상이 아니라 문자열에 출력을 씁니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

C++에서 이러한 함수는 보다 최신의 안전한 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf**|**_snprintf**|**_snprintf**|**_snwprintf**|
|**_sntprintf_l**|**_snprintf_l**|**_snprintf_l**|**_snwprintf_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**snprintf**, **_snprintf**,  **_snprintf_l**|\<stdio.h>|
|**_snwprintf**, **_snwprintf_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_snprintf.c
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

#if !defined(__cplusplus)
typedef int bool;
const bool true = 1;
const bool false = 0;
#endif

#define FAIL 0 // change to 1 and see what happens

int main(void)
{
   char buffer[200];
   const static char s[] = "computer"
#if FAIL
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
#endif
   ;
   const char c = 'l';
   const int i = 35;
#if FAIL
   const double fp = 1e300; // doesn't fit in the buffer
#else
   const double fp = 1.7320534;
#endif
   /* !subtract one to prevent "squeezing out" the terminal null! */
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;
   int bufferUsed = 0;
   int bufferLeft = bufferSize - bufferUsed;
   bool bSuccess = true;
   buffer[0] = 0;

   /* Format and print various data: */

   if (bufferLeft > 0)
   {
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
      bufferLeft, "   String: %s\n", s ); // C4996
      // Note: _snprintf is deprecated; consider _snprintf_s instead
      if (bSuccess = (perElementBufferUsed >= 0))
      {
         bufferUsed += perElementBufferUsed;
         bufferLeft -= perElementBufferUsed;
         if (bufferLeft > 0)
         {
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
            bufferLeft, "   Character: %c\n", c ); // C4996
            if (bSuccess = (perElementBufferUsed >= 0))
            {
               bufferUsed += perElementBufferUsed;
               bufferLeft -= perElementBufferUsed;
               if (bufferLeft > 0)
               {
                  int perElementBufferUsed = _snprintf(&buffer
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996
                  if (bSuccess = (perElementBufferUsed >= 0))
                  {
                     bufferUsed += perElementBufferUsed;
                     bufferLeft -= perElementBufferUsed;
                     if (bufferLeft > 0)
                     {
                        int perElementBufferUsed = _snprintf(&buffer
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996
                        if (bSuccess = (perElementBufferUsed >= 0))
                        {
                           bufferUsed += perElementBufferUsed;
                        }
                     }
                  }
               }
            }
         }
      }
   }

   if (!bSuccess)
   {
      printf("%s\n", "failure");
   }
   else
   {
      /* !store null because _snprintf doesn't necessarily (if the string
       * fits without the terminal null, but not with it)!
       * bufferUsed might be as large as bufferSize, which normally is
       * like going one element beyond a buffer, but in this case
       * subtracted one from bufferSize, so we're ok.
       */
      buffer[bufferUsed] = 0;
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );
   }
   return EXIT_SUCCESS;
}
```

```Output
Output:
   String: computer
   Character: l
   Integer: 35
   Real: 1.732053

character count = 69
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
