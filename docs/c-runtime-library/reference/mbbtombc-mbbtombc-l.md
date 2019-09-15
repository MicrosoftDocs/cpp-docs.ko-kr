---
title: _mbbtombc, _mbbtombc_l
ms.date: 11/04/2016
api_name:
- _mbbtombc_l
- _mbbtombc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 244e603a3234b755d19a1c1d0738e8c22d74b8e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952729"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc, _mbbtombc_l

싱글바이트 멀티바이트 문자를 해당 더블바이트 멀티바이트 문자로 변환합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
변환할 싱글바이트 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_Mbbtombc** 가 *c*를 성공적으로 변환 하는 경우 멀티 바이트 문자를 반환 합니다. 그렇지 않으면 *c*를 반환 합니다.

## <a name="remarks"></a>설명

**_Mbbtombc** 함수는 지정 된 싱글바이트 멀티 바이트 문자를 해당 더블 바이트 멀티 바이트 문자로 변환 합니다. 문자는 변환 될 0x20-0x7E 또는 0xA1-0Xa1 범위 내에 있어야 합니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale을](setlocale-wsetlocale.md) 참조 하세요. **_Mbbtombc** 는이 로캘 종속 동작에 현재 로캘을 사용 하 고 **_mbbtombc_l** 는 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고이 함수의 버전은 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

이전 버전에서 **_mbbtombc** 의 이름은 **hantozen**입니다. 새 코드의 경우 **_mbbtombc**를 사용 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
