---
title: _get_output_format | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
dev_langs:
- C++
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e34147c5d8990b9ec47f2a2b6ab3d2689190252
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065922"
---
# <a name="getoutputformat"></a>_get_output_format

출력 형식 플래그의 현재 값을 가져옵니다.

> [!IMPORTANT]
>  이 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>반환 값

출력 형식 플래그의 현재 값입니다.

## <a name="remarks"></a>설명

출력 형식 플래그는 형식이 지정된 I/O의 기능을 제어합니다. 현재 플래그는 두 가지 가능한 값인 0과 `_TWO_DIGIT_EXPONENT`를 사용합니다. `_TWO_DIGIT_EXPONENT` 가 설정된 경우 부동 소수점 숫자는 세 번째 숫자가 지수의 크기에 따라 필요한 경우가 아닌 한 지수에 두 자리 숫자로 인쇄됩니다. 플래그가 0이면 부동 소수점 출력은 필요한 경우 0을 사용하여 세 자리에 값을 채워 지수의 세 자리를 표시합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

호환성에 대한 자세한 내용은 소개 단원의 [호환성](../c-runtime-library/compatibility.md) 부분을 참조하세요.

## <a name="see-also"></a>참고 항목

[형식 사양 구문: printf 및 wprintf 함수](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
