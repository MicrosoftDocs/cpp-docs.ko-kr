---
description: '다음에 대 한 자세한 정보: __vmx_vmclear'
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 2eec5c1189c6a798246a6dabfc731fb0166bc14a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333567"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Microsoft 전용**

지정 된 VMCS (가상 컴퓨터 제어 구조)를 초기화 하 고 해당 시작 상태를로 설정 `Clear` 합니다.

## <a name="syntax"></a>구문

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>매개 변수

*VmcsPhysicalAddress*\
진행 지울 VMCS의 실제 주소를 포함 하는 64 비트 메모리 위치에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

|값|의미|
|-----------|-------------|
|0|작업에 성공했습니다.|
|1|현재 VMCS의 `VM-instruction error field` 에서 사용할 수 있는 확장된 상태로 작업이 실패했습니다.|
|2|사용 가능한 상태 없이 작업이 실패했습니다.|

## <a name="remarks"></a>설명

응용 프로그램은 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) 또는 [__vmx_vmresume](../intrinsics/vmx-vmresume.md) 함수를 사용 하 여 VM 입력 작업을 수행할 수 있습니다. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) 함수는 시작 상태가 인 vmcs 에서만 사용할 수 있으며 `Clear` , [__vmx_vmresume](../intrinsics/vmx-vmresume.md) 함수는 시작 상태가 인 vmcs 에서만 사용할 수 있습니다 `Launched` . 따라서 [__vmx_vmclear](../intrinsics/vmx-vmclear.md) 함수를 사용 하 여 vmcs의 시작 상태를로 설정 `Clear` 합니다. 첫 번째 VM에 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) 함수를 사용 하 고 후속 vm 입력 작업에 대해 [__vmx_vmresume](../intrinsics/vmx-vmresume.md) 함수를 사용 합니다.

`__vmx_vmclear` 함수는 `VMCLEAR` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 Intel 아키텍처용 Intel 가상화 기술 사양" 문서 번호 C97063-002 문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
