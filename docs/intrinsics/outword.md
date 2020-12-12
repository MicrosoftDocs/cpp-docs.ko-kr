---
description: '다음에 대 한 자세한 정보: __outword'
title: __outword
ms.date: 09/02/2019
f1_keywords:
- __outword
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
ms.openlocfilehash: 07136a5ae293f7e23a1cf6b0baa2b3a0f0cc54d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257578"
---
# <a name="__outword"></a>__outword

**Microsoft 전용**

포트에 `out` 지정 된 i/o 포트에서 Word *데이터* 를 전송 하는 명령을 생성 합니다. 

## <a name="syntax"></a>구문

```C
void __outword(
   unsigned short Port,
   unsigned short Data
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 데이터를 보낼 포트입니다.

*데이터*\
진행 보낼 데이터입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__outword`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
