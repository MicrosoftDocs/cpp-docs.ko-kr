---
description: '다음에 대 한 자세한 정보: _swab'
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 178189ede5330d467e8ec263a4558bb55108f354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326254"
---
# <a name="_swab"></a>_swab

바이트를 교환합니다.

## <a name="syntax"></a>구문

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>매개 변수

*src*<br/>
복사하고 교환할 데이터입니다.

*dest*<br/>
교환된 데이터에 대한 스토리지 위치입니다.

*n*<br/>
복사되고 교환될 바이트 수입니다.

## <a name="return-value"></a>반환 값

**Swab** 함수는 값을 반환 하지 않습니다. *Src* 또는 *dest* 포인터가 null 이거나 *n* 이 0 보다 작은 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고, [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다.

이 코드 및 기타 반환 코드에 대 한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 를 참조 하세요.

## <a name="remarks"></a>설명

*N* 이 짝수 이면 **_swab** 함수는 *src* 에서 *n* 바이트를 복사 하 고, 인접 한 각 바이트 쌍을 교환 하 고, 결과를 *대상* 에 저장 합니다. *N* 이 홀수 이면 **_swab** 은 *src* 의 첫 번째 *n*-1 바이트를 복사 하 고 교환 하 고 최종 바이트는 복사 되지 않습니다. **_Swab** 함수는 일반적으로 다른 바이트 순서를 사용 하는 컴퓨터에 전송할 이진 데이터를 준비 하는 데 사용 됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> c + +: \<cstdlib> 또는 \<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>참고 항목

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
