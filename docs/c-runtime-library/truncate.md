---
description: '다음에 대 한 자세한 정보: _TRUNCATE'
title: _TRUNCATE
ms.date: 11/04/2016
f1_keywords:
- _TRUNCATE
- TRUNCATE
helpviewer_keywords:
- TRUNCATE constant
- _TRUNCATE constant
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
ms.openlocfilehash: ea8a1517db8b270e03c5767838f3965cdea8b36f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162367"
---
# <a name="_truncate"></a>_TRUNCATE

문자열 잘라내기 동작을 지정합니다.

## <a name="syntax"></a>구문

```
#include <stdlib.h>
```

## <a name="remarks"></a>설명

`_TRUNCATE`는 다음 함수에 `count` 매개 변수로 전달될 때 잘라내기 동작을 가능하게 만듭니다.

[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

[mbsrtowcs_s](../c-runtime-library/reference/mbsrtowcs-s.md)

[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[wcsrtombs_s](../c-runtime-library/reference/wcsrtombs-s.md)

[_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

대상 버퍼가 너무 작아서 전체 문자열을 포함할 수 없으면 이를 오류 상황으로 처리하는 것이 이러한 함수의 일반적인 동작입니다([매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md) 참조). 그러나 `_TRUNCATE`를 전달하여 문자열 잘라내기가 가능할 경우 이러한 함수는 대상 버퍼가 null로 종료된 상태로 둔 채 맞는 만큼의 문자열 부분만 복사하고 반환됩니다.

문자열 잘라내기는 영향을 받는 함수의 반환 값을 변경합니다. 다음 함수는 잘라내기가 발생하지 않으면 0을 반환하고, 잘라내기가 발생하면 `STRUNCATE`를 반환합니다.

[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

다음 함수는 잘라내기가 발생하지 않으면 복사된 문자 수를 반환하고, 잘라내기가 발생하면 -1을 반환합니다(원래 snprintf 함수의 동작과 일치).

[_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

## <a name="example"></a>예제

```c
// crt_truncate.c
#include <stdlib.h>
#include <errno.h>

int main()
{
   char src[] = "1234567890";
   char dst[5];
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);
   if ( err == STRUNCATE )
      printf( "truncation occurred!\n" );
   printf( "'%s'\n", dst );
}
```

```Output
truncation occurred!
'1234'
```

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
