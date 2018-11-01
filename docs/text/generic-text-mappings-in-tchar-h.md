---
title: Tchar.h의 제네릭 텍스트 매핑
ms.date: 11/04/2016
f1_keywords:
- tchar.h
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: 969894502689dd5aeeeaa27404bafc3c483c1336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667586"
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar.h의 제네릭 텍스트 매핑

전송을 단순화 하기 위해 전 세계에서 사용 하는 코드를 Microsoft 런타임 라이브러리는 많은 데이터 형식, 루틴 및 다른 개체에 대 한 Microsoft 특정 일반 텍스트 매핑을 제공 합니다. 싱글바이트 멀티 바이트에 대해 컴파일할 수 있는 일반 코드를 쓸 Tchar.h에 정의 된 이러한 매핑을 사용 하 여 또는 유니코드 문자 집합을 사용 하 여 정의 하는 매니페스트 상수에 따라는 `#define` 문입니다. 제네릭 텍스트 매핑은 ANSI와 호환되지 않는 Microsoft 확장입니다.

Tchar.h를 사용 하 여 단일 바이트, 멀티 바이트 문자 집합 (MBCS) 및 동일한 원인에서 유니코드 응용 프로그램을 빌드할 수 있습니다. Tchar.h 매크로 정의 (접두사를 포함 하는 `_tcs`) 매핑되는 올바른 전처리기 정의 사용 하 여 `str`를 `_mbs`, 또는 `wcs` 함수를 적절 하 게 합니다. MBCS를 빌드하려면 기호를 정의 `_MBCS`합니다. 유니코드를 빌드하려면 기호를 정의 `_UNICODE`합니다. 싱글바이트 응용 프로그램을 빌드하려면 모두 (기본값)을 정의 합니다. 기본적으로 `_MBCS` MFC 응용 프로그램에 대해 정의 됩니다.

`_TCHAR` tchar.h에서 데이터 형식 조건에 따라 정의 됩니다. 경우 기호 `_UNICODE` 하는 빌드에 대해 정의 된 `_TCHAR` 란 **wchar_t**고, 그렇지 않으면로 정의 된 싱글바이트 및 MBCS 빌드에 대 한 **char**합니다. (**wchar_t**, 기본 유니코드 와이드 문자 데이터 형식에는 8 비트 부호 있는 16 비트 누구 **char**.) 국가별 응용 프로그램을 사용 합니다 `_tcs` 작동 하는 함수 패밀리 `_TCHAR` 단위, 바이트가 아닌 합니다. 예를 들어 `_tcsncpy` 복사본 `n` `_TCHARs`아니라 `n` 바이트입니다.

일부 단일 바이트 문자 집합 (SBCS) 문자열 처리 함수는 (signed) 때문 `char*` 매개 변수, 형식 불일치 컴파일러 경고 발생 경우 `_MBCS` 정의 됩니다. 이 경고를 방지 하는 방법은 세 가지가 있습니다.

1. Tchar.h에 형식이 안전한 인라인 함수 썽크가 사용 합니다. 이것은 기본적인 동작입니다.

1. Tchar.h에 직접 매크로 사용 하 여 정의 하 여 `_MB_MAP_DIRECT` 명령줄에서. 이렇게 하는 경우 형식을 수동으로 일치시켜야 합니다. 가장 빠른 방법 이지만 형식이 안전 하지 않습니다.

1. Tchar.h에 형식이 안전한 정적 링크 라이브러리 함수 썽크를 사용 합니다. 이렇게 하려면 명령줄에서 `_NO_INLINING` 상수를 정의합니다. 이는 속도가 가장 느린 방법이지만 형식은 가장 안전합니다.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>일반 텍스트 매핑용 전처리기 지시문

|# 정의|컴파일 버전|예제|
|---------------|----------------------|-------------|
|`_UNICODE`|유니코드(와이드 문자)|`_tcsrev`는 `_wcsrev`에 매핑됩니다.|
|`_MBCS`|멀티바이트 문자|`_tcsrev`는 `_mbsrev`에 매핑됩니다.|
|None (기본값에 둘 다 `_UNICODE` 나 `_MBCS` 정의)|SBCS(ASCII)|`_tcsrev`는 `strrev`에 매핑됩니다.|

예를 들어 제네릭 텍스트 함수인 `_tcsrev`, Tchar.h에 정의 되어 있는 매핑되 `_mbsrev` 정의한 경우 `_MBCS` 또는 프로그램에 `_wcsrev` 정의한 경우 `_UNICODE`합니다. 그렇지 않으면 `_tcsrev`는 `strrev`로 매핑됩니다. 프로그래밍 편의 위해 다른 데이터 형식 매핑이 Tchar.h에 제공 되지만 `_TCHAR` 가장 유용 합니다.

### <a name="generic-text-data-type-mappings"></a>일반 텍스트 데이터 형식 매핑

|일반 텍스트<br /> 데이터 형식 이름|_UNICODE &AMP;<br /> _MBCS 정의 되지 않음|_MBCS<br /> 정의됨|_UNICODE<br /> 정의됨|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**서명 된 char**|**서명 된 char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` 또는 `_TEXT`|효과 없음(전처리기에 의해 제거됨)|효과 없음(전처리기에 의해 제거됨)|`L` (유니코드 문자에는 다음 문자 또는 문자열 변환)|

루틴, 변수 및 기타 개체의 제네릭 텍스트 매핑의 목록을 참조 하세요 [일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md) 런타임 라이브러리 참조에서 합니다.

> [!NOTE]
>  사용 하지 마십시오는 `str` 포함할 수 있는 유니코드 문자열을 사용 하 여 함수 패밀리를 null 바이트를 포함 합니다. 마찬가지로, 사용 하지 마십시오는 `wcs` MBCS (또는 SBCS) 문자열을 사용 하 여 함수의 제품군입니다.

다음 코드 조각은 MBCS, 유니코드 및 SBCS 모델에 매핑하는 데 `_TCHAR` 및 `_tcsrev`를 사용하는 방법을 보여 줍니다.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

경우 `_MBCS` 되었습니다 정의 된 전처리기가이 조각에 매핑됩니다이 코드:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

경우 `_UNICODE` 되었습니다 정의 된 전처리기가이 조각에 매핑됩니다이 코드:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

모두 `_MBCS` 나 `_UNICODE` 되었습니다 정의 전처리기 매핑되 조각을 싱글바이트 ASCII 코드를 다음과 같이 합니다.

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

따라서 작성할 수 있습니다. 유지 관리 및 실행 문자 집합의 세 가지 종류 중 하나에 관련 된 루틴을 사용 하 여 단일 소스 코드 파일을 컴파일하십시오.

## <a name="see-also"></a>참고 항목

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)<br/>
[_MBCS 코드와 TCHAR.H 데이터 형식 사용](../text/using-tchar-h-data-types-with-mbcs-code.md)