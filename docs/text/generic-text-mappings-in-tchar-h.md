---
description: '자세한 정보: tchar.h의 Generic-Text 매핑'
title: Tchar.h의 Generic-Text 매핑
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: f083dc03eab7db25b54955d8d34a13f2b5b7197b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118350"
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar.h의 Generic-Text 매핑

Microsoft 런타임 라이브러리는 국가별 사용을 위해 코드를 전송 하는 과정을 간소화 하기 위해 다양 한 데이터 형식, 루틴 및 기타 개체에 대 한 Microsoft 고유의 일반 텍스트 매핑을 제공 합니다. Tchar.h에 정의 된 이러한 매핑을 사용 하 여 문을 사용 하 여 정의 하는 매니페스트 상수에 따라 싱글바이트, 멀티 바이트 또는 유니코드 문자 집합에 대해 컴파일할 수 있는 제네릭 코드를 작성할 수 있습니다 `#define` . 제네릭 텍스트 매핑은 ANSI와 호환되지 않는 Microsoft 확장입니다.

Tchar.h를 사용 하면 동일한 소스에서 단일 바이트, MBCS (멀티 바이트 문자 집합) 및 유니코드 응용 프로그램을 빌드할 수 있습니다. tchar.h는 접두사를 포함 하는 매크로를 정의 합니다 .이는 `_tcs` 올바른 전처리기 정의를 사용 하 여 `str` , `_mbs` 또는 함수를 적절 하 게 매핑합니다 `wcs` . MBCS를 빌드하려면 기호를 정의 `_MBCS` 합니다. 유니코드를 빌드하려면 기호를 정의 `_UNICODE` 합니다. 싱글바이트 응용 프로그램을 빌드하려면 (기본값)를 정의 하지 않습니다. 기본적으로 `_UNICODE` 는 MFC 응용 프로그램에 대해 정의 됩니다.

`_TCHAR`데이터 형식은 tchar.h에 조건부로 정의 됩니다. 기호가 `_UNICODE` 빌드에 대해 정의 된 경우 `_TCHAR` 은로 정의 되 고, **`wchar_t`** 그렇지 않으면 싱글바이트 및 MBCS 빌드의 경우로 정의 됩니다 **`char`** . **`wchar_t`** 기본 유니코드 와이드 문자 데이터 형식이 며 8 비트에 해당 하는 16 비트입니다 **`signed char`** . 국가별 응용 프로그램의 경우 `_tcs` 바이트가 아닌 단위로 작동 하는 함수 패밀리를 사용 합니다 `_TCHAR` . 예를 들어, `_tcsncpy` 바이트는 복사 `n` `_TCHARs` 하지 않습니다 `n` .

일부 SBCS (싱글바이트 문자 집합) 문자열 처리 함수는 (부호 있는) 매개 변수를 사용 하기 때문에 **`char*`** 가 정의 되 면 형식이 일치 하지 않는다는 컴파일러 경고가 발생 `_MBCS` 합니다. 이 경고를 방지 하는 방법에는 다음 세 가지가 있습니다.

1. Tchar.h에 형식이 안전한 인라인 함수 썽크를 사용 합니다. 이것은 기본적인 동작입니다.

1. 명령줄에서를 정의 하 여 tchar.h에서 직접 매크로를 사용 `_MB_MAP_DIRECT` 합니다. 이렇게 하는 경우 형식을 수동으로 일치시켜야 합니다. 이는 가장 빠른 방법 이지만 형식이 안전 하지 않습니다.

1. Tchar.h에 형식이 안전한 정적 연결 라이브러리 함수 썽크를 사용 합니다. 이렇게 하려면 명령줄에서 `_NO_INLINING` 상수를 정의합니다. 이는 속도가 가장 느린 방법이지만 형식은 가장 안전합니다.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>일반 텍스트 매핑용 전처리기 지시문

|# define|컴파일 버전|예제|
|---------------|----------------------|-------------|
|`_UNICODE`|유니코드(와이드 문자)|`_tcsrev`는 `_wcsrev`에 매핑됩니다.|
|`_MBCS`|멀티바이트 문자|`_tcsrev`는 `_mbsrev`에 매핑됩니다.|
|없음 (기본값은 또는 정의 되어 있지 않음 `_UNICODE` `_MBCS` )|SBCS(ASCII)|`_tcsrev`는 `strrev`에 매핑됩니다.|

예를 들어 tchar.h에 정의 된 일반 텍스트 함수는 `_tcsrev` 프로그램에서 정의한 경우에 매핑되고,를 `_mbsrev` `_MBCS` `_wcsrev` 정의한 경우에는로 매핑됩니다 `_UNICODE` . 그렇지 않으면 `_tcsrev`는 `strrev`로 매핑됩니다. 다른 데이터 형식 매핑은 프로그래밍 편의를 위해 tchar.h에 제공 되지만 `_TCHAR` 가장 유용 합니다.

### <a name="generic-text-data-type-mappings"></a>일반 텍스트 데이터 형식 매핑

|Generic-Text<br /> 데이터 형식 이름|_UNICODE &<br /> _MBCS 정의 되지 않음|_MBCS<br /> 정의됨|_UNICODE<br /> 정의됨|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`unsigned int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` 또는 `_TEXT`|효과 없음(전처리기에 의해 제거됨)|효과 없음(전처리기에 의해 제거됨)|`L` 다음 문자 또는 문자열을 해당 유니코드로 변환 합니다.|

루틴, 변수 및 기타 개체의 일반 텍스트 매핑 목록은 Run-Time 라이브러리 참조에서 [일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md) 을 참조 하세요.

> [!NOTE]
> `str`포함 된 null 바이트를 포함할 수 있는 유니코드 문자열과 함수 패밀리를 사용 하지 마세요. 마찬가지로 `wcs` MBCS (또는 SBCS) 문자열과 함께 함수 패밀리를 사용 하지 마십시오.

다음 코드 조각은 MBCS, 유니코드 및 SBCS 모델에 매핑하는 데 `_TCHAR` 및 `_tcsrev`를 사용하는 방법을 보여 줍니다.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

`_MBCS`가 정의 된 경우 전처리기는이 조각을 다음 코드에 매핑합니다.

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

`_UNICODE`가 정의 된 경우 전처리기는이 조각을 다음 코드에 매핑합니다.

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

`_MBCS`및가 둘 다 `_UNICODE` 정의 되지 않은 경우 전처리기는 다음과 같이 조각을 싱글바이트 ASCII 코드에 매핑합니다.

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

따라서 세 가지 종류의 문자 집합 중 하 나와 관련 된 루틴을 사용 하 여 실행할 단일 소스 코드 파일을 작성 하 고, 유지 관리 하 고, 컴파일할 수 있습니다.

## <a name="see-also"></a>참고 항목

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)<br/>
[TCHAR.H 사용. _MBCS 코드를 포함 하는 H 데이터 형식](../text/using-tchar-h-data-types-with-mbcs-code.md)
