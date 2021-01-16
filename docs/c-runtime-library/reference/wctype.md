---
description: '자세히 알아보기: wctype'
title: wctype
ms.date: 1/14/2021
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.openlocfilehash: d0afd2bd163af967b11d0df58c84b62521ca6c2a
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242931"
---
# `wctype`

와이드 문자 코드에 대한 분류 규칙을 결정합니다.

## <a name="syntax"></a>구문

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>매개 변수

*`property`*\
속성 문자열입니다.

## <a name="return-value"></a>반환 값

**`LC_CTYPE`** 현재 로캘의 범주가 이름이 속성 문자열과 일치 하는 분류 규칙을 정의 하지 않는 경우 *`property`* 이 함수는 0을 반환 합니다. 그렇지 않으면에 대 한 후속 호출에 두 번째 인수로 사용 하기에 적합 한 0이 아닌 값을 반환 [`towctrans`](towctrans.md) 합니다.

## <a name="remarks"></a>설명

이 함수는 와이드 문자 코드에 대한 분류 규칙을 결정합니다. 다음 호출 쌍은 모든 로캘에서 동일하게 동작하지만 구현은 "C" 로캘에서도 추가 분류 규칙을 정의할 수 있습니다.

|함수|다음과 같이 사용|
|--------------|-------------|
|`iswalnum(c)`|`iswctype(c, wctype( "alnum" ))`|
|`iswalpha(c)`|`iswctype(c, wctype( "alpha" ))`|
|`iswcntrl(c)`|`iswctype(c, wctype( "cntrl" ))`|
|`iswdigit(c)`|`iswctype(c, wctype( "digit" ))`|
|`iswgraph(c)`|`iswctype(c, wctype( "graph" ))`|
|`iswlower(c)`|`iswctype(c, wctype( "lower" ))`|
|`iswprint(c)`|`iswctype(c, wctype( "print" ))`|
|`iswpunct(c)`|`iswctype(c, wctype( "punct" ))`|
|`iswspace(c)`|`iswctype(c, wctype( "space" ))`|
|`iswupper(c)`|`iswctype(c, wctype( "upper" ))`|
|`iswxdigit(c)`|`iswctype(c, wctype( "xdigit" ))`|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`wctype`|`<wctype.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)\
[`setlocale`, `_wsetlocale`](setlocale-wsetlocale.md)
