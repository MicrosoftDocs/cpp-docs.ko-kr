---
description: '자세한 정보: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l'
title: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l
ms.date: 11/04/2016
api_name:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
ms.openlocfilehash: 84702c0ab04027f350978c511ee8f871af753bb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292301"
---
# <a name="_sprintf_p-_sprintf_p_l-_swprintf_p-_swprintf_p_l"></a>_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l

형식 문자열에서 매개 변수가 사용되는 순서를 지정하는 기능과 함께 문자열에 형식이 지정된 데이터를 씁니다.

## <a name="syntax"></a>구문

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치

*sizeOfBuffer*<br/>
저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열입니다.

*argument_list*<br/>
서식 문자열에 대 한 선택적 인수입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

기록 된 문자 수 이며, 오류가 발생 한 경우-1입니다.

## <a name="remarks"></a>설명

**_Sprintf_p** 함수는 일련의 문자 및 값의 형식을 지정 하 고 *버퍼* 에 저장 합니다. *Argument_list* 의 각 인수 (있는 경우)는 *형식의* 해당 형식 지정에 따라 변환 되 고 출력 됩니다. *Format* 인수는 [printf 및 wprintf 함수에 대 한 형식 지정 구문을](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)사용 합니다. 기록된 마지막 문자 뒤에 null 문자가 추가됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다. **_Sprintf_p** 와 **sprintf_s** 의 차이점은 **_sprintf_p** 에서 위치 매개 변수를 지원 한다는 것입니다 .이를 통해 형식 문자열에서 인수가 사용 되는 순서를 지정할 수 있습니다. 자세한 내용은 [printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**_swprintf_p** 은 **_sprintf_p** 의 와이드 문자 버전입니다. **_swprintf_p** 에 대 한 포인터 인수는 와이드 문자 문자열입니다. **_Swprintf_p** 의 인코딩 오류 검색은 **_sprintf_p** 와 다를 수 있습니다. **_swprintf_p** 및 **fwprintf_p** 는 동일 하 게 동작 합니다. 단, **_swprintf_p** **파일** 의 대상이 아니라 문자열에 출력을 작성 하 고 **_swprintf_p** 는 *count* 매개 변수를 사용 하 여 쓸 최대 문자 수를 지정 합니다. **_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

**_sprintf_p** 는 종료 null 문자를 제외 하 고 *버퍼* 에 저장 된 바이트 수를 반환 합니다. **_swprintf_p** 는 종료 null 와이드 문자를 제외 하 고 *버퍼* 에 저장 된 와이드 문자 수를 반환 합니다. *버퍼* 또는 *형식이* null 포인터 이거나 형식 문자열에 잘못 된 형식 지정 문자가 포함 된 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_p**|**_sprintf_p**|**_sprintf_p**|**_swprintf_p**|
|**_stprintf_p_l**|**_sprintf_p_l**|**_sprintf_p_l**|**_swprintf_p_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_sprintf_p**, **_sprintf_p_l**|\<stdio.h>|
|**_swprintf_p**, **_swprintf_p_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example-use-_sprintf_p-to-format-data"></a>예: _sprintf_p을 사용 하 여 데이터 서식 지정

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
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
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
