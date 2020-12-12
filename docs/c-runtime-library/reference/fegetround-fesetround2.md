---
description: '다음에 대 한 자세한 정보: fegetround, fesetround'
title: fegetround, fesetround
ms.date: 04/05/2018
api_name:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
ms.openlocfilehash: f3c112efc1c380ac4ce4495f4365e2a47a1d8fd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322552"
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround

현재 부동 소수점 반올림 모드를 가져오거나 설정합니다.

## <a name="syntax"></a>구문

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>매개 변수

*round_mode*<br/>
부동 소수점 반올림 매크로 중 하나로 설정할 반올림 모드입니다. 값이 부동 소수점 반올림 매크로 중 하나와 같지 않은 경우 반올림 모드가 변경되지 않습니다.

## <a name="return-value"></a>반환 값

성공 하면 **fegetround** 는 반올림 모드를 부동 소수점 반올림 매크로 값 중 하나로 반환 합니다. 현재 반올림 모드를 확인할 수 없는 경우 음수 값이 반환됩니다.

성공할 경우 **fesetround** 는 0을 반환 합니다. 그렇지 않으면 0이 아닌 값이 반환됩니다.

## <a name="remarks"></a>설명

부동 소수점 연산에는 몇 가지 반올림 모드 중 하나를 사용할 수 있습니다. 이러한 모드에 따라 결과가 저장될 때 부동 소수점 연산의 결과가 반올림되는 방향이 제어됩니다. 다음은에 정의 된 부동 소수점 반올림 매크로의 이름 및 동작입니다 \<fenv.h> .

|매크로|설명|
|-----------|-----------------|
|FE_DOWNWARD|음의 무한대로 반올림합니다.|
|FE_TONEAREST|가장 가까운 값으로 반올림합니다.|
|FE_TOWARDZERO|0으로 반올림합니다.|
|FE_UPWARD|양의 무한대로 반올림합니다.|

FE_TONEAREST의 기본 동작은 표현 가능한 값의 중간 결과를 짝수(0) 최하위 비트를 갖는 가장 가까운 값으로 반올림하는 것입니다.

현재 반올림 모드는 다음 작업을 영향을 줍니다.

- 문자열 변환

- 상수 식 외부의 부동 소수점 산술 연산자 결과

- **Rint** 및 **nearbyint** 와 같은 라이브러리 반올림 함수입니다.

- 표준 라이브러리 수학 함수의 값을 반환합니다.

현재 반올림 모드는 다음 작업에 영향을 주지 않습니다.

- **Trunc**, **ceil**, **floor** 및 **lround** 라이브러리 함수

- 항상 0으로 반올림되는 부동 소수점-정수 암시적 캐스팅 및 변환

- 항상 가장 가까운 값으로 반올림되는 상수 식의 부동 소수점 산술 연산자 결과

이러한 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
