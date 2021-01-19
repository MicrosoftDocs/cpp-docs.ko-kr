---
title: memset, wmemset
description: Memset, wmemset에 대해 자세히 알아보세요.
ms.date: 1/15/2021
api_name:
- wmemset
- memset
- _o_memset
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memset
- wmemset
helpviewer_keywords:
- wmemset function
- memset function
ms.openlocfilehash: 1ee5b3cb3653a3d5486eecb0f3b033e69d9db9fa
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563967"
---
# <a name="memset-wmemset"></a>`memset`, `wmemset`

버퍼를 지정된 문자로 설정합니다.

## <a name="syntax"></a>구문

```C
void *memset(
   void *dest,
   int c,
   size_t count
);
wchar_t *wmemset(
   wchar_t *dest,
   wchar_t c,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*`dest`*\
대상에 대한 포인터입니다.

*`c`*\
설정할 문자입니다.

*`count`*\
문자 수입니다.

## <a name="return-value"></a>반환 값

의 값 *`dest`* 입니다.

## <a name="remarks"></a>설명

의 첫 번째 *`count`* 문자 *`dest`* 를 문자로 설정 합니다 *`c`* .

**보안 정보** 대상 버퍼의 공간이 충분 한지 확인 *`count`* 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`memset`**|`<memory.h>` 또는 `<string.h>`|
|**`wmemset`**|`<wchar.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_memset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <memory.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is a test of the memset function";

   printf( "Before: %s\n", buffer );
   memset( buffer, '*', 4 );
   printf( "After:  %s\n", buffer );
}
```

### <a name="output"></a>출력

```Output
Before: This is a test of the memset function
After:  **** is a test of the memset function
```

다음은 wmemset 사용에 대한 예제입니다.

```C
// crt_wmemset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <wchar.h>
#include <stdio.h>

int main( void )
{
   wchar_t buffer[] = L"This is a test of the wmemset function";

   wprintf( L"Before: %s\n", buffer );
   wmemset( buffer, '*', 4 );
   wprintf( L"After:  %s\n", buffer );
}
```

### <a name="output"></a>출력

```Output
Before: This is a test of the wmemset function
After:  **** is a test of the wmemset function
```

## <a name="see-also"></a>참조

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memchr`, `wmemchr`](memchr-wmemchr.md)\
[`memcmp`, `wmemcmp`](memcmp-wmemcmp.md)\
[`memcpy`, wmemcpy](memcpy-wmemcpy.md)\
[`_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l`](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)