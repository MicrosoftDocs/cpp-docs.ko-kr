---
description: '다음에 대 한 자세한 정보: __outwordstring'
title: __outwordstring
ms.date: 09/02/2019
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: c0dba174776c7606a0f9ed11ac172331a6a8f350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257539"
---
# <a name="__outwordstring"></a>__outwordstring

**Microsoft 전용**

`rep outsw` *포트* 에서 지정 된 i/o 포트에서 시작 하는  *카운트* 단어를 전송 하는 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 데이터를 보낼 포트입니다.

*버퍼*\
진행 지정 된 포트를 통해 전송 되는 데이터에 대 한 포인터입니다.

*수*\
진행 보낼 단어 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
