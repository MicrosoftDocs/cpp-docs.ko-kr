---
description: '자세히 알아보기: btowc'
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: bbd6121499e03c356e80e49cbcbe75929ca96c2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171727"
---
# <a name="btowc"></a>btowc

초기 시프트 상태에서 정수가 유효한 싱글바이트 문자를 나타내는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>매개 변수

*character*<br/>
테스트할 정수입니다.

## <a name="return-value"></a>반환 값

초기 시프트 상태에서 정수가 유효한 싱글바이트 문자를 나타내는 경우 문자의 와이드 문자 표현을 반환합니다. 초기 시프트 상태에서 정수가 EOF이거나 유효한 싱글바이트 문자가 아닌 경우 WEOF를 반환합니다. 이 함수의 출력은 현재 **LC_TYPE** 로캘의 영향을 받습니다.

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**btowc**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
