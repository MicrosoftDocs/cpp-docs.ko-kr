---
description: '자세한 정보: 로캘 범주'
title: 로캘 범주
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 2c6bfa4b2d1d0b76520043ee5568d51cf28a23c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246385"
---
# <a name="locale-categories"></a>로캘 범주

## <a name="syntax"></a>구문

```
#include <locale.h>
```

## <a name="remarks"></a>설명

로캘 범주는 지역화 루틴에서 사용할 프로그램 로캘 정보 부분을 지정하는 데 사용하는 매니페스트 상수입니다. 로캘은 프로그램의 특정 측면을 사용자 지정할 수 있는 지역성(또는 국가/지역)을 나타냅니다. 로캘 종속 영역에는 날짜 형식 지정 및 통화 값의 형식 표시 등이 포함됩니다.

|로캘 범주|영향을 받는 프로그램 부분|
|---------------------|-------------------------------|
|`LC_ALL`|모든 로캘 관련 동작(모든 범주)|
|`LC_COLLATE`|`strcoll` 및 `strxfrm` 함수의 동작|
|`LC_CTYPE`|문자 처리 함수(영향을 받지 않는 `isdigit`, `isxdigit`, `mbstowcs` 및 `mbtowc` 제외)의 동작|
|`LC_MAX`|`LC_TIME`과 동일|
|`LC_MIN`|`LC_ALL`과 동일|
|`LC_MONETARY`|`localeconv` 함수에 의해 반환되는 통화 서식 정보입니다.|
|`LC_NUMERIC`|서식이 지정된 출력 루틴(예: `printf`), 데이터 변환 루틴 및 `localeconv` 함수에 의해 반환된 비통화 서식 정보에 대한 소수점 문자입니다.|
|`LC_TIME`|`strftime` 함수의 동작|

예제에 대해서는 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll 함수](../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
