---
description: '다음에 대 한 자세한 정보: fegetenv'
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: f4d6ab3de440d2d8d7e145111339577f04699f8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322578"
---
# <a name="fegetenv"></a>fegetenv

지정된 개체에 현재 부동 소수점 환경을 저장합니다.

## <a name="syntax"></a>구문

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>매개 변수

*penv*<br/>
현재 부동 소수점 환경 값을 포함 하는 **fenv_t** 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

부동 소수점 환경이 *penv* 에 성공적으로 저장 된 경우 0을 반환 합니다. 그렇지 않으면 0이 아닌 값을 반환합니다.

## <a name="remarks"></a>설명

**Fegetenv** 함수는 *penv* 가 가리키는 개체에 현재 부동 소수점 환경을 저장 합니다. 부동 소수점 환경은 부동 소수점 계산에 영향을 미치는 상태 플래그 및 제어 모드의 집합입니다. 여기에는 부동 소수점 예외에 대한 상태 플래그와 반올림 방향 모드가 포함됩니다.  *Penv* 가 유효한 **fenv_t** 개체를 가리키지 않으면 후속 동작이 정의 되지 않습니다.

이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
