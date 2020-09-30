---
title: 일반 텍스트 매핑 사용
description: C 런타임의 데이터 형식, 루틴 및 기타 개체에 대 한 Microsoft 관련 매핑을 소개 합니다.
ms.topic: conceptual
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: ea3b1eef413a0d9f52e81795c04424d533b83504
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590110"
---
# <a name="using-generic-text-mappings"></a>일반 텍스트 매핑 사용

**Microsoft 전용**

Microsoft 런타임 라이브러리는 다양한 해외 시장을 겨냥하여 코드 개발을 간소화하기 위해 다양한 데이터 형식, 루틴 및 기타 개체에 대해 Microsoft 전용 "일반 텍스트" 매핑을 제공합니다. 이러한 매핑은 TCHAR.H에 정의됩니다. 이러한 이름 매핑을 사용하면 `#define` 문을 사용하여 정의하는 매니페스트 상수에 따라, 세 가지 종류의 문자 집합, 즉 ASCII(SBCS), MBCS 또는 유니코드용으로 컴파일할 수 있는 일반 코드를 쓸 수 있습니다. 제네릭 텍스트 매핑은 ANSI와 호환되지 않는 Microsoft 확장입니다.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>일반 텍스트 매핑용 전처리기 지시문

|#define|컴파일 버전|예제|
|--------------|----------------------|-------------|
|`_UNICODE`|유니코드(와이드 문자)|`_tcsrev`는 `_wcsrev`에 매핑됩니다.|
|`_MBCS`|멀티바이트 문자|`_tcsrev`는 `_mbsrev`에 매핑됩니다.|
|없음(기본값: `_UNICODE` 및 `_MBCS` 둘 다 정의되지 않음)|SBCS(ASCII)|`_tcsrev`는 `strrev`에 매핑됩니다.|

예를 들어 TCHAR.H에 정의된 일반 텍스트 함수인 `_tcsrev`는 프로그램에 `MBCS`가 정의된 경우에는 `mbsrev`로 매핑되고, `_UNICODE`가 정의된 경우에는 `_wcsrev`로 매핑됩니다. 그렇지 않으면 `_tcsrev`는 `strrev`로 매핑됩니다.

`_TCHAR`Tchar.h에 정의 된 일반 텍스트 데이터 형식입니다. H는가 정의 된 경우 형식에 매핑되고, **`char`** `_MBCS` 가 정의 된 경우에는 형식으로 매핑되고, **`wchar_t`** `_UNICODE` **`char`** 상수가 정의 되어 있지 않으면를 입력 합니다. 프로그래밍 편의를 위해 다른 데이터 형식 매핑이 TCHAR.H에 제공되지만 `_TCHAR`이 가장 유용한 형식입니다.

### <a name="generic-text-data-type-mappings"></a>일반 텍스트 데이터 형식 매핑

|일반 텍스트 데이터 형식 이름|SBCS(_UNICODE 및 MBCS가 정의되지 않음)|_MBCS 정의됨|_UNICODE 정의됨|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` 또는 `_TEXT`|효과 없음(전처리기에 의해 제거됨)|효과 없음(전처리기에 의해 제거됨)|`L`(다음 문자 또는 문자열을 유니코드 문자 또는 문자열로 변환)|

루틴, 변수 및 기타 개체의 일반 텍스트 매핑에 대한 전체 목록을 보려면 [일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md)을 참조하세요.

다음 코드 조각은 MBCS, 유니코드 및 SBCS 모델에 매핑하는 데 `_TCHAR` 및 `_tcsrev`를 사용하는 방법을 보여 줍니다.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

`MBCS`가 정의되면 전처리기는 위 조각을 다음 코드에 매핑합니다.

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

`_UNICODE`가 정의되면 전처리기는 같은 조각을 다음 코드에 매핑합니다.

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

`_MBCS` 또는 `_UNICODE`가 둘 다 정의되지 않은 경우 전처리기는 다음과 같이 해당 조각을 싱글바이트 ASCII 코드에 매핑합니다.

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

따라서 이러한 세 가지 종류의 문자 집합과 관련된 루틴에서 실행할 단일 소스 코드 파일을 작성하고, 유지하고, 컴파일할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md)<br/>
[데이터 형식 매핑](../c-runtime-library/data-type-mappings.md)<br/>
[상수 및 전역 변수 매핑](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[루틴 매핑](../c-runtime-library/routine-mappings.md)<br/>
[샘플 일반 텍스트 프로그램](../c-runtime-library/a-sample-generic-text-program.md)
