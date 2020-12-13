---
description: '다음에 대 한 자세한 정보: __stosb'
title: __stosb
ms.date: 09/02/2019
f1_keywords:
- __stosb
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
ms.openlocfilehash: 8fa8b506b1b4a15738d2eaebeeaad4b547b2f02e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143730"
---
# <a name="__stosb"></a>__stosb

**Microsoft 전용**

저장소 문자열 명령 ()을 생성 `rep stosb` 합니다.

## <a name="syntax"></a>구문

```C
void __stosb(
   unsigned char* Destination,
   unsigned char Data,
   size_t Count
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 작업의 대상입니다.

*데이터*\
진행 저장할 데이터입니다.

*수*\
진행 쓸 바이트 블록의 길이입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__stosb`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

결과적으로 문자 *데이터* 는 *대상* 문자열의 *카운트* 바이트 블록에 기록 됩니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```C
// stosb.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosb)

int main()
{
    unsigned char c = 0x40; /* '@' character */
    unsigned char s[] = "*********************************";

    printf_s("%s\n", s);
    __stosb((unsigned char*)s+1, c, 6);
    printf_s("%s\n", s);

}
```

```Output
*********************************
*@@@@@@**************************
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
