---
title: _vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vcwprintf
- _vcprintf_l
- _vcwprintf_l
- _vcprintf
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
- _vcwprintf_l
- _vtcprintf
- vcwprintf
- _vcwprintf
- vcprintf_l
- _vcprintf_l
- _vcprintf
- vcprintf
- vcwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- vcwprintf function
- _vcwprintf_l function
- _vcprintf function
- _vcprintf_l function
- vtcprintf_l function
- vcprintf function
- vcprintf_l function
- _vtcprintf function
- _vcwprintf function
- _vtcprintf_l function
- vcwprintf_l function
- vtcprintf function
- formatted text [C++]
ms.assetid: 4ef8d237-6200-4b66-8731-8c57e5624bb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa7ccf2db8447b51757f5c8a90b2e9a5b6558929
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="vcprintf-vcprintfl-vcwprintf-vcwprintfl"></a>_vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l

인수 목록에 대한 포인터를 사용하여 콘솔에 형식이 지정된 출력을 씁니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)을 참조하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _vcprintf(
   const char* format,
   va_list argptr
);
int _vcprintf_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>매개 변수

*format*<br/>
형식 사양입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

기록된 문자 수 또는 출력 오류가 발생하는 경우 음수 값입니다. 경우 *형식* 가 null 포인터에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EINVAL** 고-1이 반환 됩니다.

## <a name="remarks"></a>설명

이러한 함수는 각각 인수 목록에 대한 포인터를 가져오며 지정된 데이터의 형식을 지정하고 콘솔에 지정된 데이터를 씁니다. **_vcwprintf** 의 와이드 문자 버전이 **_vcprintf**합니다. 이 함수는 인수로 와이드 문자열을 사용합니다.

있는 이러한 함수 버전은 **_l** 은 현재 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 점을 제외 하 고 접미사는 동일 합니다.

> [!IMPORTANT]
> *format*이 사용자 정의 문자열이 아닌지 확인하세요. 자세한 내용은 [버퍼 오버런 방지](http://msdn.microsoft.com/library/windows/desktop/ms717795)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf**|**_vcprintf**|**_vcprintf**|**_vcwprintf**|
|**_vtcprintf_l**|**_vcprintf_l**|**_vcprintf_l**|**_vcwprintf_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**_vcprintf**, **_vcprintf_l**|\<conio.h> 및 \<stdarg.h>|\<varargs.h>*|
|**_vcwprintf**, **_vcwprintf_l**|\<conio.h> 또는 \<wchar.h> 및 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 호환성을 위해 필요합니다.

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
// crt_vcprintf.cpp
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function used to print to the console.
int eprintf(const char* format, ...)
{
    va_list args;
    va_start(args, format);
    int result = _vcprintf(format, args);
    va_end(args);
    return result;
}

int main()
{
    eprintf("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
           "<some error text>");
    eprintf("    (Related to symbol '%s' defined on line %d).\n",
            "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
