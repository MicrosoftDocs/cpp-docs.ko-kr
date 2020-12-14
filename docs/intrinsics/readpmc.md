---
description: '다음에 대 한 자세한 정보: __readpmc'
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: ceff8522d4895f69a47cf429e59d267c671e3a66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294134"
---
# <a name="__readpmc"></a>__readpmc

**Microsoft 전용**

카운터에 `rdpmc` 지정 된 성능 모니터링 카운터를 읽는 명령을 생성 합니다 .

## <a name="syntax"></a>구문

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>매개 변수

*counter*\
진행 읽을 성능 카운터입니다.

## <a name="return-value"></a>반환 값

지정 된 성능 카운터의 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readpmc`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
