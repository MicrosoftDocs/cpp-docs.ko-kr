---
description: '자세히 알아보기: wctype'
title: wctype
ms.date: 11/04/2016
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: 0791d4f048dfa5d6804db14d577b1370ffbf8754
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254198"
---
# <a name="wctype"></a>wctype

와이드 문자 코드에 대한 분류 규칙을 결정합니다.

## <a name="syntax"></a>구문

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>매개 변수

*property*<br/>
속성 문자열입니다.

## <a name="return-value"></a>반환 값

현재 로캘의 **LC_CTYPE** 범주가 이름이 속성 문자열 *속성과* 일치 하는 분류 규칙을 정의 하지 않는 경우이 함수는 0을 반환 합니다. 그렇지 않으면 이 함수는 [towctrans](towctrans.md)에 대한 후속 호출에 두 번째 인수로 사용할 수 있는 0이 아닌 값을 반환합니다.

## <a name="remarks"></a>설명

이 함수는 와이드 문자 코드에 대한 분류 규칙을 결정합니다. 다음 호출 쌍은 모든 로캘에서 동일하게 동작하지만 구현은 "C" 로캘에서도 추가 분류 규칙을 정의할 수 있습니다.

|함수|다음과 같이 사용|
|--------------|-------------|
|iswalnum (c)|iswctype (c, wctype ("alnum"))|
|iswalpha (c)|iswctype (c, wctype ("alpha"))|
|iswcntrl (c)|iswctype (c, wctype ("cntrl"))|
|iswdigit (c)|iswctype (c, wctype ("digit"))|
|iswgraph (c)|iswctype (c, wctype ("graph"))|
|iswlower (c)|iswctype (c, wctype ("lower"))|
|iswprint (c)|iswctype (c, wctype ("print"))|
|iswpunct (c)|iswctype (c, wctype ("punct"))|
|iswspace (c)|iswctype (c, wctype ("space"))|
|iswupper (c)|iswctype (c, wctype ("upper"))|
|iswxdigit (c)|iswctype (c, wctype ("xdigit"))|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
