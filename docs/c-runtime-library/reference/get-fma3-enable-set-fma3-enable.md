---
description: '자세히 알아보기: _get_FMA3_enable, _set_FMA3_enable'
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: d43b5e4e6db652c87bcddf9dd3c91371dc038f33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303676"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable, _set_FMA3_enable

초월수 수학 부동 소수점 라이브러리 함수가 X64 플랫폼용으로 컴파일된 코드에서 FMA3 명령을 사용 하는지 여부를 지정 하는 플래그를 가져오거나 설정 합니다.

## <a name="syntax"></a>구문

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>매개 변수

*flag*<br/>
X64 플랫폼에서 초월수 math 부동 소수점 라이브러리 함수의 FMA3 구현을 사용 하도록 설정 하려면 1로 설정 하 고 FMA3 명령을 사용 하지 않는 구현을 사용 하려면 0으로 설정 합니다.

## <a name="return-value"></a>반환 값

초월수 math 부동 소수점 라이브러리 함수의 FMA3 구현을 사용할 수 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="remarks"></a>설명

CRT 라이브러리의 초월수 math 부동 소수점 함수에서 FMA3 명령을 사용 하거나 사용 하지 않도록 설정 하려면 **_set_FMA3_enable** 함수를 사용 합니다. 반환 값은 변경 후에 사용 중인 구현을 반영 합니다. CPU가 FMA3 명령을 지원 하지 않는 경우이 함수는 라이브러리에서 사용 하도록 설정할 수 없으며 반환 값은 0입니다. **_Get_FMA3_enable** 를 사용 하 여 라이브러리의 현재 상태를 가져옵니다. 기본적으로 X64 플랫폼에서 CRT 시작 코드는 CPU가 FMA3 명령을 지원 하는지 여부를 검색 하 고 라이브러리에서 FMA3 구현을 사용 하거나 사용 하지 않도록 설정 합니다.

FMA3 구현은 서로 다른 알고리즘을 사용 하므로 FMA3 구현이 사용 되거나 사용 하지 않도록 설정 되거나 FMA3를 지원 하지 않는 컴퓨터 사이에서 계산 결과의 약간 차이가 관찰 될 수 있습니다. 자세한 내용은 [부동 소수점 마이그레이션 문제](../../porting/floating-point-migration-issues.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**_Set_FMA3_enable** 및 **_GET_FMA3_ENABLE** 함수는 CRT의 X64 버전 에서만 사용할 수 있습니다.

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C \<math.h><br />C + +: \<cmath> 또는 \<math.h>|

**_Set_FMA3_enable** 및 **_Get_FMA3_enable** 함수는 Microsoft 전용입니다. 호환성에 대한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[부동 소수점 마이그레이션 문제](../../porting/floating-point-migration-issues.md)<br/>
