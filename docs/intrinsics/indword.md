---
description: '다음에 대 한 자세한 정보: __indword'
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: bd637027ee930b551f08508874554e2b19f22461
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336926"
---
# <a name="__indword"></a>__indword

**Microsoft 전용**

명령을 사용 하 여 지정 된 포트에서 한 개의 double 단어로 데이터를 읽습니다 `in` .

## <a name="syntax"></a>구문

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
진행 읽을 포트입니다.

## <a name="return-value"></a>반환 값

포트에서 읽은 단어입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__indword`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
