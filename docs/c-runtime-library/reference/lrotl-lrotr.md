---
title: _lrotl, _lrotr
description: '_Lrotl 및 _lrotr에 대 한 API 참조 비트를 왼쪽 (_lrotl) 또는 오른쪽 (_lrotr)으로 회전 하는입니다. '
ms.date: 04/04/2018
api_name:
- _lrotl
- _lrotr
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: ccd14f7aa6ba3c1278063593aecee20c6789110d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555009"
---
# <a name="_lrotl-_lrotr"></a>_lrotl, _lrotr

비트를 왼쪽 (**_lrotl**) 또는 오른쪽 (**_lrotr**)으로 회전 합니다.

## <a name="syntax"></a>구문

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>매개 변수

*value*<br/>
순환할 값입니다.

*shift*<br/>
*value*를 이동할 비트 수입니다.

## <a name="return-value"></a>반환 값

두 함수 모두 순환된 값을 반환합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**_Lrotl** 및 **_lrotr** 함수는 *값* 을 *shift* 비트로 회전 합니다. **_lrotl** 는 더 중요 한 비트 쪽으로 값을 왼쪽으로 회전 합니다. **_lrotr** 값을 유효 하지 않은 비트 단위로 오른쪽으로 회전 합니다. 두 함수 모두 순환되어 *value*의 한쪽 끝에서 잘린 비트 부분을 다른 쪽 끝에 추가합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_lrotl**, **_lrotr**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl, _rotl64, _rotr, _rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
