---
description: '다음에 대 한 자세한 정보: __stosd'
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: 56a29a27790f7f45a9fb3f0ace348759c0b1ff3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143717"
---
# <a name="__stosd"></a>__stosd

**Microsoft 전용**

저장소 문자열 명령 ()을 생성 `rep stosd` 합니다.

## <a name="syntax"></a>구문

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 작업의 대상입니다.

*데이터*\
진행 저장할 데이터입니다.

*수*\
진행 쓸 더블 워드 블록의 길이입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__stosd`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

그 결과, 더블 워드 *데이터* 는 *대상이* 가리키는 메모리 위치에서 더블 *수* 의 블록에 기록 됩니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```C
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
