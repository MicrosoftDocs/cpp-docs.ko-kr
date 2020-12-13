---
description: '자세한 정보: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson'
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d9840fbb0ccbefd5b9d78f4c3a7b208dc7b89571
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332748"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

이러한 함수는 C 런타임 라이브러리에서 CRT 라이브러리 함수에 전달된 유효하지 않은 매개 변수를 처리하는 데 사용됩니다. 코드에서는 유효하지 않은 매개 변수의 기본 처리 또는 사용자 지정 가능한 처리를 지원하기 위해 이러한 함수를 사용할 수도 있습니다.

## <a name="syntax"></a>구문

```C
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

## <a name="parameters"></a>매개 변수

*expression*<br/>
잘못된 소스 코드 매개 변수 식을 나타내는 문자열입니다.

*function_name*<br/>
처리기를 호출한 함수의 이름입니다.

*file_name*<br/>
처리기가 호출된 소스 코드 파일입니다.

*line_number*<br/>
처리기가 호출된 소스 코드의 줄 번호입니다.

*쓰이는*<br/>
사용되지 않습니다.

## <a name="return-value"></a>반환 값

이러한 함수는 값을 반환하지 않습니다. **_Invalid_parameter_noinfo_noreturn** 및 **_invoke_watson** 함수는 호출자로 반환 되지 않으며, 경우에 따라 **_invalid_parameter** 및 **_invalid_parameter_noinfo** 호출자로 반환 되지 않을 수 있습니다.

## <a name="remarks"></a>설명

C 런타임 라이브러리 함수가 유효하지 않은 매개 변수를 전달하는 경우 라이브러리 함수는 프로그래머가 여러 가지 작업을 수행하도록 지정할 수 있는 함수인 *잘못된 매개 변수 처리기* 를 호출합니다. 예를 들어 사용자에게 문제를 보고하거나, 로그에 기록하거나, 디버거를 중단하거나, 프로그램을 종료하거나, 아무 작업도 수행하지 않을 수 있습니다. 프로그래머가 함수를 지정 하지 않은 경우 기본 처리기 **_invoke_watson** 가 호출 됩니다.

기본적으로 디버그 코드에서 유효 하지 않은 매개 변수를 식별 하는 경우 CRT 라이브러리 함수는 자세한 매개 변수를 사용 하 여 **_invalid_parameter** 함수를 호출 합니다. 디버그가 아닌 코드에서 **_invalid_parameter_noinfo** 함수를 호출 합니다 .이 함수는 빈 매개 변수를 사용 하 여 **_invalid_parameter** 함수를 호출 합니다. 디버그가 아닌 CRT 라이브러리 함수에 프로그램 종료가 필요한 경우 **_invalid_parameter_noinfo_noreturn** 함수를 호출 합니다 .이 함수는 빈 매개 변수를 사용 하 여 **_invalid_parameter** 함수를 호출한 다음 **_invoke_watson** 함수를 호출 하 여 프로그램 종료를 강제로 실행 합니다.

**_Invalid_parameter** 함수는 사용자 정의 잘못 된 매개 변수 처리기가 설정 되었는지 여부를 확인 하 고, 그럴 경우 호출 합니다. 예를 들어 사용자 정의 스레드 로컬 처리기가 현재 스레드에서 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)를 호출하여 설정된 경우 호출되면 함수가 반환됩니다. 그러지 않고 사용자 정의 전역 잘못된 매개 변수 처리기가 [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)를 호출하여 설정된 경우 호출되면 함수가 반환됩니다. 그렇지 않으면 기본 처리기 **_invoke_watson** 가 호출 됩니다. **_Invoke_watson** 의 기본 동작은 프로그램을 종료 하는 것입니다. 사용자 정의 처리기가 종료되거나 반환될 수 있습니다. 복구가 확실하지 않으면 사용자 정의 처리기에서 프로그램을 종료하는 것이 좋습니다.

기본 처리기 **_invoke_watson** 가 호출 되 면 프로세서가 [__fastfail](../../intrinsics/fastfail.md) 작업을 지 원하는 경우 **FAST_FAIL_INVALID_ARG** 매개 변수를 사용 하 여 호출 되 고 프로세스가 종료 됩니다. 그렇지 않으면 빠른 실패 예외가 발생하며 연결된 디버거에서 catch할 수 있습니다. 프로세스를 계속할 수 있는 경우 **STATUS_INVALID_CRUNTIME_PARAMETER** 예외 코드 상태를 사용 하 여 Windows **TerminateProcess** 함수를 호출 하 여 종료 됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)<br/>
