---
description: '자세히 알아보기: memmove, wmemmove'
title: memmove, wmemmove
ms.date: 11/04/2016
api_name:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 15dee8eab2a1b7eedd3891d8673647a711c0e499
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171389"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

한 버퍼를 다른 버퍼로 이동합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*dest*<br/>
대상 개체입니다.

*src*<br/>
소스 개체입니다.

*count*<br/>
복사할 바이트 수 (**memmove**) 또는 문자 수 (**wmemmove**)입니다.

## <a name="return-value"></a>반환 값

*Dest* 의 값입니다.

## <a name="remarks"></a>설명

*Src* 에서 *dest* 로 바이트 *수* (**memmove**) 또는 문자 (**wmemmove**)를 복사 합니다. 소스 영역과 대상의 일부 영역이 겹치는 경우 두 함수는 모두 겹치는 영역에서 원래 소스 바이트가 덮어쓰기 전에 복사되도록 합니다.

**보안 정보** 대상 버퍼의 크기가 소스 버퍼의 크기보다 크거나 같아야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

**Memmove** 및 **wmemmove** 함수는 함수를 사용 하지 않기 위해 포함 문 이전에 상수 **_CRT_SECURE_DEPRECATE_MEMORY** 정의 된 경우에만 사용 되지 않습니다. 예를 들면 다음과 같습니다.

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

또는

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>참고 항목

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
