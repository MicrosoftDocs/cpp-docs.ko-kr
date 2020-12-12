---
description: '다음에 대 한 자세한 정보: __setusermatherr'
title: __setusermatherr
ms.date: 11/04/2016
api_name:
- __setusermatherr
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __setusermatherr
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
ms.openlocfilehash: 11b470f3c39a22b212187936dc4bad36c3cefd1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277079"
---
# <a name="__setusermatherr"></a>__setusermatherr

[_matherr](../c-runtime-library/reference/matherr.md) 루틴 대신 수학 오류를 처리하기 위한 사용자 제공 루틴을 지정합니다.

## <a name="syntax"></a>구문

```cpp
void __setusermatherr(
   _HANDLE_MATH_ERROR pf
   )
```

#### <a name="parameters"></a>매개 변수

*pf*<br/>
사용자가 제공하는 `_matherr`의 구현에 대한 포인터입니다.

*pf* 매개 변수의 형식은 `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`로 선언됩니다.

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__setusermatherr|matherr.c|
