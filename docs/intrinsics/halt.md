---
description: '다음에 대 한 자세한 정보: __halt'
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: e38478b14b59c910e6d6ac12f9cb69fa369e3459
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336975"
---
# <a name="__halt"></a>__halt

**Microsoft 전용**

사용 가능한 인터럽트, 비 마스크 해제 인터럽트 (NMI) 또는 다시 설정이 발생할 때까지 마이크로프로세서를 중단 합니다.

## <a name="syntax"></a>Syntax

```C
void __halt( void );
```

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__halt`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`__halt`함수는 `HLT` 컴퓨터 명령과 같으며 커널 모드 에서만 사용할 수 있습니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "Intel 아키텍처 소프트웨어 개발자 설명서, 볼륨 2: 명령 집합 참조" 문서를 검색 하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
