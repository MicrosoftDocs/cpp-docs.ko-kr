---
title: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9a97dc0d1e52cb23e26eeb46e86c684b6bee9d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="sprintfp-sprintfpl-swprintfp-swprintfpl"></a>_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l

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

*buffer*<br/>
출력을 위한 저장소 위치

*sizeOfBuffer*<br/>
저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열입니다.

*argument_list*<br/>
서식 문자열에 선택적 인수입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

작성 된 문자 수 또는 오류가 발생 한 경우-1입니다.

## <a name="remarks"></a>설명

**_sprintf_p** 포맷 하 고 일련의 문자 및 값을 저장 하는 함수 *버퍼*합니다. 각 인수에는 *argument_list* (있는 경우)이 변환 되 고 해당 형식 사양에 따라 출력 *형식*합니다. *형식* 인수를 사용 하는 [형식 사양 구문 printf 및 wprintf 함수에 대 한](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)합니다. A **NULL** 문자가 작성 된 마지막 문자 뒤에 추가 됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다. 차이 **_sprintf_p** 및 **sprintf_s** 은 **_sprintf_p** 지원 위치 매개 변수를 인수는 순서를 지정할 수 있습니다 형식 문자열에 사용 합니다. 자세한 내용은 [printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**_swprintf_p** 의 와이드 문자 버전이 **_sprintf_p**;에 대 한 포인터 인수 **_swprintf_p** 는 와이드 문자 문자열입니다. 인코딩 오류를 탐지 **_swprintf_p** 에 다를 수 있습니다 **_sprintf_p**합니다. **_swprintf_p** 및 **fwprintf_p** 점을 제외 하 고 동일 하 게 작동 **_swprintf_p** 유형의 대상 대신 문자열에 출력을 기록 **파일**, 및 **_swprintf_p** 필요는 *count* 매개 변수를 쓸 문자의 최대 수를 지정 합니다. 있는 이러한 함수 버전은 **_l** 은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 점을 제외 하 고 접미사는 동일 합니다.

**_sprintf_p** 에 저장 된 바이트 수를 반환 *버퍼*를 제외 하 고 종료 **NULL** 문자입니다. **_swprintf_p** 에 저장 된 와이드 문자 수를 반환 *버퍼*를 제외 하 고 종료 **NULL** 와이드 문자입니다. 경우 *버퍼* 또는 *형식* 가 null 포인터 또는에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 형식 문자열에 잘못 된 서식 문자가 들어 [매개 변수 유효성 검사 ](../../c-runtime-library/parameter-validation.md). 실행을 계속 허용 된, 하는 경우 이러한 함수가-1을 반환 하 고 설정 **errno** 를 **EINVAL**합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_p**|**_sprintf_p**|**_sprintf_p**|**_swprintf_p**|
|**_stprintf_p_l**|**_sprintf_p_l**|**_sprintf_p_l**|**_swprintf_p_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_sprintf_p**, **_sprintf_p_l**|\<stdio.h>|
|**_swprintf_p**, **_swprintf_p_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

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

## <a name="example"></a>예제

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

## <a name="see-also"></a>참고자료

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
