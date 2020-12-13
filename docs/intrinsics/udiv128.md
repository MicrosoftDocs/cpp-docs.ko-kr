---
description: '다음에 대 한 자세한 정보: _udiv128'
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: f88546a179106f4291fcaeb865f1aad9e67c4045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333655"
---
# <a name="_udiv128"></a>_udiv128

`_udiv128`내장 함수는 128 비트 부호 없는 정수를 64 비트 부호 없는 정수로 나눕니다. 반환 값은 몫을 보유 하 고 내장 함수는 포인터 매개 변수를 통해 나머지를 반환 합니다. `_udiv128` 는 **Microsoft** 전용입니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>매개 변수

*highDividend* \
진행 피제수의 상위 64 비트입니다.

*lowDividend* \
진행 피제수의 하위 64 비트입니다.

*나누기* \
진행 로 나눌 64 비트 정수입니다.

*남은* \
제한이 나머지의 64 비트 정수 비트입니다.

## <a name="return-value"></a>반환 값

몫의 64 비트입니다.

## <a name="remarks"></a>설명

*Highdividend* 에서 128 비트 피제수의 상한 64 비트와 *lowdividend* 의 하위 64 비트를 전달 합니다. 내장 함수는이 값을 *제수로* 나눕니다. *나머지* 를 가리키는 64 비트 부호 없는 정수에 나머지를 저장 하 고 몫의 64 비트를 반환 합니다.

`_udiv128`내장 함수는 Visual Studio 2019 RTM부터 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|헤더|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>참고 항목

[_div128](div128.md) \
[컴파일러 내장 함수](compiler-intrinsics.md)
