---
description: '다음에 대 한 자세한 정보: __ll_lshift'
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 324286a0f7ca28eaa7259f05f629f87e763aac0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167762"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft 전용**

제공 된 64 비트 값을 지정 된 비트 수 만큼 왼쪽으로 이동 합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>매개 변수

*마스크할*\
진행 왼쪽으로 이동할 64 비트 정수 값입니다.

*nBit*\
진행 이동할 비트 수입니다.

## <a name="return-value"></a>반환 값

마스크를 비트로 왼쪽으로 이동 `nBit` 했습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

64 비트 아키텍처에 대 한 프로그램을 컴파일하 `nBit` 는 경우 63 보다 크면 이동할 비트 수는 `nBit` 모듈로 64입니다. 32 비트 아키텍처에 대 한 프로그램을 컴파일하 `nBit` 는 경우 31 보다 크면 이동할 비트 수는 `nBit` 모듈로 32입니다.

`ll`이름의은 ()에 대 한 작업 임을 나타냅니다 **`long long`** **`__int64`** .

## <a name="example"></a>예제

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>출력

```Output
10000
```

> [!NOTE]
> 왼쪽 시프트 연산의 서명 되지 않은 버전이 없습니다. 는 `__ll_lshift` 이미 부호 없는 입력 매개 변수를 사용 하기 때문입니다. 오른쪽 시프트와는 달리, 결과의 최하위 비트는 이동 된 값의 부호와 관계 없이 항상 0으로 설정 되기 때문에 왼쪽 shift에 대 한 부호 종속성은 없습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
