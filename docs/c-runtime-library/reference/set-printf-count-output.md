---
description: '다음에 대 한 자세한 정보: _set_printf_count_output'
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 455c4f0e49ce111853145a05d78efabcd76386fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114249"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

[Printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)family 함수에서 **% n** 형식의 지원을 사용 하거나 사용 하지 않도록 설정 합니다.

## <a name="syntax"></a>구문

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>매개 변수

*enable*<br/>
0이 아닌 값은 **% n** 지원을 사용 하도록 설정 하 고 0은 **% n** 지원을 사용 하지 않도록 설정 합니다.

## <a name="property-valuereturn-value"></a>속성 값/반환 값

이 함수를 호출 하기 전에 **% n** 지원의 상태입니다. **% n** 지원이 사용 하도록 설정 된 경우 0이 아닌 값이 고, 사용 하지 않도록 설정 된 경우 0입니다.

## <a name="remarks"></a>설명

보안상의 이유로 **printf** 와 모든 변형에서 **% n** 서식 지정자에 대 한 지원은 기본적으로 사용 되지 않습니다. **Printf** 형식 사양에 **% n** 이 있으면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 하는 것이 기본 동작입니다. 0이 아닌 인수를 사용 하 여 **_set_printf_count_output** 를 호출 하면 [형식 사양 구문: Printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)에 설명 된 대로 **printf** 제품군 함수가 **% n** 을 해석 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>참고 항목

[_get_printf_count_output](get-printf-count-output.md)<br/>
