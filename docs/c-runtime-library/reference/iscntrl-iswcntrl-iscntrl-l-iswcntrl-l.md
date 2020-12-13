---
description: Iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l에 대해 자세히 알아보세요.
title: iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l
ms.date: 4/2/2020
api_name:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
- _o_iscntrl
- _o_iswcntrl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
ms.openlocfilehash: b4dcba09b139d1ad1c80e495477a6b7b2283e3f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332706"
---
# <a name="iscntrl-iswcntrl-_iscntrl_l-_iswcntrl_l"></a>iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l

정수가 제어 문자를 나타내는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*C* 가 제어 문자의 특정 표현인 경우 이러한 각 루틴은 0이 아닌 값을 반환 합니다. *c* 가 제어 문자 (0X00-0X1F 또는 0x7f) 인 경우 **iscntrl** 는 0이 아닌 값을 반환 합니다. *c* 가 컨트롤 와이드 문자인 경우 **iswcntrl** 는 0이 아닌 값을 반환 합니다. *C* 가 테스트 조건을 충족 하지 않는 경우 이러한 루틴은 각각 0을 반환 합니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 로캘 대신 전달 된 로캘 매개 변수를 사용 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*C* 가 EOF가 아니거나 0에서 0xff 사이 (포함) 범위 내에 있는 경우 **iscntrl** 및 **_iscntrl_l** 의 동작이 정의 되지 않습니다. 디버그 CRT 라이브러리가 사용 되 고 *c* 가 이러한 값 중 하나가 아니면 함수는 어설션을 발생 시킵니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl**|**iscntrl**|**iscntrl**|**iswcntrl**|
|**_istcntrl_l**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**iscntrl**|\<ctype.h>|
|**iswcntrl**|\<ctype.h> 또는 \<wchar.h>|
|**_iscntrl_l**|\<ctype.h>|
|**_iswcntrl_l**|\<ctype.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
