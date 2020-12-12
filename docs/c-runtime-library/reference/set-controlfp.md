---
description: '다음에 대 한 자세한 정보: _set_controlfp'
title: _set_controlfp
ms.date: 04/05/2018
api_name:
- _set_controlfp
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
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 44316cb4114d06ced1b3d67a261bc8d3ceb1aee6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288869"
---
# <a name="_set_controlfp"></a>_set_controlfp

부동 소수점 제어 단어를 설정합니다.

## <a name="syntax"></a>구문

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>매개 변수

*newControl*<br/>
새 제어 단어 비트 값입니다.

*마스크할*<br/>
설정할 새 제어 단어 비트의 마스크입니다.

## <a name="return-value"></a>반환 값

없음

## <a name="remarks"></a>설명

**_Set_controlfp** 함수는 **_control87** 와 유사 하지만 부동 소수점 제어 단어를 *newcontrol* 로 설정 합니다. 값의 비트는 부동 소수점 제어 상태를 나타냅니다. 부동 소수점 제어 상태를 사용하면 프로그램이 부동 소수점 연산 패키지에서 정밀도, 반올림 및 무한대 모드를 변경할 수 있습니다. **_Set_controlfp** 를 사용 하 여 부동 소수점 예외를 마스킹 또는 마스크 해제할 수도 있습니다. 자세한 내용은 [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)를 참조하세요.

공용 언어 런타임이 기본 부동 소수점 전체 자릿수를 지원 하기 때문에 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일할 때이 함수는 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|호환성|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|x86 프로세서만|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
