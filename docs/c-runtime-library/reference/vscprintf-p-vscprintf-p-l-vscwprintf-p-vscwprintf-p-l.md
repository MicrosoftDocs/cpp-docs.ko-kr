---
description: '자세한 정보: _vscprintf_p, _vscprintf_p_l, _vscwprintf_p, _vscwprintf_p_l'
title: _vscprintf_p, _vscprintf_p_l, _vscwprintf_p, _vscwprintf_p_l
ms.date: 3/9/2021
api_name:
- _vscprintf_p_l
- _vscprintf_p
- _vscwprintf_p_l
- _vscwprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vscprintf_p
- _vscprintf_p_l
- vscwprintf_p
- vscprintf_p
- vscwprintf_p_l
- _vscwprintf_p_l
- vscprintf_p_l
- _vscwprintf_p
helpviewer_keywords:
- vscprintf_p function
- _vsctprintf_p_l function
- vscwprintf_p_l function
- _vscwprintf_p_l function
- _vscprintf_p function
- vsctprintf_p function
- _vscprintf_p_l function
- _vscwprintf_p function
- vscwprintf_p function
- vsctprintf_p_l function
- _vsctprintf_p function
- vscprintf_p_l function
ms.openlocfilehash: 2aa08bb8164a741a74405cb1fdb16c5db1506d32
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621687"
---
# <a name="_vscprintf_p-_vscprintf_p_l-_vscwprintf_p-_vscwprintf_p_l"></a>_vscprintf_p, _vscprintf_p_l, _vscwprintf_p, _vscwprintf_p_l

인수가 사용되는 순서를 지정하는 기능과 함께 인수 목록에 대한 포인터를 사용하여 형식이 지정된 문자열의 문자 수를 반환합니다.

## <a name="syntax"></a>구문

```C
int _vscprintf_p(
   const char *format,
   va_list argptr
);
int _vscprintf_p _l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vscwprintf_p (
   const wchar_t *format,
   va_list argptr
);
int _vscwprintf_p _l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>매개 변수

*format*<br/>
형식 컨트롤 문자열입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

**_vscprintf_p** 는 인수 목록에서 가리키는 문자열이 지정 된 형식 지정 코드를 사용 하 여 인쇄 되거나 파일 또는 버퍼로 전송 될 경우 생성 되는 문자 수를 반환 합니다. 반환된 값은 종료 null 문자를 포함하지 않습니다. **_vscwprintf_p** 는 와이드 문자에 대해 동일한 기능을 수행 합니다.

## <a name="remarks"></a>설명

이러한 함수는 인수가 사용 되는 순서를 지정 하는 기능을 지 원하는 경우에만 **_vscprintf** 와 **_vscwprintf** 다릅니다. 자세한 내용은 [printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

*Format* 이 null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

> [!IMPORTANT]
> *Format* 이 사용자 정의 문자열인 경우 null로 종료 되 고 올바른 수와 형식의 매개 변수를 사용 해야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면 [' legacy_stdio_float_rounding .obj '](../link-options.md)를 사용 하 여 연결 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsctprintf_p**|**_vscprintf_p**|**_vscprintf_p**|**_vscwprintf_p**|
|**_vsctprintf_p_l**|**_vscprintf_p_l**|**_vscprintf_p_l**|**_vscwprintf_p_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_vscprintf_p**, **_vscprintf_p_l**|\<stdio.h>|
|**_vscwprintf_p**, **_vscwprintf_p_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예

[vsprintf](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[_scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l](scprintf-p-scprintf-p-l-scwprintf-p-scwprintf-p-l.md)<br/>
[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)<br/>
