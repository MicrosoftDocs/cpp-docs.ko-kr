---
description: '자세히 알아보기: feholdexcept'
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 89ccf9bedb05752202152f6bd862b11b2f765322
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322526"
---
# <a name="feholdexcept"></a>feholdexcept

현재 부동 소수점 환경을 지정된 개체에 저장하고, 부동 소수점 상태 플래그를 지우고, 가능한 경우 부동 소수점 환경을 무중단 모드로 전환합니다.

## <a name="syntax"></a>구문

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>매개 변수

*penv*<br/>
부동 소수점 환경의 복사본을 포함 하는 **fenv_t** 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

함수에서 중지 되지 않은 부동 소수점 예외 처리를 성공적으로 켤 수 있는 경우에만 0을 반환 합니다.

## <a name="remarks"></a>설명

**Feholdexcept** 함수는 *penv* 가 가리키는 **fenv_t** 개체에 현재 부동 소수점 환경의 상태를 저장 하 고, 부동 소수점 예외에 대 한 실행을 인터럽트 하지 않도록 환경을 설정 하는 데 사용 됩니다. 이를 무중단 모드라고 합니다.  이 모드는 [fesetenv](fesetenv1.md) 또는 [feupdateenv](feupdateenv.md)를 통해 환경이 복원될 때까지 계속됩니다.

호출자로부터 하나 이상의 부동 소수점 예외를 숨겨야 하는 하위 루틴의 시작 부분에서 이 함수를 사용할 수 있습니다. 예외를 보고 하려면 [feclearexcept을](feclearexcept1.md) 사용 하 여 원치 않는 예외를 지운 다음 **feupdateenv** 를 호출 하 여 중지 안 함 모드를 종료 하면 됩니다.

이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
