---
description: '다음에 대 한 자세한 정보: _get_printf_count_output'
title: _get_printf_count_output
ms.date: 3/9/2021
api_name:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.openlocfilehash: f31c0321d2d7873db20e7d663918aebc002c768d
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102622129"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

[Printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)family 함수가 **% n** 형식을 지원 하는지 여부를 나타냅니다.

## <a name="syntax"></a>구문

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Return Value

**% N** 이 (가) 지원 되는 경우 0이 아닙니다. **% n** 이 (가) 지원 되지 않는 경우 0입니다.

## <a name="remarks"></a>설명

**% N** 이 (가) 지원 되지 않는 경우 (기본값) **printf** 함수의 형식 문자열에서 **% n** 을 (를) 발생 하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. **% N** 지원이 사용 하도록 설정 된 경우 [(_set_printf_count_output](set-printf-count-output.md)참조) **% n** 은 (는) [형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)에 설명 된 대로 동작 합니다.

> [!IMPORTANT]
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면 [' legacy_stdio_float_rounding .obj '](../link-options.md)를 사용 하 여 연결 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예

[_set_printf_count_output](set-printf-count-output.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[_set_printf_count_output](set-printf-count-output.md)<br/>
