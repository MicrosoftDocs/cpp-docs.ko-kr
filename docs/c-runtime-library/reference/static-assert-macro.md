---
description: '자세한 정보: 매크로 _STATIC_ASSERT'
title: _STATIC_ASSERT 매크로
ms.date: 11/04/2016
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
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: bbdb615cccfb245868d4c282acf86c9228ea574b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171201"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT 매크로

컴파일 시간에 식을 계산 하 고 결과가 **FALSE** 인 경우 오류를 생성 합니다.

## <a name="syntax"></a>구문

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
0이 아닌 값 (**TRUE**) 또는 0 (**FALSE**)으로 계산 되는 식 (포인터 포함)입니다.

## <a name="remarks"></a>설명

이 매크로는 [_ASSERT 및 _ASSERTE 매크로](assert-asserte-assert-expr-macros.md)와 비슷합니다. 단, *booleanExpression* 는 런타임이 아닌 컴파일 시간에 평가 됩니다. *BooleanExpression* 가 **FALSE** (0)로 평가 되는 경우 [컴파일러 오류 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) 이 생성 됩니다.

## <a name="example"></a>예제

이 예제에서는 [sizeof](../../c-language/sizeof-operator-c.md) **`int`** a가 2 바이트 보다 크거나 같은지와 [sizeof](../../c-language/sizeof-operator-c.md) a가 1 바이트 인지 여부를 확인 합니다 **`long`** . 프로그램이 컴파일되지 않으며,가 1 바이트 보다 크기 때문에 [컴파일러 오류 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) 생성 됩니다 **`long`** .

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR 매크로](assert-asserte-assert-expr-macros.md)<br/>
