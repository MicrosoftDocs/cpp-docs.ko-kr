---
description: C16rtomb, c32rtomb에 대해 자세히 알아보세요.
title: c16rtomb, c32rtomb
ms.date: 10/22/2019
api_name:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 35fb8f46693008cca9ee2a28e5b2656f009e4a6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171675"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

UTF-16 또는 u t f-32 와이드 문자를 UTF-8 멀티 바이트 문자로 변환 합니다.

## <a name="syntax"></a>구문

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>매개 변수

*mbchar*\
변환 된 UTF-8 멀티 바이트 문자를 저장할 배열에 대 한 포인터입니다.

*wchar*\
변환할 와이드 문자입니다.

*상태일*\
**Mbstate_t** 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

배열 개체 *mbchar* 에 저장 된 바이트 수 (이동 시퀀스 포함)입니다. *Wchar* 가 유효한 와이드 문자가 아닌 경우 값 (**size_t**) (-1)이 반환 되 고 **errno** 가 **eilseq** 로 설정 되 고 *상태* 값이 지정 되지 않습니다.

## <a name="remarks"></a>설명

**C16rtomb** 함수는 utf-16 LE 문자 *wchar* 를 해당 하는 utf-8 멀티 바이트 좁은 문자 시퀀스로 변환 합니다. *Mbchar* 가 null 포인터가 아닌 경우 함수는 *mbchar* 가 가리키는 배열 개체에 변환 된 시퀀스를 저장 합니다. 최대 **MB_CUR_MAX** 바이트는 *mbchar* 에 저장 되 고 *상태* 는 결과 멀티 바이트 이동 상태로 설정 됩니다.

*Wchar* 가 null 와이드 문자인 경우 초기 이동 상태를 복원 하는 데 필요한 시퀀스가 저장 되 고, 필요한 경우 null 문자가 뒤에 저장 됩니다. *상태* 는 초기 변환 상태로 설정 됩니다. **C32rtomb** 함수는 동일 하지만, 32 문자를 변환 합니다.

*Mbchar* 가 null 포인터인 경우 동작은 *mbchar* 에 대 한 내부 버퍼와 *wchar* 의 와이드 null 문자를 대체 하는 함수 호출과 동일 합니다.

*상태* 변환 상태 개체를 사용 하면이 함수 및 멀티 바이트 출력 문자의 이동 상태를 유지 하는 다시 시작 가능한 다른 함수에 대해 후속 호출을 수행할 수 있습니다. 다시 시작 가능 및 다시 시작 불가능 함수의 사용을 혼합 하는 경우 결과가 정의 되지 않습니다.

UTF-16 문자를 비 UTF-8 멀티 바이트 문자로 변환 하려면 [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md), [wcstombs_s 또는 _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) 함수를 사용 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C + +: \<uchar.h>|

호환성에 대한 내용은 [호환성](../compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../data-conversion.md)\
[로캘을](../locale.md)\
[멀티 바이트 문자 시퀀스 해석](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
