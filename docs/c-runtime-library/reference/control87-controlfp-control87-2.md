---
description: _Control87, _controlfp, __control87_2에 대해 자세히 알아보세요.
title: _control87, _controlfp, __control87_2
ms.date: 08/29/2019
api_name:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: 0270c4a65225ad463f9098b5c00d311ee1096652
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146512"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87, _controlfp, __control87_2

부동 소수점 제어 단어를 가져와서 설정합니다. **_Controlfp** 의 더 안전한 버전을 사용할 수 있습니다. [_controlfp_s](controlfp-s.md)를 참조 하세요.

## <a name="syntax"></a>구문

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>매개 변수

*새로운*\
새 제어 단어 비트 값입니다.

*마스크할*\
설정할 새 제어 단어 비트의 마스크입니다.

*x86_cw*\
x87 부동 소수점 유닛에 대한 제어 단어로 채워집니다. SSE2 제어 단어만 설정 하려면 0 (**NULL**)을 전달 합니다.

*sse2_cw*\
SSE 부동 소수점 유닛에 대한 제어 단어입니다. 0 (**NULL**)을 전달 하 여 x87 제어 단어만 설정 합니다.

## <a name="return-value"></a>반환 값

**_Control87** 및 **_controlfp** 의 경우 반환 되는 값의 비트는 부동 소수점 제어 상태를 표시 합니다. **_Control87** 에서 반환 된 비트의 전체 정의는 FLOAT. H를 참조 하십시오.

**__Control87_2** 의 경우 반환 값은 성공을 나타내는 1입니다.

## <a name="remarks"></a>설명

**_Control87** 함수는 부동 소수점 제어 단어를 가져오고 설정 합니다. 부동 소수점 제어 단어를 사용 하면 프로그램이 플랫폼에 따라 전체 자릿수, 반올림 및 무한대 모드를 변경할 수 있습니다. 또한 **_control87** 를 사용 하 여 부동 소수점 예외를 마스킹 또는 마스크 해제할 수 있습니다. *Mask* 의 값이 0 인 경우 부동 소수점 제어 단어를 **_control87** 가져옵니다. *Mask* 가 0이 아닌 경우 제어 단어의 새 값이 설정 됩니다. 즉, *mask* 의 모든 비트 (즉, 1과 같음)에 대해 *new* 의 해당 비트가 제어 단어를 업데이트 하는 데 사용 됩니다. 즉, **fpcntrl** = ((**fpcntrl** & ~*mask*) &#124; (*new*  &  *mask*))를 지정 합니다. 여기서 **fpcntrl** 은 부동 소수점 제어 단어입니다.

> [!NOTE]
> 기본적으로 런타임 라이브러리는 모든 부동 소수점 예외를 마스킹합니다.

**_controlfp** 은 **_control87** 함수와 거의 동일한 플랫폼 독립적 휴대용 버전의 **_control87** 입니다. 코드에서 두 개 이상의 플랫폼을 대상으로 하는 경우 **_controlfp** 또는 **_controlfp_s** 를 사용 합니다. **_Control87** 와 **_controlfp** 간의 차이점은 DENORMAL 값을 처리 하는 방법에 있습니다. X86, x64, ARM 및 ARM64 플랫폼용 **_CONTROL87** DENORMAL 피연산자 예외 마스크를 설정 하 고 지울 수 있습니다. **_CONTROLFP** DENORMAL 피연산자 예외 마스크를 수정 하지 않습니다. 이 예제에서는 다음과 같은 차이를 보여 줍니다.

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Mask 상수 (*mask*) 및 새 컨트롤 값 (*new*)에 사용할 수 있는 값은 컨트롤 word 마스크 및 값 표에 표시 됩니다. 16 진수 값을 명시적으로 제공 하는 대신 아래에 나열 된 이식 가능한 상수 (**_MCW_EM**, **_EM_INVALID** 등)를 이러한 함수의 인수로 사용 합니다.

Intel x86 파생 플랫폼은 하드웨어에서 DENORMAL 입력 및 출력 값을 지원 합니다. x86 동작은 DENORMAL 값을 유지하는 것입니다. ARM 및 ARM64 플랫폼과 SSE2를 지 원하는 x64 플랫폼을 사용 하면 DENORMAL 피연산자와 결과를 플러시할 수 있습니다. **_Controlfp** 및 **_control87** 함수는이 동작을 변경 하는 마스크를 제공 합니다. 다음 예제에서는 이 마스크의 사용을 보여 줍니다.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

ARM 및 ARM64 플랫폼에서 **_control87** 및 **_controlfp** 함수는 fpscr 레지스터에 적용 됩니다. MXCSR 레지스터에 저장 된 SSE2 제어 단어만 x64 플랫폼에서 영향을 받습니다. X86 플랫폼에서 **_control87** 및 **_controlfp** 는 x87 및 SSE2 모두에 대 한 제어 단어 (있는 경우)에 영향을 줍니다.

**__Control87_2** 함수를 사용 하면 X87 및 SSE2 부동 소수점 단위를 함께 또는 별도로 제어할 수 있습니다. 두 단위에 모두 영향을 주려면 두 정수의 주소를 전달 하 여 **x86_cw** 하 고 **sse2_cw** 합니다. 하나의 단위에만 영향을 주려면 해당 매개 변수에 대 한 주소를 전달 하지만 다른에는 0 (**NULL**)을 전달 합니다. 이러한 매개 변수 중 하나에 대해 0을 전달하면 함수가 부동 소수점 유닛에는 영향을 주지 않습니다. 코드의 일부에서 x87 부동 소수점 단위를 사용 하 고 다른 부분은 SSE2 부동 소수점 단위를 사용 하는 경우 유용 합니다.

**__Control87_2** 를 사용 하 여 부동 소수점 제어 단어에 대해 다른 값을 설정 하는 경우 **_control87** 또는 **_controlfp** 는 두 부동 소수점 단위의 상태를 나타내기 위해 단일 제어 단어를 반환 하지 못할 수 있습니다. 이러한 경우 이러한 함수는 반환 된 정수 값에 **EM_AMBIGUOUS** 플래그를 설정 하 여 두 개의 제어 단어 간에 불일치를 표시 합니다. **EM_AMBIGUOUS** 플래그는 반환 된 컨트롤 단어가 두 부동 소수점 제어 단어의 상태를 정확 하 게 나타내지 않을 수 있다는 경고입니다.

ARM, ARM64 및 x64 플랫폼에서 무한대 모드 또는 부동 소수점 정밀도를 변경 하는 것은 지원 되지 않습니다. 전체 자릿수 제어 마스크가 x64 플랫폼에서 사용 되는 경우이 함수는 어설션을 발생 시키고 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다.

> [!NOTE]
> **__CONTROL87_2** ARM, ARM64 또는 x64 플랫폼에서 지원 되지 않습니다. **__Control87_2** 를 사용 하 고 ARM, ARM64 또는 x64 플랫폼용 프로그램을 컴파일하는 경우 컴파일러에서 오류를 생성 합니다.

[/Clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일할 때 이러한 함수는 무시 됩니다. CLR (공용 언어 런타임)은 기본 부동 소수점 전체 자릿수를 지원 합니다.

### <a name="control-word-masks-and-values"></a>단어 마스크 및 값 제어

**_MCW_EM** 마스크의 경우 마스크를 지우면 하드웨어 예외가 허용 되는 예외를 설정 합니다. 마스크를 설정 하면 예외가 숨겨집니다. **_EM_UNDERFLOW** 또는 **_EM_OVERFLOW** 발생 하면 다음 부동 소수점 명령이 실행 될 때까지 하드웨어 예외가 throw 되지 않습니다. **_EM_UNDERFLOW** 또는 **_EM_OVERFLOW** 직후에 하드웨어 예외를 생성 하려면 **fwait** MASM 명령을 호출 합니다.

|Mask|16진수 값|상수|16진수 값|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Denormal 컨트롤)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (인터럽트 예외 마스크)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Infinity 컨트롤)<br /><br /> ARM 또는 x64 플랫폼에서는 지원 되지 않습니다.|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (반올림 제어)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (전체 자릿수 컨트롤)<br /><br /> ARM 또는 x64 플랫폼에서는 지원 되지 않습니다.|0x00030000|**_PC_24** (24 비트)<br /><br /> **_PC_53** (53 비트)<br /><br /> **_PC_64** (64 비트)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[_clear87, _clearfp](clear87-clearfp.md)\
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
