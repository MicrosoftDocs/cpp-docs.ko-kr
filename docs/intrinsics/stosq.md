---
description: '다음에 대 한 자세한 정보: __stosq'
title: __stosq
ms.date: 09/02/2019
f1_keywords:
- __stosq
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
ms.openlocfilehash: 5fce587c163da18679750c20ec697c489ecf5d90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143704"
---
# <a name="__stosq"></a>__stosq

**Microsoft 전용**

저장소 문자열 명령 ()을 생성 `rep stosq` 합니다.

## <a name="syntax"></a>구문

```C
void __stosb(
   unsigned __int64* Destination,
   unsigned __int64 Data,
   size_t Count
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 작업의 대상입니다.

*데이터*\
진행 저장할 데이터입니다.

*수*\
진행 쓸 quadwords 블록의 길이입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__stosq`|AMD64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

그 결과, 쿼드 워드 *데이터* 는 *대상* 문자열의 *Count* quadwords 블록에 기록 됩니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```C
// stosq.c
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosq)

int main()
{
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;
   unsigned __int64 a[10];
   memset(a, 0, sizeof(a));
   __stosq(a+1, val, 2);
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff ffffffffffff 0
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
