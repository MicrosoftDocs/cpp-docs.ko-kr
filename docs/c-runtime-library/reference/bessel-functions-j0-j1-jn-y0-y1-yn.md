---
description: '자세히 알아보기: Bessel 함수: _j0, _j1, _jn, _y0, _y1, _yn'
title: 'Bessel 함수: _j0, _j1, _jn, _y0, _y1, _yn'
ms.date: 4/2/2020
api_name:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
- _o__j0
- _o__j1
- _o__jn
- _o__y0
- _o__y1
- _o__yn
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 8ada869b615e26d004e10ccc3355e83c9772888f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171870"
---
# <a name="bessel-functions-_j0-_j1-_jn-_y0-_y1-_yn"></a>Bessel 함수: _j0, _j1, _jn, _y0, _y1, _yn

첫 번째 또는 두 번째 종류의 Bessel 함수를 0, 1 또는 n 순서로 계산합니다. Bessel 함수는 일반적으로 전자기파 이론의 수학에 사용됩니다.

## <a name="syntax"></a>구문

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 값입니다.

*n*<br/>
Bessel 함수의 정수 순서입니다.

## <a name="return-value"></a>반환 값

이러한 각 루틴은 *x* 의 Bessel 함수를 반환 합니다. **_Y0**, **_y1** 또는 **_yn** 함수에서 *x* 가 음수 이면 루틴은 **errno** 를 **edom** 으로 설정 하 고, **_DOMAIN** 오류 메시지를 **stderr** 에 출력 하 고, **_HUGE_VAL** 를 반환 합니다. **_Matherr** 를 사용 하 여 오류 처리를 수정할 수 있습니다.

## <a name="remarks"></a>설명

**_J0**, **_j1** 및 **_jn** 루틴은 첫 번째 종류의 Bessel 함수를 각각 0, 1, n 순서로 반환 합니다.

|입력|SEH 예외|Matherr 예외|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|**올바르지 않음**|**_DOMAIN**|

**_Y0**, **_y1** 및 **_yn** 루틴은 두 번째 종류의 Bessel 함수를 각각 0, 1, n 순서로 반환 합니다.

|입력|SEH 예외|Matherr 예외|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|**올바르지 않음**|**_DOMAIN**|
|± 0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0.0|**올바르지 않음**|**_DOMAIN**|

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_j0**, **_j1**, **_jn**, **_y0**, **_y1**, **_yn**|\<cmath> (C + +), \<math.h> (C, C + +)|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>
