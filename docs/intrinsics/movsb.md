---
description: '다음에 대 한 자세한 정보: __movsb'
title: __movsb
ms.date: 09/02/2019
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 6e4a9ba7482f7f614b80bd0596111874f0087c86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222452"
---
# <a name="__movsb"></a>__movsb

**Microsoft 전용**

이동 문자열 ( `rep movsb` ) 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 복사본의 대상에 대 한 포인터입니다.

*원본*\
진행 복사본의 원본에 대 한 포인터입니다.

*수*\
진행 복사할 바이트 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__movsb`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

그 결과에서 가리키는 첫 번째 `Count` 바이트가 `Source` 문자열에 복사 됩니다 `Destination` .

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
