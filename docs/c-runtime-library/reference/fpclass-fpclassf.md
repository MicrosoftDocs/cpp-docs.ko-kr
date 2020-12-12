---
description: '자세히 알아보기: _fpclass, _fpclassf'
title: _fpclass, _fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: bd7a2aa02a3431ff41c4d9695efca1f959ece24f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164915"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

인수의 부동 소수점 분류를 나타내는 값을 반환합니다.

## <a name="syntax"></a>구문

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>매개 변수

*x*<br/>
테스트할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**_Fpclass** 및 **_fpclassf** 함수는 인수 *x* 의 부동 소수점 분류를 나타내는 정수 값을 반환 합니다. 분류는에 정의 된 다음 값 중 하나를 가질 수 있습니다 \<float.h> .

|값|설명|
|-----------|-----------------|
|**_FPCLASS_SNAN**|신호 NaN|
|**_FPCLASS_QNAN**|자동 NaN|
|**_FPCLASS_NINF**|음의 무한대 (-INF)|
|**_FPCLASS_NN**|정규화된 0이 아닌 음수 값|
|**_FPCLASS_ND**|비정규화된 음수|
|**_FPCLASS_NZ**|음수 0 (-0)|
|**_FPCLASS_PZ**|양수 0(+0)|
|**_FPCLASS_PD**|비정규화된 양수|
|**_FPCLASS_PN**|정규화된 0이 아닌 양수 값|
|**_FPCLASS_PINF**|양수 무한대(+INF)|

## <a name="remarks"></a>설명

**_Fpclass** 및 **_Fpclassf** 함수는 Microsoft 전용입니다. [fpclassify](fpclassify.md)와 비슷하지만 인수에 대한 더 자세한 정보를 반환합니다. **_Fpclassf** 함수는 x64 플랫폼용으로 컴파일된 경우에만 사용할 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

호환성 및 규칙에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
