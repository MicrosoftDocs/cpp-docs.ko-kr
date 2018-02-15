---
title: "_fpieee_flt | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fpieee_flt
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fpieee_flt
- _fpieee_flt
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88d05d4d8c7f403cc2702c5a0ec3b2af840bd320
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="fpieeeflt"></a>_fpieee_flt
IEEE 부동 소수점 예외에 대한 사용자 정의 트랩 처리기를 호출합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `excCode`  
 예외 코드입니다.  
  
 `excInfo`  
 Windows NT 예외 정보 구조체에 대한 포인터입니다.  
  
 `handler`  
 사용자의 IEEE 트랩 처리기 루틴에 대한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 `_fpieee_flt`의 반환 값은 `handler`의해 반환되는 값입니다. 따라서 IEEE 필터 루틴은 SEH(구조적 예외 처리) 메커니즘의 예외 절에서 사용될 수 있습니다.  
  
## <a name="remarks"></a>설명  
 `_fpieee_flt` 함수는 IEEE 부동 소수점 예외에 대한 사용자 정의 트랩 처리기를 호출하고 모든 관련 정보를 제공합니다. 이 루틴은 필요할 때 자신의 IEEE 예외 처리기를 호출하는 SEH 메커니즘에서 예외 필터로 사용됩니다.  
  
 Fpieee.h에 정의된 `_FPIEEE_RECORD` 구조체는 IEEE 부동 소수점 예외에 대한 정보를 포함합니다. 이 구조체는 `_fpieee_flt`에 의해 사용자 정의 트랩 처리기로 전달됩니다.  
  
|_FPIEEE_RECORD 필드|설명|  
|----------------------------|-----------------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|이러한 필드는 예외가 발생했을 때 부동 소수점 환경에 대한 정보를 포함합니다.|  
|`unsigned int Operation`|트랩을 발생시킨 작업의 형식을 나타냅니다. 해당 형식이 비교(`_FpCodeCompare`)인 경우 `_FPIEEE_COMPARE_RESULT` 필드에 특수 `Result.Value` 값(Fpieee.h에 정의됨) 중 하나를 제공할 수 있습니다. 변환 형식(`_FpCodeConvert`)은 부동 소수점 변환 작업을 수행하는 동안 트랩이 발생했음을 나타냅니다. `Operand1` 및`Result` 형식을 살펴보면 시도되는 변환 형식을 확인할 수 있습니다.|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|이러한 구조체는 제안된 결과 및 피연산자의 형식 및 값을 나타냅니다.<br /><br /> `OperandValid` 응답 값이 올바른지 여부를 나타내는 플래그입니다.<br /><br /> `Format` 해당 값의 데이터 형식입니다. 해당 값이 잘못되어도 형식 유형이 반환될 수 있습니다.<br /><br /> `Value` 결과 또는 피연산자 데이터 값입니다.|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|_FPIEEE_EXCEPTION_FLAGS는 부동 소수점 예외의 형식당 1비트 필드를 포함합니다.<br /><br /> 이러한 필드와 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)에 제공된 예외를 마스크하는 데 사용하는 인수 간에 대응 관계가 있습니다.<br /><br /> 각 비트의 정확한 의미는 컨텍스트에 따라 달라집니다.<br /><br /> `Cause`각 설정 비트는 발생된 특정 예외를 나타냅니다.<br /><br /> `Enable`각 설정 비트는 특정 예외가 현재 마스크되지 않음을 나타냅니다.<br /><br /> `Status`각 설정 비트는 특정 예외가 현재 보류 중임을 나타냅니다. 이는 `_controlfp`에 의해 마스크되었기 때문에 발생하지 못한 예외를 포함합니다.|  
  
 사용할 수 없는 보류 중 예외는 해당 예외를 사용할 때 발생합니다. `_fpieee_flt`를 예외 필터로 사용할 때 이는 정의되지 않은 동작을 발생시킵니다. 부동 소수점 예외를 사용하도록 설정하기 전에 항상 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)를 호출합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|함수|필수 헤더|  
|--------------|---------------------|  
|`_fpieee_flt`|\<fpieee.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_fpieee.c  
// This program demonstrates the implementation of  
// a user-defined floating-point exception handler using the  
// _fpieee_flt function.  
  
#include <fpieee.h>  
#include <excpt.h>  
#include <float.h>  
#include <stddef.h>  
  
int fpieee_handler( _FPIEEE_RECORD * );  
  
int fpieee_handler( _FPIEEE_RECORD *pieee )  
{  
   // user-defined ieee trap handler routine:  
   // there is one handler for all   
   // IEEE exceptions  
  
   // Assume the user wants all invalid   
   // operations to return 0.  
  
   if ((pieee->Cause.InvalidOperation) &&   
       (pieee->Result.Format == _FpFormatFp32))   
   {  
        pieee->Result.Value.Fp32Value = 0.0F;  
  
        return EXCEPTION_CONTINUE_EXECUTION;  
   }  
   else  
      return EXCEPTION_EXECUTE_HANDLER;  
}  
  
#define _EXC_MASK    \  
    _EM_UNDERFLOW  + \  
    _EM_OVERFLOW   + \  
    _EM_ZERODIVIDE + \  
    _EM_INEXACT  
  
int main( void )  
{  
   // ...  
  
   __try {  
      // unmask invalid operation exception  
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);   
  
      // code that may generate   
      // fp exceptions goes here  
   }  
   __except ( _fpieee_flt( GetExceptionCode(),  
                GetExceptionInformation(),  
                fpieee_handler ) ){  
  
      // code that gets control   
  
      // if fpieee_handler returns  
      // EXCEPTION_EXECUTE_HANDLER goes here  
  
   }  
  
   // ...  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [부동 소수점 지원](../../c-runtime-library/floating-point-support.md)   
 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)