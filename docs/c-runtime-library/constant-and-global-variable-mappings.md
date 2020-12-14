---
description: '자세한 정보: 상수 및 전역 변수 매핑'
title: 상수 및 전역 변수 매핑
ms.date: 11/04/2016
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
ms.openlocfilehash: 6078564a5f9d6ef28de704f4991264b5de58041b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195764"
---
# <a name="constant-and-global-variable-mappings"></a>상수 및 전역 변수 매핑

이러한 일반 텍스트 상수, 전역 변수 및 표준 형식 매핑은 TCHAR.H에서 정의되며, 상수 `_UNICODE` 또는 `_MBCS`가 프로그램에서 정의되었는지 여부에 따라 달라집니다.

### <a name="generic-text-constant-and-global-variable-mappings"></a>일반 텍스트 상수 및 전역 변수 매핑

|일반 텍스트 - 개체 이름|SBCS(_UNICODE 및 MBCS가 정의되지 않음)|_MBCS 정의됨|_UNICODE 정의됨|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>참고 항목

[일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md)<br/>
[데이터 형식 매핑](../c-runtime-library/data-type-mappings.md)<br/>
[루틴 매핑](../c-runtime-library/routine-mappings.md)<br/>
[샘플 Generic-Text 프로그램](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Generic-Text 매핑 사용](../c-runtime-library/using-generic-text-mappings.md)
