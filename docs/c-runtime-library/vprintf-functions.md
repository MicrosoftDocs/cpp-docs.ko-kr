---
description: '자세한 정보: vprintf 함수'
title: vprintf 함수
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: 54490518fd083826108da6a87e4a759fc2aa6227
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162099"
---
# <a name="vprintf-functions"></a>vprintf 함수

이러한 `vprintf` 함수는 각각 인수 목록에 대한 포인터를 가져오며 지정된 데이터의 형식을 지정하고 특정 대상에 지정된 데이터를 씁니다. 이러한 함수는 수행되는 매개 변수 유효성 검사, 함수가 와이드 문자를 사용하는지 또는 싱글바이트 문자열을 사용하는지, 출력 대상 및 형식 문자열에 매개 변수가 사용되는 순서를 지정하는 기능에 대한 지원 측면에서 다릅니다.

[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)\
[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)\
[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)\
[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)\
[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)\
[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)\
[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)\
[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 
 [vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)\
[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)\
[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)

## <a name="remarks"></a>설명

`vprintf` 함수는 다음 표에 나열된 상대 함수와 비슷합니다. 그러나 각 `vprintf` 함수는 인수 목록에 대한 포인터를 수락하지만 각 상대 함수는 인수 목록을 수락합니다.

이러한 함수는 대상 출력에 대한 데이터 서식을 다음과 같이 지정합니다.

|함수|상대 함수|출력 대상|매개 변수 유효성 검사|위치 매개 변수 지원|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|콘솔|Null인지 확인합니다.|no|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|콘솔|Null인지 확인합니다.|no|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*스트림*|Null인지 확인합니다.|no|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*스트림*|Null 및 유효한 형식인지 확인합니다.|예|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*스트림*|Null 및 유효한 형식인지 확인합니다.|no|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*스트림*|Null인지 확인합니다.|no|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*스트림*|Null 및 유효한 형식인지 확인합니다.|예|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*스트림*|Null 및 유효한 형식인지 확인합니다.|no|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Null인지 확인합니다.|no|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Null 및 유효한 형식인지 확인합니다.|예|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Null 및 유효한 형식인지 확인합니다.|no|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Null인지 확인합니다.|no|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Null 및 유효한 형식인지 확인합니다.|예|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Null 및 유효한 형식인지 확인합니다.|no|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*buffer* 로 가리키는 메모리|Null 및 유효한 형식인지 확인합니다.|예|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*buffer* 로 가리키는 메모리|Null 및 유효한 형식인지 확인합니다.|no|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*buffer* 로 가리키는 메모리|Null 및 유효한 형식인지 확인합니다.|예|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*buffer* 로 가리키는 메모리|Null 및 유효한 형식인지 확인합니다.|no|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*buffer* 로 가리키는 메모리|Null인지 확인합니다.|no|

`argptr` 인수 형식은 VARARGS.H 및 STDARG.H에 정의된 `va_list`입니다. `argptr` 변수는 **va_start** 에 의해 초기화되어야 하고 후속 `va_arg` 호출로 다시 초기화할 수 있습니다. `argptr`은 인수 목록의 맨 처음을 가리킵니다. 이러한 인수는 *format* 인수에 지정된 해당 사양에 따라 출력을 위해 변환 및 전송됩니다. *format* 은 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)에 대한 *format* 인수와 같은 양식 및 함수를 갖습니다. 이러한 함수는 `va_end`를 호출하지 않습니다. 각 `vprintf` 함수에 대한 자세한 설명을 보려면 앞의 표에 나열된 상대 함수에 대한 설명을 참조하세요.

`_vsnprintf`는 *count* 바이트만 *buffer* 에 쓴다는 점에서 **vsprintf** 와 다릅니다.

이름에 **w** 중위가 있는 이러한 함수의 버전은 **w** 중위가 없는 해당 함수의 와이드 문자 버전입니다. 이러한 각 와이드 문자 함수에서 *buffer* 및 *format* 은 와이드 문자열입니다. 그렇지 않은 경우 각 와이드 문자 함수는 해당 SBCS 상대 함수와 동일하게 동작합니다.

**_s** 및 **_p** 접미사가 있는 이러한 함수 버전이 좀 더 안전한 버전입니다. 이러한 버전은 형식 문자열의 유효성을 검사하고 형식 문자열 형식이 잘못되면(예를 들어 잘못된 형식 지정 문자 사용) 예외를 발생합니다.

**_p** 접미사가 있는 이러한 함수 버전은 형식 문자열에서 제공된 인수가 대체되는 순서를 지정하는 기능을 제공합니다. 자세한 내용은 [printf_p 위치 매개 변수](../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**Vsprintf**, 및의 경우 `vswprintf` `_vsnprintf` `_vsnwprintf` 중복 되는 문자열 간에 복사를 수행 하는 경우 동작이 정의 되지 않습니다.

> [!IMPORTANT]
> *format* 이 사용자 정의 문자열이 아닌지 확인하세요. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요. 이러한 함수의 보안 버전을 사용하는 경우(**_s** 또는 **_p** 접미사) 사용자 제공 형식 문자열은 사용자 제공 문자열에 잘못된 형식 지정 문자가 포함되어 있으면 잘못된 매개 변수 예외를 트리거할 수 있습니다.

## <a name="see-also"></a>참고 항목

[스트림 I/O](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
