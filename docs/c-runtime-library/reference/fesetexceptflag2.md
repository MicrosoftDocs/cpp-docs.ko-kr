---
title: fesetexceptflag
ms.date: 04/05/2018
apiname:
- fesetexceptflag
apilocation:
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
apitype: DLLExport
f1_keywords:
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: 9ac79e790f0b1e7a89413a0d4974f6053c95616e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615880"
---
# <a name="fesetexceptflag"></a>fesetexceptflag

현재 부동 소수점 환경에서 지정된 부동 소수점 상태 플래그를 설정합니다.

## <a name="syntax"></a>구문

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>매개 변수

*pstatus*<br/>
에 대 한 포인터를 **fexcept_t** 예외 상태 플래그를 설정할 값이 들어 있는 개체입니다. 개체는 [fegetexceptflag](fegetexceptflag2.md)에 대한 이전 호출을 통해 설정될 수 있습니다.

*제외한*<br/>
설정할 부동 소수점 예외 상태 플래그입니다.

## <a name="return-value"></a>반환 값

모든 지정된 예외 상태 플래그가 성공적으로 설정되면 0을 반환합니다. 그렇지 않으면 0이 아닌 값을 반환합니다.

## <a name="remarks"></a>설명

**fesetexceptflag** 함수에 지정 된 부동 소수점 예외 상태 플래그의 상태를 설정 합니다. *제외한* 설정 된 해당 값을 **fexcept_t** 개체에서 가리키는 *pstatus*합니다.  이 함수는 예외를 발생시키지 않습니다. 합니다 *pstatus* 유효한 포인터를 가리켜야 **fexcept_t** 개체 또는 후속 동작이 정의 되지 않습니다. 합니다 **fesetexceptflag** 함수에서 다음 예외 매크로 값을 지 원하는 *제외한*에 정의 된 \<n v. h >:

|예외 매크로|설명|
|---------------------|-----------------|
|FE_DIVBYZERO|초기 부동 소수점 작업에서 특이성 또는 극 오류가 발생했습니다. 무한대 값이 생성되었습니다.|
|FE_INEXACT|함수가 초기 부동 소수점 작업의 저장된 결과를 강제로 반올림했습니다.|
|FE_INVALID|초기 부동 소수점 작업에서 도메인 오류가 발생했습니다.|
|FE_OVERFLOW|범위 오류가 발생했습니다. 초기 부동 소수점 작업 결과가 표시하기에 너무 큽니다.|
|FE_UNDERFLOW|초기 부동 소수점 작업 결과가 완전히 정확하게 표시하기에 너무 작습니다. 비정상적인 값이 생성되었습니다.|
|FE_ALLEXCEPT|모든 지원되는 부동 소수점 예외의 비트 OR입니다.|

합니다 *를 제외한* 인수는 0 일 수 있습니다 또는 매크로 중 두 개 이상의 지원 되는 부동 소수점 예외 매크로 또는 비트 중 하나입니다. 기타 인수 값의 결과는 정의 해제됩니다.

이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
