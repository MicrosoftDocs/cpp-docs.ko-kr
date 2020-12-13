---
description: '다음에 대 한 자세한 정보: __min'
title: __min
ms.date: 04/05/2018
api_name:
- __min
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: 337d4fc7226044e41a616dc6da8230e013b2702d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340582"
---
# <a name="__min"></a>__min

두 값 중 더 작은 값을 반환 하는 전처리기 매크로입니다.

## <a name="syntax"></a>구문

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>매개 변수

*a*, *b*<br/>
연산자가 작동 하는 모든 형식의 값입니다 **<** .

## <a name="return-value"></a>반환 값

두 인수 중 더 작은 값입니다.

## <a name="remarks"></a>설명

**__Min** 매크로는 두 값을 비교 하 여 더 작은 값을 반환 합니다. 인수는 서명되거나 서명되지 않은 모든 숫자 데이터 형식일 수 있습니다. 두 인수와 반환 값은 동일한 데이터 형식이어야 합니다.

반환 되는 인수는 매크로에 의해 두 번 계산 됩니다. 이로 인해 인수가 계산 될 때 값을 변경 하는 식인 경우 (예:) 예기치 않은 결과가 발생할 수 있습니다 `*p++` .

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>예제

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
