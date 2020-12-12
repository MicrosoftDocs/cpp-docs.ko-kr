---
description: '자세히 알아보기: feraiseexcept'
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 8e7a06006cfdc768fdaa306bc293857f1c375b90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124945"
---
# <a name="feraiseexcept"></a>feraiseexcept

지정된 부동 소수점 예외를 발생시킵니다.

## <a name="syntax"></a>구문

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>매개 변수

*제외한*<br/>
발생시킬 부동 소수점 예외입니다.

## <a name="return-value"></a>반환 값

모든 지정된 예외가 성공적으로 발생하면 0을 반환합니다.

## <a name="remarks"></a>설명

**Feraiseexcept** 함수는 *제외한* 로 지정 된 부동 소수점 예외를 발생 시 키 려 고 합니다.   **Feraiseexcept** 함수는에 정의 된 다음 예외 매크로를 지원 합니다 \<fenv.h> .

|예외 매크로|설명|
|---------------------|-----------------|
|FE_DIVBYZERO|초기 부동 소수점 작업에서 특이성 또는 극 오류가 발생했습니다. 무한대 값이 생성되었습니다.|
|FE_INEXACT|함수가 초기 부동 소수점 작업의 저장된 결과를 강제로 반올림했습니다.|
|FE_INVALID|초기 부동 소수점 작업에서 도메인 오류가 발생했습니다.|
|FE_OVERFLOW|범위 오류가 발생했습니다. 초기 부동 소수점 작업 결과가 표시하기에 너무 큽니다.|
|FE_UNDERFLOW|초기 부동 소수점 작업 결과가 완전히 정확하게 표시하기에 너무 작습니다. 비정상적인 값이 생성되었습니다.|
|FE_ALL_EXCEPT|모든 지원되는 부동 소수점 예외의 비트 OR입니다.|

*제외한* 인수는 0, 예외 매크로 값 중 하나 또는 지원 되는 예외 매크로 중 두 개 이상의 비트 or 일 수 있습니다. 지정된 예외 매크로 중 하나가 FE_OVERFLOW 또는 FE_UNDERFLOW이면 파생 작업으로 FE_INEXACT 예외가 발생할 수 있습니다.

이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

**Microsoft 전용:** *제외한* 에 지정 된 예외는 FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT 순서로 발생 합니다. 그러나 *제외한* 에 지정 되지 않은 경우에도 FE_OVERFLOW 또는 FE_UNDERFLOW 발생 하면 FE_INEXACT 발생할 수 있습니다.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
