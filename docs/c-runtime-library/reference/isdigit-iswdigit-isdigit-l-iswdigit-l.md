---
description: '자세한 정보: isdigit, iswdigit, _isdigit_l, _iswdigit_l'
title: isdigit, iswdigit, _isdigit_l, _iswdigit_l
ms.date: 4/2/2020
api_name:
- _isdigit_l
- iswdigit
- _iswdigit_l
- isdigit
- _o_isdigit
- _o_iswdigit
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswdigit_l
- _isdigit_l
- iswdigit
- isdigit
- _istdigit
- _istdigit_l
helpviewer_keywords:
- iswdigit function
- iswdigit_l function
- _iswdigit_l function
- _istdigit_l function
- _istdigit function
- istdigit function
- isdigit function
- isdigit_l function
- _ismbcdigit_l function
- _isdigit_l function
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
ms.openlocfilehash: 3c0b2695f76a9dff1a4502e51938c428dc971fb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321102"
---
# <a name="isdigit-iswdigit-_isdigit_l-_iswdigit_l"></a>isdigit, iswdigit, _isdigit_l, _iswdigit_l

정수가 10진수 문자를 나타내는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int isdigit(
   int c
);
int iswdigit(
   wint_t c
);
int _isdigit_l(
   int c,
   _locale_t locale
);
int _iswdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*C* 가 10 진수 문자의 특정 표현인 경우 이러한 각 루틴은 0이 아닌 값을 반환 합니다. **isdigit** 는 *c* 가 10 진수 (0-9) 인 경우 0이 아닌 값을 반환 합니다. **iswdigit** 는 *c* 가 10 진수 문자에 해당 하는 와이드 문자인 경우 0이 아닌 값을 반환 합니다. *C* 가 테스트 조건을 충족 하지 않는 경우 이러한 루틴은 각각 0을 반환 합니다.

**_L** 접미사가 있는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘 대신 전달 된 로캘을 사용 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**Isdigit** 및 **_isdigit_l** 의 동작은 *c* 가 EOF가 아니거나 0에서 0xff 사이 (포함) 범위 내에 있는 경우 정의 되지 않습니다. 디버그 CRT 라이브러리가 사용 되 고 *c* 가 이러한 값 중 하나가 아니면 함수는 어설션을 발생 시킵니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istdigit**|**isdigit**|[_ismbcdigit](ismbcalnum-functions.md)|**iswdigit**|
|**_istdigit_l**|**_isdigit_l**|[_ismbcdigit_l](ismbcalnum-functions.md)|**_iswdigit_l**|

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**isdigit**|\<ctype.h>|
|**iswdigit**|\<ctype.h> 또는 \<wchar.h>|
|**_isdigit_l**|\<ctype.h>|
|**_iswdigit_l**|\<ctype.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
