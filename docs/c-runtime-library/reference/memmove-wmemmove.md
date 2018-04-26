---
title: memmove, wmemmove | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
dev_langs:
- C++
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd65c2fc73a20c45338348f05736bb71c1f6b772
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
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
바이트 수입니다 (**memmove**) 또는 문자 (**wmemmove**)에 복사 합니다.

## <a name="return-value"></a>반환 값

값 *dest*합니다.

## <a name="remarks"></a>설명

복사본 *count* 바이트 (**memmove**) 또는 문자 (**wmemmove**)에서 *src* 를 *dest*합니다. 소스 영역과 대상의 일부 영역이 겹치는 경우 두 함수는 모두 겹치는 영역에서 원래 소스 바이트가 덮어쓰기 전에 복사되도록 합니다.

**보안 정보** 대상 버퍼의 크기가 소스 버퍼의 크기보다 크거나 같아야 합니다. 자세한 내용은 [버퍼 오버런 방지](http://msdn.microsoft.com/library/windows/desktop/ms717795)를 참조하세요.

**memmove** 및 **wmemmove** 함수는 경우에 중단 될 상수 **_CRT_SECURE_DEPRECATE_MEMORY** 위해에서 포함 문 이전 정의 사용 되지 않는 경우, 아래 예제 처럼 함수:

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

|루틴|필수 헤더|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

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

## <a name="see-also"></a>참고자료

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
