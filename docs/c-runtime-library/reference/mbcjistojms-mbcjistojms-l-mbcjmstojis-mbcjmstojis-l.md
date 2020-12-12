---
description: '자세한 정보: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l'
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 4/2/2020
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
- _o__mbcjistojms
- _o__mbcjistojms_l
- _o__mbcjmstojis
- _o__mbcjmstojis_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: 6c7d19ce59c381d4f4a60fb2d1ddbed41fe43ba3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171519"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

JIS(Japan Industry Standard)와 JMS(일본 Microsoft) 문자 간을 변환합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
변환할 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

일본어 로캘에서 이러한 함수는 변환된 문자를 반환하거나 변환할 수 없는 경우 0을 반환합니다. 일본어가 아닌 다른 언어 로캘에서 이러한 함수는 전달된 문자를 반환합니다.

## <a name="remarks"></a>설명

**_Mbcjistojms** 함수는 일본 산업 표준 (JIS) 문자를 Microsoft 간지 (Shift JIS) 문자로 변환 합니다. 문자는 선행 및 후행 바이트가 0x21-0x7E의 범위에 있는 경우에만 변환 됩니다. 선행 또는 평가판 바이트가이 범위를 벗어나면 **errno** 는 **eilseq** 로 설정 됩니다. 이 오류 코드 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

**_Mbcjmstojis** 함수는 Shift jis 문자를 JIS 문자로 변환 합니다. 선행 바이트가 0x81-0x9F 또는 0xE0-0xFC 범위에 있고 트레일 바이트가 0x40-0x7E 또는 0x80-0xFC 범위에 있는 경우에만 문자가 변환 됩니다. 해당 범위의 일부 코드 포인트에는 할당된 문자가 없으므로 변환할 수 없습니다.

값 *c* 는 16 비트 값 이어야 합니다. 상위 8 비트는 변환할 문자의 선행 바이트를 나타내고, 하위 8 비트는 후행 바이트를 나타냅니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

이전 버전에서는 **_mbcjistojms** 및 **_mbcjmstojis** 를 각각 **jistojms** 및 **jistojms** 라고 했습니다. **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** 및 **_mbcjmstojis_l** 를 대신 사용 해야 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb 루틴](../../c-runtime-library/ismbb-routines.md)<br/>
