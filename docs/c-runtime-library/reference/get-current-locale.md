---
description: '다음에 대 한 자세한 정보: _get_current_locale'
title: _get_current_locale
ms.date: 11/04/2016
api_name:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: 672914875aebbe020fbfab0c4958ce2963958432
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341492"
---
# <a name="_get_current_locale"></a>_get_current_locale

현재 로캘을 나타내는 로캘 개체를 가져옵니다.

## <a name="syntax"></a>구문

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Return Value

현재 로캘을 나타내는 로캘 개체입니다.

## <a name="remarks"></a>설명

**_Get_current_locale** 함수는 스레드에 대해 현재 설정 된 로캘을 가져오고 해당 로캘을 나타내는 로캘 개체를 반환 합니다.

이 함수의 이전 이름인 **__get_current_locale** (선행 밑줄 두 개 포함)은 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
