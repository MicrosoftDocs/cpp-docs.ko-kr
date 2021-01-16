---
description: '자세히 알아보기: memmove, wmemmove'
title: memmove, wmemmove
ms.date: 1/14/2021
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 6f9942c232710585aa5837510f0f04e5db36fb2a
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243127"
---
# <a name="memmove-wmemmove"></a>`memmove`, `wmemmove`

한 버퍼를 다른 버퍼로 이동합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [ `memmove_s` 을 `wmemmove_s` ](memmove-s-wmemmove-s.md)참조 하십시오.

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

*`dest`*\
대상 개체입니다.

*`src`*\
소스 개체입니다.

*`count`*\
복사할 바이트 ( **`memmove`** ) 또는 문자 수 ( **`wmemmove`** )입니다.

## <a name="return-value"></a>반환 값

의 값 *`dest`* 입니다.

## <a name="remarks"></a>설명

*`count`* 바이트 ( **`memmove`** ) 또는 문자 ( **`wmemmove`** )를에서 *`src`* 로 복사 *`dest`* 합니다. 소스 영역과 대상의 일부 영역이 겹치는 경우 두 함수는 모두 겹치는 영역에서 원래 소스 바이트가 덮어쓰기 전에 복사되도록 합니다.

**보안 정보** 대상 버퍼의 크기가 소스 버퍼의 크기보다 크거나 같아야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

**`memmove`** **`wmemmove`** **`_CRT_SECURE_DEPRECATE_MEMORY`** 아래 예제와 같이 함수가 더 이상 사용 되지 않도록 하기 위해 상수가 포함 문 앞에 정의 된 경우에만 및 함수가 사용 되지 않습니다.

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
|**`memmove`**|`<string.h>`|
|**`wmemmove`**|`<wchar.h>`|

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

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memcpy`, `wmemcpy`](memcpy-wmemcpy.md)\
[`strcpy`, `wcscpy`, `_mbscpy`](strcpy-wcscpy-mbscpy.md)\
[`strncpy`, `_strncpy_l`, `wcsncpy`, `_wcsncpy_l`, `_mbsncpy`, `_mbsncpy_l`](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)\
