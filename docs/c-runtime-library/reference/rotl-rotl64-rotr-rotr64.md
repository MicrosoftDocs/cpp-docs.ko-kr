---
title: _rotl, _rotl64, _rotr, _rotr64 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _rotr64
- _rotl
- _rotr
- _rotl64
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
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _rotr64
- rotl64
- _rotl64
- rotr64
- rotr
- _rotr
- _rotl
- rotl
dev_langs:
- C++
helpviewer_keywords:
- rotl64 function
- _rotl function
- rotr function
- rotr64 function
- _rotr function
- rotl function
- _rotl64 function
- rotating bits
- _rotr64 function
- bits, rotating
ms.assetid: cfce439b-366f-4584-8ab1-d527b13fcfc6
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9633e22dbfe62673194cb2aa9148c0938cc0a9a5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="rotl-rotl64-rotr-rotr64"></a>_rotl, _rotl64, _rotr, _rotr64

비트를 왼쪽으로 회전 (**_rotl**) 또는 오른쪽 (**_rotr**).

## <a name="syntax"></a>구문

```C

unsigned int _rotl(
   unsigned int value,
   int shift
);
unsigned __int64 _rotl64(
   unsigned __int64 value,
   int shift
);
unsigned int _rotr(
   unsigned int value,
   int shift
);
unsigned __int64 _rotr64(
   unsigned __int64 value,
   int shift
);
```

### <a name="parameters"></a>매개 변수

*값*<br/>
순환할 값입니다.

*shift*<br/>
이동할 비트 수입니다.

## <a name="return-value"></a>반환 값

순환된 값입니다. 반환되는 오류가 없습니다.

## <a name="remarks"></a>설명

**_rotl** 및 **_rotr** 함수는 부호 없는 회전 *값* 여 *shift* 비트입니다. **_rotl** 값을 왼쪽으로 회전 합니다. **_rotr** 은 값을 오른쪽으로 회전 합니다. 두 함수 모두 순환되어 *value*의 한쪽 끝에서 잘린 비트 부분을 다른 쪽 끝에 추가합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_rotl**, **_rotl64**|\<stdlib.h>|
|**_rotr**, **_rotr64**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_rot.c
/* This program shifts values to rotate an integer.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned val = 0x0fd93;
   __int64 val2 = 0x0101010101010101;

   printf( "0x%4.4x rotated left three times is 0x%4.4x\n",
           val, _rotl( val, 3 ) );
   printf( "0x%4.4x rotated right four times is 0x%4.4x\n",
           val, _rotr( val, 4 ) );

   printf( "%I64x rotated left three times is %I64x\n",
           val2, _rotl64( val2, 3 ) );
   printf( "%I64x rotated right four times is %I64x\n",
           val2, _rotr64( val2, 4 ) );
}
```

### <a name="output"></a>출력

```Output
0xfd93 rotated left three times is 0x7ec98
0xfd93 rotated right four times is 0x30000fd9
101010101010101 rotated left three times is 808080808080808
101010101010101 rotated right four times is 1010101010101010
```

## <a name="see-also"></a>참고자료

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_lrotl, _lrotr](lrotl-lrotr.md)<br/>
