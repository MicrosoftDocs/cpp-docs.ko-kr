---
description: '다음에 대 한 자세한 정보: __invlpg'
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 16d8f51c8bf36ea94be7b1325ee5bed256c29693
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167905"
---
# <a name="__invlpg"></a>__invlpg

**Microsoft 전용**

`invlpg` *주소* 에 의해 가리키는 메모리와 연결 된 페이지의 TLB (translation 할당 준비 buffer)를 무효화 하는 x86 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>매개 변수

*위치*\
진행 64 비트 주소입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__invlpg`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 `__invlpg` 권한 있는 명령을 내보내고, 권한 수준 (CPL)이 0 인 커널 모드 에서만 사용할 수 있습니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
