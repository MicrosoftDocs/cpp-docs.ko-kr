---
description: '다음에 대 한 자세한 정보: _get_printf_count_output'
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: fe5ee728b7bc8400cd93ec4e93131496d59334c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339011"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

[Printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)family 함수가 **% n** 형식을 지원 하는지 여부를 나타냅니다.

## <a name="syntax"></a>구문

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Return Value

**% N** 이 (가) 지원 되는 경우 0이 아닙니다. **% n** 이 (가) 지원 되지 않는 경우 0입니다.

## <a name="remarks"></a>설명

**% N** 이 (가) 지원 되지 않는 경우 (기본값) **printf** 함수의 형식 문자열에서 **% n** 을 (를) 발생 하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. **% N** 지원이 사용 하도록 설정 된 경우 [(_set_printf_count_output](set-printf-count-output.md)참조) **% n** 은 (는) [형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)에 설명 된 대로 동작 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_set_printf_count_output](set-printf-count-output.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[_set_printf_count_output](set-printf-count-output.md)<br/>
