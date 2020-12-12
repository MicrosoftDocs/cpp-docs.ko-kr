---
description: '자세한 정보: toascii, __toascii'
title: toascii, __toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 9f1718da5e7d701bb6cc6ea68c1e21b6fe4283f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318353"
---
# <a name="toascii-__toascii"></a>toascii, __toascii

잘라내기를 통해 문자를 7비트 ASCII로 변환합니다.

## <a name="syntax"></a>구문

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>매개 변수

*c*<br/>
변환할 문자입니다.

## <a name="return-value"></a>반환 값

**__toascii** *c* 의 값을 7 비트 ASCII 범위로 변환 하 고 결과를 반환 합니다. 오류를 나타내기 위해 예약된 반환 값은 없습니다.

## <a name="remarks"></a>설명

**__Toascii** 루틴은 지정 된 문자를 하위 7 비트로 잘라 ASCII 문자로 변환 합니다. 다른 변환은 적용되지 않습니다.

전처리기 매크로 _CTYPE_DISABLE_MACROS 정의 되어 있지 않으면 **__toascii** 루틴은 매크로로 정의 됩니다. 이전 버전과의 호환성을 위해 **toascii** 는 [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) 정의 되지 않았거나 0으로 정의 된 경우에만 매크로로 정의 됩니다. 그렇지 않으면 정의 되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**toascii**, **__toascii**|C \<ctype.h><br /><br /> C + +: \<cctype> 또는 \<ctype.h>|

**Toascii** 매크로는 posix 확장 이며 **__toascii** 은 posix 확장의 Microsoft 관련 구현입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
[to 함수](../../c-runtime-library/to-functions.md)<br/>
