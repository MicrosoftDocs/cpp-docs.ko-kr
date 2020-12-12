---
description: '자세한 정보: _vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l'
title: _vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l
ms.date: 11/04/2016
api_name:
- _vwprintf_p
- _vprintf_p
- _vprintf_p_l
- _vwprintf_p_l
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
- _vwprintf_p_l
- vprintf_p
- _vprintf_p_l
- _vwprintf_p
- vprintf_p_l
- vwprintf_p_l
- vwprintf_p
- vtprintf_p
- _vtprintf_p
- _vprintf_p
helpviewer_keywords:
- _vtprintf_p_l function
- _vtprintf_p function
- vtprintf_p function
- _vwprintf_p function
- _vwprintf_p_l function
- _vprintf_p function
- _vprintf_p_l function
- vprintf_p_l function
- vwprintf_p function
- vprintf_p function
- vtprintf_p_l function
- vwprintf_p_l function
- formatted text [C++]
ms.assetid: 3f99bde3-c891-493d-908f-30559c421058
ms.openlocfilehash: 20bee781aa139335dbdbb2feac299e0dde8da8c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120645"
---
# <a name="_vprintf_p-_vprintf_p_l-_vwprintf_p-_vwprintf_p_l"></a>_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l

인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 작성하고, 인수가 사용되는 순서를 지정할 수 있도록 설정합니다.

## <a name="syntax"></a>구문

```C
int _vprintf_p(
   const char *format,
   va_list argptr
);
int _vprintf_p_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vwprintf_p(
   const wchar_t *format,
   va_list argptr
);
int _vwprintf_p_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>매개 변수

*format*<br/>
형식 사양입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

**_vprintf_p** 및 **_vwprintf_p** 는 종료 null 문자를 포함 하지 않고 작성 된 문자 수를 반환 하거나, 출력 오류가 발생 하는 경우 음수 값을 반환 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 인수 목록에 대 한 포인터를 가져온 다음 지정 된 데이터를 **stdout** 에 서식 지정 하 고 씁니다. 이러한 함수는 인수가 사용 되는 순서를 지정 하는 기능을 지 원하는 경우에만 **vprintf_s** 와 **vwprintf_s** 다릅니다. 자세한 내용은 [printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)를 참조하세요.

**_vwprintf_p** 은 **_vprintf_p** 의 와이드 문자 버전입니다. 두 함수는 스트림이 ANSI 모드에서 열리는 경우 동일 하 게 동작 합니다. **_vprintf_p** 는 현재 유니코드 스트림으로의 출력을 지원 하지 않습니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

> [!IMPORTANT]
> *format* 이 사용자 정의 문자열이 아닌지 확인하세요. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

*Format* 이 null 포인터 이거나 형식 문자열에 잘못 된 형식 지정 문자가 포함 된 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf_p**|**_vprintf_p**|**_vprintf_p**|**_vwprintf_p**|
|**_vtprintf_p_l**|**_vprintf_p_l**|**_vprintf_p_l**|**_vwprintf_p_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**_vprintf_p**, **_vprintf_p_l**|\<stdio.h> 및 \<stdarg.h>|\<varargs.h>*|
|**_vwprintf_p**, **_vwprintf_p_l**|\<stdio.h> 또는 \<wchar.h> , 및 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 호환성을 위해 필요합니다.

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf_p 위치 매개 변수](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
