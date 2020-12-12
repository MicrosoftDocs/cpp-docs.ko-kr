---
description: '다음에 대 한 자세한 정보: __inwordstring'
title: __inwordstring
ms.date: 09/02/2019
f1_keywords:
- __inwordstring
- __inwordstring_cpp
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
ms.openlocfilehash: d65aaedd3fc0fd51ab276abb391ed3c58047ccda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167814"
---
# <a name="__inwordstring"></a>__inwordstring

**Microsoft 전용**

명령을 사용 하 여 지정 된 포트에서 데이터를 읽습니다 `rep insw` .

## <a name="syntax"></a>구문

```C
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 읽을 포트입니다.

*버퍼*\
제한이 포트에서 읽은 데이터는 여기에 기록 됩니다.

*수*\
진행 읽을 데이터의 단어 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__inwordstring`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
