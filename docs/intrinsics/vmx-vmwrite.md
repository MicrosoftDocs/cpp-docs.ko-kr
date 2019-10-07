---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219399"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Microsoft 전용**

현재 VMCS (가상 컴퓨터 제어 구조)의 지정 된 필드에 지정 된 값을 씁니다.

## <a name="syntax"></a>구문

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>매개 변수

*필드가*\
진행 쓸 VMCS 필드입니다.

*FieldValue*\
진행 VMCS 필드에 쓸 값입니다.

## <a name="return-value"></a>반환 값

0\
작업에 성공했습니다.

1\
현재 VMCS의 `VM-instruction error field` 에서 사용할 수 있는 확장된 상태로 작업이 실패했습니다.

2\
사용 가능한 상태 없이 작업이 실패했습니다.

## <a name="remarks"></a>설명

`__vmx_vmwrite` 함수는 `VMWRITE` 컴퓨터 명령에 해당합니다. `Field` 매개 변수 값은 Intel 설명서에 설명 된 인코딩된 필드 인덱스입니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 intel Architecture에 대 한 Intel 가상화 기술 사양"의 부록 C를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**헤더 파일** \<intrin.h >

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
