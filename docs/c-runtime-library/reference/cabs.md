---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: ba24b10fb267c9b54ec4944704de988128b4b419
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443057"
---
# <a name="_cabs"></a>_cabs

복소수의 절대값을 계산합니다.

## <a name="syntax"></a>구문

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>매개 변수

*-*<br/>
복소수입니다.

## <a name="return-value"></a>Return Value

성공 하면 **_cabs** 는 인수의 절대값을 반환 합니다. 오버플로 시 **_cabs** **HUGE_VAL** 를 반환 하 고 **errno** 를 **ERANGE**로 설정 합니다. [_matherr](matherr.md)을 사용하여 오류 처리를 변경할 수 있습니다.

## <a name="remarks"></a>설명

**_Cabs** 함수는 [_complex](../../c-runtime-library/standard-types.md)형식의 구조 여야 하는 복소수의 절대값을 계산 합니다. 구조체 *z* 는 실제 구성 요소 *x* 및 허수 구성 요소 *y*로 구성 됩니다. **_Cabs** 에 대 한 호출은 식 `sqrt( z.x * z.x + z.y * z.y )`의 값과 동일한 값을 생성 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_cabs**|\<math.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)