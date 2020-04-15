---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343919"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

특정 문자가 ASCII 문자인지 여부를 결정합니다.

## <a name="syntax"></a>구문

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>매개 변수

*C*<br/>
테스트할 정수입니다.

## <a name="return-value"></a>Return Value

**c가** ASCII 문자의 특정 표현인 경우 이러한 각 루틴은 영하지 않은 루틴을 반환합니다. **__isascii** **c가** ASCII 문자인 경우 비영값을 반환합니다(범위 0x00 - 0x7F). **iswascii** **는 c가** ASCII 문자의 넓은 문자 표현인 경우 비영도 값을 반환합니다. **c가** 테스트 조건을 충족하지 않는 경우 이러한 각 루틴은 0을 반환합니다.

## <a name="remarks"></a>설명

**__isascii** **iswasci는** 프로세서 _CTYPE_DISABLE_MACROS 정의되지 않는 한 매크로로 구현됩니다.

이전 버전과의 호환성을 위해 **isascii는** [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) 정의되지 않았거나 0으로 정의된 경우에만 매크로로 구현됩니다. 그렇지 않으면 정의되지 않습니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**이사시**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> 또는 \<ctype.h>|
|**iswascii**|C: \<wctype.h>, \<ctype.h> 또는 \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> 또는 \<wchar.h>|

**isascii,** **__isascii** 및 **iswascii** 함수는 Microsoft에 특정합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
