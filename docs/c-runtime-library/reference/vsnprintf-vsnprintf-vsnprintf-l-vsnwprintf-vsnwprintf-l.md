---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
description: Vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf 및 _vsnwprintf_l에 대 한 API 참조 인수 목록에 대 한 포인터를 사용 하 여 형식이 지정 된 출력을 작성 합니다.
ms.date: 3/9/2021
api_name:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.openlocfilehash: 870afc9cae241e61daebcac06089d01ac2fc3675
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621999"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치입니다.

*count*<br/>
작성할 최대 문자 수입니다.

*format*<br/>
형식 사양입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

**Vsnprintf** 함수는 null 종결 문자를 제외 하 고 작성 된 문자 수를 반환 합니다. *Count* 로 지정 된 버퍼 크기가 *format* 및 *argptr* 로 지정 된 출력을 포함 하는 데 충분히 크지 않은 경우 **vsnprintf** 의 반환 값은 null 문자를 제외 하 고 작성 되는 문자 수입니다 ( *개수가* 충분히 큰 경우). 반환 값이 *개수* -1 보다 큰 경우 출력이 잘렸습니다. 반환 값 -1은 인코딩 오류가 발생했음을 나타냅니다.

**_Vsnprintf** 및 **_vsnwprintf** 함수는 쓸 문자 수가 *count* 보다 작거나 같은 경우 쓴 문자 수를 반환 합니다. 작성할 문자 수가 *count* 보다 큰 경우 이러한 함수는 출력이 잘린 것을 나타내는-1을 반환 합니다.

이러한 모든 함수에서 반환 되는 값에는 쓰기가 기록 되었는지 여부에 관계 없이 종료 null이 포함 되지 않습니다.

- *Count* 가 0이 고 *buffer* 가 **NULL** 이면 함수가 쓸 수 있는 문자 수가 반환 됩니다. 이 값은 종료 **NULL** 을 고려 하지 않습니다. 이 결과를 사용하여 문자열과 해당 종결 null에 대해 충분한 버퍼 공간을 할당한 다음 함수를 다시 호출하여 버퍼를 채울 수 있습니다.
- *Count* 가 0 이지만 *버퍼가* **NULL** 이 아닌 경우 아무 것도 쓰여지지 않으며 함수는를 반환 `-1` 합니다.
- *Format* 이 **null** 이거나 *buffer* 가 **null** 이 고 *Count* 가 0이 아닌 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 인수 목록에 대 한 포인터를 가져온 다음 데이터의 형식을 지정 하 고 *버퍼* 에 의해 가리키는 메모리에 문자 *수를 계산* 합니다. **Vsnprintf** 함수는 출력을 자르는 경우에도 항상 null 종결자를 씁니다. **_Vsnprintf** 및 **_vsnwprintf** 를 사용 하는 경우 버퍼는 끝에 공간이 있는 경우에만 null로 종료 됩니다. 즉, 쓰려는 문자 수가 *count* 보다 작은 경우에만 null이 종료 됩니다.

> [!IMPORTANT]
> 특정 종류의 보안 위험을 방지 하려면 *형식이* 사용자 정의 문자열이 아닌지 확인 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면 [' legacy_stdio_float_rounding .obj '](../link-options.md)를 사용 하 여 연결 하세요.

> [!NOTE]
> **_Vsnprintf**, **_vsnprintf_l** **_vsnwprintf** 및 **_vsnwprintf_l** 를 호출할 때 종료 null에 대 한 공간이 있는지 확인 하려면 *count* 가 버퍼 길이 보다 엄격 하 게 작아야 하며 함수를 호출 하기 전에 버퍼를 null로 초기화 해야 합니다.
>
> **Vsnprintf** 는 항상 종료 null을 작성 하므로 *count* 매개 변수는 버퍼의 크기와 같을 수 있습니다.

Visual Studio 2015 및 Windows 10의 일부 터 RT부터 **vsnprintf** 는 더 이상 **_vsnprintf** 와 동일 하지 않습니다. **Vsnprintf** 함수는 C99 표준을 준수 합니다. 이전 Visual Studio code와의 호환성을 위해 **_vnsprintf** 유지 됩니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**, **_vsnprintf**, **_vsnprintf_l**|\<stdio.h>|\<stdio.h> 또는 \<cstdio>|
|**_vsnwprintf**, **_vsnwprintf_l**|\<stdio.h> 또는 \<wchar.h>|\<stdio.h>, \<wchar.h>, \<cstdio> 또는 \<cwchar>|

**_Vsnprintf**, **_vsnprintf_l**, **_Vsnwprintf** 및 **_vsnwprintf_l** 함수는 Microsoft 전용입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example-use-wide-characters-with-_vsnwprintf"></a>예:에서 와이드 문자 사용 `_vsnwprintf()`

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

좁은 문자열 매개 변수와 함께 vsnprintf를 대신 사용하면 동작이 변경됩니다. *Count* 매개 변수는 버퍼의 전체 크기가 될 수 있으며, 반환 값은 *개수가* 충분히 큰 경우에 기록 되는 문자 수입니다.

## <a name="example-use-vsnprintf-with-narrow-strings"></a>예: `vsnprintf()` 좁은 문자열과 함께 사용

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
