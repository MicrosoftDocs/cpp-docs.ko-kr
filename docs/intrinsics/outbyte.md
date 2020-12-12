---
description: '다음에 대 한 자세한 정보: __outbyte'
title: __outbyte
ms.date: 09/02/2019
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: e062d561719cbcdb32ab980efde9eb568defeadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222478"
---
# <a name="__outbyte"></a>__outbyte

**Microsoft 전용**

`out`로 지정 된 i/o 포트에서 지정 된 1 바이트를 전송 하는 명령을 생성 합니다 `Data` `Port` .

## <a name="syntax"></a>구문

```C
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 데이터를 보낼 포트입니다.

*데이터*\
진행 지정 된 포트에서 전송 될 바이트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__outbyte`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
