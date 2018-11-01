---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 0ff46aa15fbb8728ce02255209a32f01a168609b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629387"
---
# <a name="invlpg"></a>__invlpg

**Microsoft 전용**

X86을 생성 `invlpg` 가 가리키는 메모리와 관련 된 페이지에 대 한 번역 할당 준비 버퍼 (TLB)을 무효화 하는 명령 `Address`입니다.

## <a name="syntax"></a>구문

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>매개 변수

*주소*<br/>
[in] 64 비트 주소입니다.

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__invlpg`|x86, x64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

내장 `__invlpg` 권한 있는 명령을 내보냅니다 이며 0의 권한 수준 (CPL)를 사용 하 여 커널 모드에서 사용할 수만 있습니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)