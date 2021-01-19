---
description: '자세히 알아보기: _scalb, _scalbf'
title: _scalb, _scalbf
ms.date: 1/15/2021
api_name:
- _scalb
- _scalbf
- _o__scalb
- _o__scalbf
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.openlocfilehash: da5a33bd6ed24ba0a3a58f789a9c8900910454d1
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564084"
---
# <a name="_scalb-_scalbf"></a>`_scalb`, `_scalbf`

2의 거듭제곱으로 인수의 크기를 조정합니다.

## <a name="syntax"></a>구문

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>매개 변수

*`x`*\
배정밀도, 부동 소수점 값입니다.

*`exp`*\
정수(Long) 지수입니다.

## <a name="return-value"></a>반환 값

성공하는 경우 지수 값을 반환합니다. 오버플로 시 (의 부호에 따라 *`x`* )는 **`_scalb`** +/-를 반환 합니다 **`HUGE_VAL`** **`errno`** . 변수는로 설정 됩니다 **`ERANGE`** .

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하십시오.

## <a name="remarks"></a>설명

**`_scalb`** 함수는 값 2를 계산 합니다 *`x`* \* <sup>*`exp`*</sup> .

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`_scalb`**, **`_scalbf`**|`<float.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`ldexp`](ldexp.md)