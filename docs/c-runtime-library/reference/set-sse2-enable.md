---
description: '다음에 대 한 자세한 정보: _set_SSE2_enable'
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: a9c82b2f17d90bc158ac77b8d7ad9625491856aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211208"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

CRT 수학 루틴에서 SSE2(스트리밍 SIMD 확장 2) 지침을 사용하도록 설정하거나 사용하지 않도록 설정합니다. SSE2가 기본적으로 사용하도록 설정되어 있으므로 x64 아키텍처에서 이 함수를 사용할 수 없습니다.

## <a name="syntax"></a>구문

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>매개 변수

*flag*<br/>
SSE2 구현을 사용하려면 1, SSE2 구현을 사용하지 않으려면 0입니다. 기본적으로 SSE2 구현은 지원하는 프로세서에서 사용할 수 있습니다.

## <a name="return-value"></a>반환 값

SSE2 구현을 사용할 수 있는 경우 0이 아닌 값이고, SSE2 구현을 사용할 수 없는 경우 0입니다.

## <a name="remarks"></a>설명

다음 함수는 **_set_SSE2_enable** 을 사용 하 여 사용 하도록 설정할 수 있는 SSE2 구현을 포함 합니다.

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [평면](floor-floorf-floorl.md)

- [로깅할](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

SSE2 중간 값은 64비트 부동 소수점 수량이지만 기본 구현 중간 값은 80비트 부동 소수점 수량이기 때문에 이러한 함수의 SSE2 구현은 기본 구현과는 약간 다른 결과를 낼 수 있습니다.

> [!NOTE]
> [/Oi (내장 함수 생성)](../../build/reference/oi-generate-intrinsic-functions.md) 컴파일러 옵션을 사용 하 여 프로젝트를 컴파일하면 **_set_SSE2_enable** 영향을 주지 않는 것 처럼 보일 수 있습니다. **/Oi** 컴파일러 옵션은 CRT 호출을 대체 하기 위해 내장 함수를 사용 하는 권한을 컴파일러에 제공 합니다. 이 동작은 **_set_SSE2_enable** 의 효과를 재정의 합니다. **/Oi** 가 **_set_SSE2_enable** 를 재정의 하지 않도록 하려면 **/Oi-** 를 사용 하 여 프로젝트를 컴파일합니다. 이는 **/oi** 를 암시 하는 다른 컴파일러 스위치를 사용 하는 경우에도 좋은 방법입니다.

SSE2 구현은 모든 예외가 마스크된 경우에만 사용됩니다. 예외를 마스크하려면 [_control87, _controlfp](control87-controlfp-control87-2.md)를 사용하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>참고 항목

[CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)<br/>
