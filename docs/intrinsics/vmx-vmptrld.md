---
description: '다음에 대 한 자세한 정보: __vmx_vmptrld'
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 850311e4423940ebd34a203e6d43ec961b3258f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333536"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Microsoft 전용**

지정 된 주소에서 현재 VMCS (가상 컴퓨터 제어 구조)에 대 한 포인터를 로드 합니다.

## <a name="syntax"></a>구문

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>매개 변수

*VmcsPhysicalAddress*\
진행 VMCS 포인터가 저장 되는 주소입니다.

## <a name="return-value"></a>반환 값

0
작업에 성공했습니다.

1(sp1)
현재 VMCS의 `VM-instruction error field` 에서 사용할 수 있는 확장된 상태로 작업이 실패했습니다.

sr-2
사용 가능한 상태 없이 작업이 실패했습니다.

## <a name="remarks"></a>설명

VMCS 포인터는 64 비트 실제 주소입니다.

`__vmx_vmptrld` 함수는 `VMPTRLD` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 Intel 아키텍처용 Intel 가상화 기술 사양" 문서 번호 C97063-002 문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
