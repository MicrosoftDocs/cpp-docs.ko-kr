---
description: '다음에 대 한 자세한 정보: __inbyte'
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: 77cc1cfb792ffa2f6aef9879820e644372895193
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337023"
---
# <a name="__inbyte"></a>__inbyte

**Microsoft 전용**

`in`로 지정 된 포트에서 읽은 단일 바이트를 반환 하는 명령을 생성 `Port` 합니다.

## <a name="syntax"></a>구문

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 읽을 포트입니다.

## <a name="return-value"></a>반환 값

지정 된 포트에서 읽은 바이트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__inbyte`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
