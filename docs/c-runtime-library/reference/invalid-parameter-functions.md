---
title: "_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 258d3e3aa9f005c76b5e4f2b3739ee588cde3f0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
이러한 함수는 C 런타임 라이브러리에서 CRT 라이브러리 함수에 전달된 유효하지 않은 매개 변수를 처리하는 데 사용됩니다. 코드에서는 유효하지 않은 매개 변수의 기본 처리 또는 사용자 지정 가능한 처리를 지원하기 위해 이러한 함수를 사용할 수도 있습니다.

## <a name="syntax"></a>구문
```
extern "C" void __cdecl 
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);  

extern "C" void __cdecl 
_invalid_parameter_noinfo(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invalid_parameter_noinfo_noreturn(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invoke_watson(  
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="return-value"></a>반환 값
이러한 함수는 값을 반환하지 않습니다. `_invalid_parameter_noinfo_noreturn` 및 `_invoke_watson` 함수는 호출자로 돌아가지 않으며, 경우에 따라 `_invalid_parameter` 및 `_invalid_parameter_noinfo`는 호출자로 돌아가지 않을 수 있습니다.

## <a name="parameters"></a>매개 변수
`expression`  
잘못된 소스 코드 매개 변수 식을 나타내는 문자열입니다.

`function_name`  
처리기를 호출한 함수의 이름입니다.

`file_name`  
처리기가 호출된 소스 코드 파일입니다.

`line_number`  
처리기가 호출된 소스 코드의 줄 번호입니다.

`reserved`  
사용되지 않습니다.

## <a name="remarks"></a>설명
C 런타임 라이브러리 함수가 유효하지 않은 매개 변수를 전달하는 경우 라이브러리 함수는 프로그래머가 여러 가지 작업을 수행하도록 지정할 수 있는 함수인 *잘못된 매개 변수 처리기*를 호출합니다. 예를 들어 사용자에게 문제를 보고하거나, 로그에 기록하거나, 디버거를 중단하거나, 프로그램을 종료하거나, 아무 작업도 수행하지 않을 수 있습니다. 프로그래머가 함수를 지정하지 않으면 기본 처리기인 `_invoke_watson`이 호출됩니다.

기본적으로 디버그 코드에서 유효하지 않은 매개 변수가 식별되면 CRT 라이브러리 함수는 verbose 매개 변수를 사용하여 `_invalid_parameter` 함수를 호출합니다. 비디버그 코드에서는 `_invalid_parameter_noinfo` 함수가 호출되며, 이 함수는 빈 매개 변수를 사용하여 `_invalid_parameter` 함수를 호출합니다. 비디버그 CRT 라이브러리 함수에서 프로그램을 종료해야 하는 경우 `_invalid_parameter_noinfo_noreturn` 함수가 호출되며, 이 함수는 빈 매개 변수를 사용하여 `_invalid_parameter` 함수를 호출한 다음 `_invoke_watson` 함수를 호출하여 강제로 프로그램을 종료합니다.

`_invalid_parameter` 함수는 사용자 정의 잘못된 매개 변수 처리기가 설정되었는지 확인하고 그럴 경우 호출합니다. 예를 들어 사용자 정의 스레드 로컬 처리기가 현재 스레드에서 [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)를 호출하여 설정된 경우 호출되면 함수가 반환됩니다. 그러지 않고 사용자 정의 전역 잘못된 매개 변수 처리기가 [set_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)를 호출하여 설정된 경우 호출되면 함수가 반환됩니다. 그렇지 않으면 기본 처리기 `_invoke_watson`이 호출됩니다. `_invoke_watson`의 기본 동작은 프로그램을 종료하는 것입니다. 사용자 정의 처리기가 종료되거나 반환될 수 있습니다. 복구가 확실하지 않으면 사용자 정의 처리기에서 프로그램을 종료하는 것이 좋습니다. 

기본 처리기 `_invoke_watson`이 호출될 때 프로세서에서 [__fastfail](../../intrinsics/fastfail.md) 작업을 지원하면 `FAST_FAIL_INVALID_ARG`의 매개 변수를 사용하여 호출되고 프로세스가 종료됩니다. 그렇지 않으면 빠른 실패 예외가 발생하며 연결된 디버거에서 catch할 수 있습니다. 프로세스를 계속할 수 있는 경우 `STATUS_INVALID_CRUNTIME_PARAMETER`의 예외 코드 상태로 Windows `TerminateProcess` 함수를 호출하여 종료합니다. 

## <a name="requirements"></a>요구 사항  
|함수|필수 헤더|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [사전순 함수 참조](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)
