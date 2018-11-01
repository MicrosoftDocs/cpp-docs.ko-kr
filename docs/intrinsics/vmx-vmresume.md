---
title: __vmx_vmresume
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 4be197566f32c5edf49a9036b1ac641416d28fc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616855"
---
# <a name="vmxvmresume"></a>__vmx_vmresume

**Microsoft 전용**

현재 VMCS(가상 머신 제어 구조)를 사용하여 VMX 루트가 아닌 작업을 다시 시작합니다.

## <a name="syntax"></a>구문

```
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>반환 값

|값|의미|
|-----------|-------------|
|0|작업에 성공했습니다.|
|1|현재 VMCS의 `VM-instruction error field` 에서 사용할 수 있는 확장된 상태로 작업이 실패했습니다.|
|2|사용 가능한 상태 없이 작업이 실패했습니다.|

## <a name="remarks"></a>설명

응용 프로그램에서 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) 또는 `__vmx_vmresume` 함수를 사용하여 VM 시작 작업을 수행할 수 있습니다. `__vmx_vmlaunch` 함수는 시작 상태가 `Clear`인 VMCS에서만 사용할 수 있으며, `__vmx_vmresume` 함수는 시작 상태가 `Launched`인 VMCS에서만 사용할 수 있습니다. 따라서 [__vmx_vmclear](../intrinsics/vmx-vmclear.md) 함수를 사용하여 VMCS의 시작 상태를 `Clear`로 설정한 다음 첫 번째 VM 시작 작업에는 `__vmx_vmlaunch` 함수를 사용하고 이후 VM 시작 작업에는 `__vmx_vmresume` 함수를 사용합니다.

`__vmx_vmresume` 함수는 `VMRESUME` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 응용 프로그램과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 Intel 아키텍처에 대한 Intel 가상화 기술 사양"(문서 번호 C97063-002) PDF 문서를 검색하세요.

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**헤더 파일** \<intrin.h >

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)