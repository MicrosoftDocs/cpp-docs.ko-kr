---
description: '자세한 정보: _vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l'
title: _vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l
ms.date: 3/9/2021
api_name:
- _vsprintf_p
- _vswprintf_p
- _vsprintf_p_l
- _vswprintf_p_l
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
- vsprintf_p
- _vswprintf_p
- _vstprintf_p
- vswprintf_p
- _vsprintf_p
- vstprintf_p
helpviewer_keywords:
- vstprintf_p_l function
- _vsprintf_p_l function
- _vstprintf_p function
- vsprintf_p_l function
- _vswprintf_p function
- vswprintf_p function
- vsprintf_p function
- vswprintf_p_l function
- _vswprintf_p_l function
- vstprintf_p function
- formatted text [C++]
- _vsprintf_p function
- _vstprintf_p_l function
ms.openlocfilehash: e67c1d064ed59f8becbfc20ed43a917a3877b058
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621973"
---
# <a name="_vsprintf_p-_vsprintf_p_l-_vswprintf_p-_vswprintf_p_l"></a>_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l

인수가 사용되는 순서를 지정하는 기능과 함께 인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 작성합니다.

## <a name="syntax"></a>구문

```C
int _vsprintf_p(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   va_list argptr
);
int _vsprintf_p_l(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vswprintf_p(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_p_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치입니다.

*sizeInBytes*<br/>
*버퍼* 의 크기 (문자)입니다.

*count*<br/>
이 함수의 유니코드 버전에 저장할 최대 문자 수입니다.

*format*<br/>
형식 사양입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_vsprintf_p** 및 **_vswprintf_p** 는 종료 null 문자를 포함 하지 않고 작성 된 문자 수를 반환 하거나, 출력 오류가 발생 하는 경우 음수 값을 반환 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 인수 목록에 대 한 포인터를 가져온 다음 지정 된 데이터의 형식을 지정 하 고 *버퍼* 에서 가리키는 메모리에 해당 데이터를 씁니다.

이러한 함수는 **vsprintf_s** 와 다르며 위치 매개 변수를 지 원하는 경우에만 **vswprintf_s** . 자세한 내용은 [printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

*Buffer* 또는 *Format* 매개 변수가 **NULL** 포인터인 경우 count가 0 이거나 형식 문자열에 잘못 된 형식 지정 문자가 포함 된 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

> [!IMPORTANT]
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면 [' legacy_stdio_float_rounding .obj '](../link-options.md)를 사용 하 여 연결 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstprintf_p**|**_vsprintf_p**|**_vsprintf_p**|**_vswprintf_p**|
|**_vstprintf_p_l**|**_vsprintf_p_l**|**_vsprintf_p_l**|**_vswprintf_p_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**_vsprintf_p**, **_vsprintf_p_l**|\<stdio.h> 및 \<stdarg.h>|\<varargs.h>*|
|**_vswprintf_p**, **_vswprintf_p_l**|\<stdio.h> 또는 \<wchar.h> , 및 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 호환성을 위해 필요합니다.

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt__vsprintf_p.c
// This program uses vsprintf_p to write to a buffer.
// The size of the buffer is determined by _vscprintf_p.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void example( char * format, ... )
{
    va_list  args;
    int      len;
    char     *buffer = NULL;

    va_start( args, format );

    // _vscprintf doesn't count the
    // null terminating string so we add 1.
    len = _vscprintf_p( format, args ) + 1;

    // Allocate memory for our buffer
    buffer = (char*)malloc( len * sizeof(char) );
    if (buffer)
    {
        _vsprintf_p( buffer, len, format, args );
        puts( buffer );
        free( buffer );
    }
    va_end( args );
}

int main( void )
{
    // First example
    example( "%2$d %1$c %3$d", '<', 123, 456 );

    // Second example
    example( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
