---
description: '다음에 대 한 자세한 정보: __indwordstring'
title: __indwordstring
ms.date: 09/02/2019
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: 18d18a8981a2dd58c0f7bcd366faaf46629647c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336909"
---
# <a name="__indwordstring"></a>__indwordstring

**Microsoft 전용**

명령을 사용 하 여 지정 된 포트에서 데이터를 읽습니다 `rep insd` .

## <a name="syntax"></a>구문

```C
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 읽을 포트입니다.

*버퍼*\
제한이 포트에서 읽은 데이터는 여기에 기록 됩니다.

*수*\
진행 읽을 데이터의 바이트 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__indwordstring`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
