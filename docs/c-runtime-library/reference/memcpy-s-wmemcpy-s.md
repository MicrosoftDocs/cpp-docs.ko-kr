---
description: '자세히 알아보기: memcpy_s, wmemcpy_s'
title: memcpy_s, wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 77c71e594d9a3853438987e85e43700d1f467718
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304742"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

버퍼 간에 바이트를 복사합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [memcpy, wmemcpy](memcpy-wmemcpy.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*dest*<br/>
새 버퍼입니다.

*destSize*<br/>
대상 버퍼의 크기로, memcpy_s의 경우 바이트 단위이고 wmemcpy_s의 경우 와이드 문자(wchar_t) 단위입니다.

*src*<br/>
복사할 버퍼입니다.

*count*<br/>
복사할 문자 수입니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다.

### <a name="error-conditions"></a>오류 조건

|*dest*|*destSize*|*src*|*count*|반환 값|*대상* 의 내용|
|------------|----------------|-----------|---|------------------|------------------------|
|any|any|any|0|0|수정 안 됨|
|**NULL**|any|any|0이 아닌 값|**EINVAL**|수정 안 됨|
|any|any|**NULL**|0이 아닌 값|**EINVAL**|*대상* 의 0을 초과 합니다.|
|any|< *수*|any|0이 아닌 값|**ERANGE**|*대상* 의 0을 초과 합니다.|

## <a name="remarks"></a>설명

**memcpy_s** 복사본은 *src* 에서 *dest* 로 바이트 *수를 계산* 합니다. **wmemcpy_s** 복사본은 와이드 문자 (2 바이트)를 *계산* 합니다. 원본과 대상이 겹치면 **memcpy_s** 의 동작이 정의 되지 않습니다. **Memmove_s** 를 사용 하 여 겹치는 영역을 처리할 수 있습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Count* 가 0이 아니고 *dest* 또는 *Src* 가 null 포인터 이거나 *destsize* 가 *Count* 보다 작은 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **EINVAL** 또는 **ERANGE** 을 반환 하 고 **errno** 를 반환 값으로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> 또는 \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>참고 항목

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
