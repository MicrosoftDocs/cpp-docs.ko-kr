---
description: '다음에 대 한 자세한 정보: __vmx_vmptrst'
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: 216da453acf5c04e4189271185567841327571ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333520"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Microsoft 전용**

현재 VMCS (가상 컴퓨터 제어 구조)에 대 한 포인터를 지정 된 주소에 저장 합니다.

## <a name="syntax"></a>구문

```C
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>매개 변수

*VmcsPhysicalAddress*\
진행 현재 VMCS 포인터가 저장 되는 주소입니다.

## <a name="remarks"></a>설명

VMCS 포인터는 64 비트 실제 주소입니다.

`__vmx_vmptrst` 함수는 `VMPTRST` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 Intel 아키텍처용 Intel 가상화 기술 사양" 문서 번호 C97063-002 문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
