---
description: '다음에 대 한 자세한 정보: 함수'
title: to 함수
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: 4e2e8993bfe3ecc85071ab53bcd38c38c9da3370
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326869"
---
# <a name="to-functions"></a>to 함수

각 **to** 함수와 이 함수에 연결된 매크로가 있는 경우에는 단일 문자를 다른 문자로 변환합니다.

[__toascii](../c-runtime-library/reference/toascii-toascii.md)\
[tolower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)\
[toupper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)

## <a name="remarks"></a>설명

**to** 함수 및 매크로 변환은 다음과 같이 수행됩니다.

|루틴에서 반환된 값|매크로|설명|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|`c`를 ASCII 문자로 변환|
|`tolower`|`tolower`|해당하는 경우 `c`를 소문자로 변환|
|`_tolower`|`_tolower`|`c`를 소문자로 변환|
|`towlower`|없음|`c`를 해당하는 와이드 문자 소문자로 변환|
|`toupper`|`toupper`|해당하는 경우 `c`를 대문자로 변환|
|`_toupper`|`_toupper`|`c`를 대문자로 변환|
|`towupper`|없음|c를 해당하는 와이드 문자 대문자로 변환|

역시 매크로로 정의된 **to** 루틴의 함수 버전을 사용하려면 `#undef` 지시문을 사용하여 매크로 정의를 제거하거나 CTYPE.H를 포함하지 마세요. /Za 컴파일러 옵션을 사용하는 경우 컴파일러는 `toupper` 또는 `tolower`의 함수 버전을 사용합니다. `toupper` 및 `tolower` 함수의 선언은 STDLIB.H에 있습니다.

`__toascii` 루틴은 변환된 값이 ASCII 문자 집합의 문자를 나타내도록 `c`의 하위 7비트를 제외한 모든 항목을 0으로 설정합니다. `c`가 이미 ASCII 문자를 나타내는 경우 `c`는 변경되지 않습니다.

`tolower` 및 `toupper` 루틴의 특성은 다음과 같습니다.

- 현재 로캘의 `LC_CTYPE` 범주에 따라 달라집니다. 즉, `tolower`은 `isupper`을 호출하고 `toupper`은 `islower`을 호출합니다.

- `c`가 현재 로캘에서 해당하는 대/소문자의 변환 가능한 문자를 나타내며 해당 로캘에서 반대되는 대/소문자가 있는 경우 `c`를 변환합니다. 그렇지 않은 경우에는 `c`가 변경되지 않습니다.

`_tolower` 및 `_toupper` 루틴의 특성은 다음과 같습니다.

- 로캘과 관련이 없으며 속도가 훨씬 더 빠른 `tolower` 및 **toupper** 버전입니다.

- **Isascii (** `c` **)** 와 **isupper (** `c` **)** 또는 **isascii (** `c` **)** 가 각각 0이 아닌 경우에만 사용할 수 있습니다.

- `c`가 변환하려는 적절한 대/소문자의 ASCII 문자가 아닌 경우 정의되지 않은 결과를 포함합니다.

`towlower` 및 `towupper` 함수는 다음 조건이 둘 다 0이 아닌 경우에만 변환된 `c` 복사본을 반환합니다. 그렇지 않은 경우에는 `c`가 변경되지 않습니다.

- `c`가 적절한 대/소문자의 와이드 문자인 경우(즉, `iswupper` 또는 **iswlower** 이 각각 0이 아닌 경우)

- 대상 대/소문자에 해당하는 와이드 문자가 있는 경우(즉, `iswlower` 또는 **iswupper** 이 각각 0이 아닌 경우)

## <a name="example"></a>예제

```c
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../c-runtime-library/data-conversion.md)<br/>
[로캘](../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../c-runtime-library/is-isw-routines.md)
