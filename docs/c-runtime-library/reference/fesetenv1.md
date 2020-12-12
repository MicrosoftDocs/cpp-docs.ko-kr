---
description: '다음에 대 한 자세한 정보: fesetenv'
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 662634e467eb224af813f60ab4434d4857d21d50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289441"
---
# <a name="fesetenv"></a>fesetenv

현재 부동 소수점 환경을 설정합니다.

## <a name="syntax"></a>구문

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>매개 변수

*penv*<br/>
[Fegetenv](fegetenv1.md) 또는 [feholdexcept](feholdexcept2.md)에 대 한 호출로 설정 된 부동 소수점 환경을 포함 하는 **fenv_t** 개체에 대 한 포인터입니다. **FE_DFL_ENV** 매크로를 사용 하 여 기본 시작 부동 소수점 환경을 지정할 수도 있습니다.

## <a name="return-value"></a>반환 값

환경이 성공적으로 설정된 경우 0을 반환합니다. 그렇지 않으면 0이 아닌 값을 반환합니다.

## <a name="remarks"></a>설명

**Fesetenv** 함수는 *penv* 가 가리키는 **fenv_t** 개체에 저장 된 값에서 현재 부동 소수점 환경을 설정 합니다. 부동 소수점 환경은 부동 소수점 계산에 영향을 미치는 상태 플래그 및 제어 모드의 집합입니다. 여기에는 부동 소수점 예외에 대한 상태 플래그와 반올림 모드가 포함됩니다.  *Penv* 가 **FE_DFL_ENV** 되지 않았거나 유효한 **fenv_t** 개체를 가리키지 않는 경우 후속 동작이 정의 되지 않습니다.

이 함수를 호출 하면 *penv* 개체에 있는 예외 상태 플래그가 설정 되지만 이러한 예외를 발생 시 키 지는 않습니다.

이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
