---
description: Mbrtoc16, mbrtoc32에 대해 자세히 알아보세요.
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 4132be867186567b31c9e297e6acb4ada68a66ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178617"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

문자열의 첫 번째 UTF-8 멀티 바이트 문자를 해당 하는 UTF-16 또는 UTF-32 문자로 변환 합니다.

## <a name="syntax"></a>구문

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
**`char16_t`** 변환할 utf-8 멀티 바이트 문자에 해당 하는 또는에 대 한 포인터 **`char32_t`** 입니다. Null 인 경우 함수는 값을 저장 하지 않습니다.

*원본*\
변환할 UTF-8 멀티 바이트 문자열에 대 한 포인터입니다.

*max_bytes*\
변환할 문자를 검사할 *소스의* 최대 바이트 수입니다. 이 인수는 *소스* 에서 남은 null 종결자를 포함 하 여 1에서 바이트 수 사이의 값 이어야 합니다.

*상태일*\
UTF-8 멀티 바이트 문자열을 하나 이상의 출력 문자로 해석 하는 데 사용 되는 **mbstate_t** 변환 상태 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

성공 하면 현재 *상태* 값이 지정 된 경우 적용 되는 이러한 조건 중 첫 번째 값을 반환 합니다.

|값|조건|
|-----------|---------------|
|0|*원본* 에서 변환 된 다음 *max_bytes* 이하의 문자는 null 와이드 문자에 해당 하며, *destination* 이 null이 아닌 경우 저장 되는 값입니다.<br /><br /> *상태* 에는 초기 이동 상태가 포함 됩니다.|
|1과 *max_bytes* 사이 (포함)|반환 되는 값은 유효한 멀티 바이트 문자를 완성 하는 *원본의* 바이트 수입니다. *대상이* null이 아닌 경우 변환 된 와이드 문자가 저장 됩니다.|
|-3|*대상이* null이 아닌 경우 함수에 대 한 이전 호출로 인해 발생 하는 다음 와이드 문자가 *대상* 에 저장 되었습니다. 이 함수 호출에서 *소스* 의 바이트를 사용 하지 않습니다.<br /><br /> *소스가* 둘 이상의 와이드 문자 (예: 서로게이트 쌍)를 나타내야 하는 utf-8 멀티 바이트 문자를 가리키는 경우 다음 함수 호출에서 추가 문자를 쓰도록 *상태* 값이 업데이트 됩니다.|
|-2|다음 *max_bytes* 바이트는 불완전 하지만 잠재적으로 유효한 utf-8 멀티 바이트 문자를 나타냅니다. *대상* 에는 값이 저장 되지 않습니다. 이 결과는 *max_bytes* 0 인 경우에 발생할 수 있습니다.|
|-1|인코딩 오류가 발생했습니다. 다음 *max_bytes* 이하의 바이트는 전체 및 유효한 utf-8 멀티 바이트 문자에 영향을 주지 않습니다. *대상* 에는 값이 저장 되지 않습니다.<br /><br /> **Eilseq** 가 **errno** 에 저장 되 고 변환 상태 값 *상태가* 지정 되지 않습니다.|

## <a name="remarks"></a>설명

**Mbrtoc16** 함수는 *원본* 에서 최대 *max_bytes* 바이트까지 읽어 첫 번째 완전 하 고 유효한 utf-8 멀티 바이트 문자를 찾은 다음 해당 하는 utf-16 문자를 *대상* 에 저장 합니다. 문자에서 서로게이트 쌍과 같은 둘 이상의 UTF-16 출력 문자가 필요한 경우 *상태* 값은 다음에 **mbrtoc16** 에 대 한 호출 시 *destination* 에 다음 utf-16 문자를 저장 하도록 설정 됩니다. **Mbrtoc32** 함수는 동일 하지만 출력이 u t f-32 문자로 저장 됩니다.

*Source* 가 null 인 경우 이러한 함수는 *대상* 에 **null** 인수를 사용 하는 호출에 해당 하는 호출 `""` (비어 있고 null로 끝나는 문자열) 및  *max_bytes* 에 대해 1을 반환 합니다. *대상* 및 *max_bytes* 전달 된 값은 무시 됩니다.

*Source* 가 null이 아닌 경우 함수는 문자열의 시작 부분에서 시작 하 고 최대 *max_bytes* 바이트까지 검사 하 여 모든 이동 시퀀스를 포함 하 여 다음 utf-8 멀티 바이트 문자를 완료 하는 데 필요한 바이트 수를 결정 합니다. 검사 된 바이트에 유효 하 고 완전 한 UTF-8 멀티 바이트 문자가 포함 된 경우이 함수는 문자를 해당 하는 16 비트 또는 32 비트 와이드 문자로 변환 합니다. *Destination* 이 null이 아닌 경우 함수는 대상에 첫 번째 (및 가능한 경우) 결과 문자를 저장 합니다. 추가 출력 문자가 필요한 경우에는 값이 *상태로* 설정 되므로 이후에 함수를 호출할 때 추가 문자가 출력 되 고 값-3이 반환 됩니다. 출력 문자가 더 이상 필요 하지 않으면 *state* 가 초기 이동 상태로 설정 됩니다.

비 UTF-8 멀티 바이트 문자를 UTF-16 LE 문자로 변환 하려면 [mbrtowc](mbrtowc.md), [mbtowc 또는 _mbtowc_l](mbtowc-mbtowc-l.md) 함수를 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

호환성에 대한 자세한 내용은 [Compatibility](../compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../data-conversion.md)\
[로캘을](../locale.md)\
[멀티 바이트 문자 시퀀스 해석](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
