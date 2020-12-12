---
description: '자세히 알아보기: _mbsbtype, _mbsbtype_l'
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: a1d17a947d830281b05291601c74ee944cebdb10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271059"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

문자열 내에서 바이트의 형식을 반환합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*mbstr*<br/>
멀티바이트 문자 시퀀스의 주소입니다.

*count*<br/>
문자열의 헤드로부터의 바이트 오프셋입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_mbsbtype** 및 **_mbsbtype_l** 는 지정 된 바이트에 대 한 테스트 결과를 나타내는 정수 값을 반환 합니다. 다음 표의 매니페스트 상수는 Mbctype.h에 정의됩니다.

|반환 값|바이트 형식|
|------------------|---------------|
|**_MBC_SINGLE** (0)|싱글바이트 문자입니다. 예를 들어 코드 페이지 932에서 **_mbsbtype** 지정 된 바이트가 0X20-0X7e 또는 0Xa1-0xa1 범위 내에 있는 경우 0을 반환 합니다.|
|**_MBC_LEAD** (1)|멀티바이트 문자의 선행 바이트입니다. 예를 들어 코드 페이지 932에서는 지정 된 바이트가 0x81-0x9F 또는 0xE0-0xFC 범위 내에 있는 경우 **_mbsbtype** 1을 반환 합니다.|
|**_MBC_TRAIL** (2)|멀티바이트 문자의 후행 바이트입니다. 예를 들어 코드 페이지 932에서 지정 된 바이트가 0x40-0x7E 또는 0x80-0xFC 범위 내에 있는 경우 **_mbsbtype** 는 2를 반환 합니다.|
|**_MBC_ILLEGAL** (-1)|*Mbstr* 의 오프셋 *개수* 에서 바이트 앞에 **null** 문자열, 잘못 된 문자 또는 null 바이트가 있습니다.|

## <a name="remarks"></a>설명

**_Mbsbtype** 함수는 멀티 바이트 문자열의 바이트 형식을 결정 합니다. 함수는 *mbstr* 의 오프셋 *개수* 에서 바이트를 검사 하 여 지정 된 바이트 앞에 잘못 된 문자를 무시 합니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_L** 접미사가 없는이 함수 버전은이 로캘 종속 동작에 현재 로캘을 사용 합니다. **_l** 접미사가 있는 버전은 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

입력 문자열이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **_MBC_ILLEGAL** 를 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 매니페스트 상수에 대해 반환 값으로 사용됩니다.

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[바이트 분류](../../c-runtime-library/byte-classification.md)<br/>
