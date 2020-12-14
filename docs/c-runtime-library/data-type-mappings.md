---
description: '자세한 정보: 데이터 형식 매핑'
title: 데이터 형식 매핑
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
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
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 9d76ecebc9bcb01e86cac2f199534ae2cda518c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258780"
---
# <a name="data-type-mappings"></a>데이터 형식 매핑

이러한 데이터 형식 매핑은 TCHAR.H에서 정의되고 상수 `_UNICODE` 또는 `_MBCS`가 프로그램에서 정의되었는지 여부에 따라 달라집니다.

관련 정보는 [_MBCS 코드와 TCHAR.H 데이터 형식 사용](../text/using-tchar-h-data-types-with-mbcs-code.md)을 참조하세요.

### <a name="generic-text-data-type-mappings"></a>일반 텍스트 데이터 형식 매핑

|일반 텍스트<br /><br /> 데이터 형식 이름|SBCS(_UNICODE,<br /><br /> _MBCS 정의되지<br /><br /> 않음)|_MBCS<br /><br /> 정의되는 위치|_UNICODE<br /><br /> 정의되는 위치|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` 또는 `_TEXT`|효과 없음(전처리기에 의해 제거됨)|효과 없음(전처리기에 의해 제거됨)|`L`(다음 문자 또는 문자열을 유니코드 문자 또는 문자열로 변환)|

## <a name="see-also"></a>참고 항목

[일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md)<br/>
[상수 및 전역 변수 매핑](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[루틴 매핑](../c-runtime-library/routine-mappings.md)<br/>
[샘플 Generic-Text 프로그램](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Generic-Text 매핑 사용](../c-runtime-library/using-generic-text-mappings.md)
