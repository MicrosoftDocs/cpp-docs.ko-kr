---
title: _mbbtombc, _mbbtombc_l
ms.date: 4/2/2020
api_name:
- _mbbtombc_l
- _mbbtombc
- _o__mbbtombc
- _o__mbbtombc_l
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
ms.openlocfilehash: b2088ea83729a74a60e75d1710529480f34cd638
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919598"
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

## <a name="return-value"></a>Return Value

**_Mbbtombc** *c*를 성공적으로 변환 하는 경우 멀티 바이트 문자를 반환 합니다. 그렇지 않으면 *c*를 반환 합니다.

## <a name="remarks"></a>설명

**_Mbbtombc** 함수는 지정 된 싱글바이트 멀티 바이트 문자를 해당 더블 바이트 멀티 바이트 문자로 변환 합니다. 문자는 변환 될 0x20-0x7E 또는 0xA1-0Xa1 범위 내에 있어야 합니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따라 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale를](setlocale-wsetlocale.md) 참조 하세요. 이 함수의 버전은 **_mbbtombc** 이 로캘 종속 동작에 현재 로캘을 사용 하 **_mbbtombc_l** 고 대신 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

이전 버전에서는 **_mbbtombc** 이름이 **hantozen**입니다. 새 코드의 경우 **_mbbtombc**를 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참조

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
