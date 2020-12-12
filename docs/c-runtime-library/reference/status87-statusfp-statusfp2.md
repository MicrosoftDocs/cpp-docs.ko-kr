---
description: _Status87, _statusfp, _statusfp2에 대해 자세히 알아보세요.
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 98e99d01e7ad96e856de589e498bbd4ea794bdcb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171142"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

부동 소수점 상태 단어를 가져옵니다.

## <a name="syntax"></a>구문

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>매개 변수

*px86*<br/>
이 주소에는 x87 부동 소수점 단위의 상태 단어가 채워집니다.

*pSSE2*<br/>
이 주소에는 SSE2 부동 소수점 단위의 상태 단어가 채워집니다.

## <a name="return-value"></a>반환 값

**_Status87** 및 **_statusfp** 의 경우 반환 되는 값의 비트는 부동 소수점 상태를 표시 합니다. FLOAT를 참조 하십시오. H include 파일 **_statusfp** 에 의해 반환 되는 비트 정의 파일입니다. 대부분의 수학 라이브러리 함수는 부동 소수점 상태 단어를 수정하는데, 이 경우 예기치 않은 결과가 발생합니다. 최적화는 **_status87**, **_statusfp** 및 관련 함수에 대 한 호출에 대 한 부동 소수점 작업의 순서를 변경, 결합 및 제거할 수 있습니다. 부동 소수점 연산을 다시 정렬하는 최적화가 수행되지 않도록 하려면 [/Od (Disable (Debug))](../../build/reference/od-disable-debug.md) 컴파일러 옵션 또는 [fenv_access](../../preprocessor/fenv-access.md) pragma 지시문을 사용합니다. 부동 소수점 상태 단어의 알려진 상태 사이에서 수행 되는 부동 소수점 작업 수가 적을수록 **_clearfp** 및 **_statusfp** 의 반환 값 및 **_statusfp2** 반환 매개 변수는 더 안정적입니다.

## <a name="remarks"></a>설명

**_Statusfp** 함수는 부동 소수점 상태 단어를 가져옵니다. 상태 단어는 부동 소수점 프로세서 상태와 부동 소수점 예외 처리기에서 검색한 기타 조건(예: 부동 소수점 스택 오버플로 및 언더플로)의 조합입니다. 상태 단어의 내용을 반환하기 전에 마스킹되지 않은 예외를 확인합니다. 즉, 호출자에게 보류 중인 예외를 알립니다. X86 플랫폼에서 **_statusfp** 는 X87 및 SSE2 부동 소수점 상태의 조합을 반환 합니다. x64 플랫폼에서 반환되는 상태는 SSE의 MXCSR 상태를 기준으로 합니다. ARM 플랫폼에서 **_statusfp** 는 fpscr 레지스터의 상태를 반환 합니다.

**_statusfp** 는 플랫폼 독립적 이며 **_status87** 의 이식 가능한 버전입니다. 이는 Intel (x86) 플랫폼에서 **_status87** 하는 것과 동일 하며 X64 및 ARM 플랫폼 에서도 지원 됩니다. 부동 소수점 코드를 모든 아키텍처로 이식할 수 있도록 하려면 **_statusfp** 을 사용 합니다. X86 플랫폼만 대상으로 하는 경우 **_status87** 또는 **_statusfp** 를 사용할 수 있습니다.

X87 및 SSE2 부동 소수점 프로세서를 모두 포함 하는 칩 (예: Pentium IV)에 **_statusfp2** 하는 것이 좋습니다. **_Statusfp2** 의 경우 X87 또는 SSE2 부동 소수점 프로세서 모두에 대해 부동 소수점 상태 단어를 사용 하 여 주소를 채웁니다. X87 및 SSE2 부동 소수점 프로세서를 지 원하는 칩의 경우 **_statusfp** 또는 **_controlfp** 사용 되 고 작업은 x87 또는 SSE2 부동 소수점 상태 단어를 참조할 수 있으므로 EM_AMBIGUOUS 1로 설정 됩니다. **_Statusfp2** 함수는 x86 플랫폼 에서만 지원 됩니다.

CLR (공용 언어 런타임)은 기본 부동 소수점 전체 자릿수를 지원 하기 때문에 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 에는 이러한 함수가 유용 하지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_control87, _controlfp, \_ _control87_2](control87-controlfp-control87-2.md)<br/>
