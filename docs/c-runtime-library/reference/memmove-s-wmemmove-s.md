---
description: '자세히 알아보기: memmove_s, wmemmove_s'
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: faa68f073949c9c1bcd3d96bb48472484adc312c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171402"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

한 버퍼를 다른 버퍼로 이동합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [memmove, wmemmove](memmove-wmemmove.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*dest*<br/>
대상 개체입니다.

*이면 numberofelements 이벤트가*<br/>
대상 버퍼의 크기입니다.

*src*<br/>
소스 개체입니다.

*count*<br/>
복사할 바이트 수 (**memmove_s**) 또는 문자 수 (**wmemmove_s**)입니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다.

### <a name="error-conditions"></a>오류 조건

|*dest*|*이면 numberofelements 이벤트가*|*src*|반환 값|*대상* 의 내용|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|any|any|**EINVAL**|수정 안 됨|
|any|any|**NULL**|**EINVAL**|수정 안 됨|
|any|< *수*|any|**ERANGE**|수정 안 됨|

## <a name="remarks"></a>설명

Src의 문자 *수* 를 *src* 에서 *dest* 로 복사 합니다. 원본 영역 및 대상의 일부 영역이 겹치면 **memmove_s** 겹쳐쓰기 지역에서 원래 원본 바이트가 복사 되기 전에 복사 되도록 합니다.

*Dest* 또는 *src* 가 null 포인터 이거나 대상 문자열이 너무 작은 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **EINVAL** 를 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**memmove_s**|\<string.h>|
|**wmemmove_s**|\<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>출력

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>참조

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
