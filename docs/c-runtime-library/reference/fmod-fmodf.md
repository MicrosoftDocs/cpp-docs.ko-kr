---
title: fmod, fmodf, fmodl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fmod
- fmodf
- fmodl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fmod
- _fmodl
- fmodf
dev_langs:
- C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c31ec67e3b5c75c334a985461365c7b139758427
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

부동 소수점 나머지를 계산합니다.

## <a name="syntax"></a>구문

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>매개 변수

*x*, *y*<br/>
부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**fmod** 의 부동 소수점 나머지를 반환 *x* / *y*합니다. 하는 경우의 값 *y* 이 0.0 인 경우 **fmod** 자동 NaN을 반환 합니다. 자동 NaN에서의 표현에 대 한 내용은 **printf** 제품군, 참조 [printf](printf-printf-l-wprintf-wprintf-l.md)합니다.

## <a name="remarks"></a>설명

**fmod** 함수는 부동 소수점 나머지 계산 *f* 의 *x* / *y* 되도록 *x*  =  *i* * *y* + *f*여기서 *i* 정수 이면 *f* 와 동일한 기호가 *x*, 및의 절대값 *f* 의 절대 값 보다 작으면 *y*합니다.

C + + 오버 로드의 오버 로드를 호출할 수 있도록 허용 **fmod** 사용 하 고 반환 **float** 및 **긴** **double** 값입니다. C 프로그램에서 **fmod** 항상는 두 가지 **double** 인수 및 반환 된 **double**합니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<math.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>참고자료

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
