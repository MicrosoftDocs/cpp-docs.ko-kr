---
description: '다음에 대 한 자세한 정보: __stosw'
title: __stosw
ms.date: 09/02/2019
f1_keywords:
- __stosw
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
ms.openlocfilehash: 2995276fb255858d6c3dd9f438487726e75fdf1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143691"
---
# <a name="__stosw"></a>__stosw

**Microsoft 전용**

저장소 문자열 명령 ()을 생성 `rep stosw` 합니다.

## <a name="syntax"></a>구문

```C
void __stosw(
   unsigned short* Destination,
   unsigned short Data,
   size_t Count
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 작업의 대상입니다.

*데이터*\
진행 저장할 데이터입니다.

*수*\
진행 쓸 단어 블록의 길이입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__stosw`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

그 결과, 단어 *데이터* 는 *대상* 문자열의 *개수* 단어 블록에 기록 됩니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```C
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
