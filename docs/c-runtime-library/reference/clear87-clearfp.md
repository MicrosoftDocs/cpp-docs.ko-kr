---
description: '자세히 알아보기: _clear87, _clearfp'
title: _clear87, _clearfp
ms.date: 04/05/2018
api_name:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: c15dd66f9a6598f351a54f0269619d9768eaa152
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124958"
---
# <a name="_clear87-_clearfp"></a>_clear87, _clearfp

부동 소수점 상태 단어를 가져오고 지웁니다.

## <a name="syntax"></a>구문

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Return Value

반환 된 값의 비트는 **_clear87** 또는 **_clearfp** 호출 전의 부동 소수점 상태를 표시 합니다. **_Clear87** 에서 반환 된 비트의 전체 정의는 Float. h를 참조 하세요. 많은 수학 라이브러리 함수는 예기치 않은 결과를 포함하여 8087/80287 상태 단어를 수정합니다. 부동 소수점 상태 단어의 알려진 상태 사이에서 수행 되는 부동 소수점 작업의 수를 줄이면 **_clear87** 및 **_status87** 의 반환 값이 더 안정적이 됩니다.

## <a name="remarks"></a>설명

**_Clear87** 함수는 부동 소수점 상태 단어의 예외 플래그를 지우고 사용 중인 비트를 0으로 설정 하 고 상태 단어를 반환 합니다. 부동 소수점 상태 단어는 8087/80287 상태 단어와 8087/80287 예외 처리기에서 검색한 기타 조건(예: 부동 소수점 스택 오버플로 및 언더플로)의 조합입니다.

**_clearfp** 는 플랫폼 독립적인 이식 가능한 버전의 **_clear87** 루틴입니다. 이는 Intel (x86) 플랫폼에서 **_clear87** 하는 것과 동일 하며 X64 및 ARM 플랫폼 에서도 지원 됩니다. 부동 소수점 코드를 x64 및 ARM으로 이식할 수 있도록 하려면 **_clearfp** 를 사용 합니다. X86 플랫폼만 대상으로 하는 경우 **_clear87** 또는 **_clearfp** 를 사용할 수 있습니다.

공용 언어 런타임은 기본 부동 소수점 전체 자릿수를 지원 하기 때문에 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일할 때 이러한 함수는 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \_ _control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
