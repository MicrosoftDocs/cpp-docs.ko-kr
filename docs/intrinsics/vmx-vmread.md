---
description: '다음에 대 한 자세한 정보: __vmx_vmread'
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 39ea9c0566d3f9c9d3fc6d980861fb3580293895
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333504"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Microsoft 전용**

현재 VMCS (가상 컴퓨터 제어 구조)에서 지정 된 필드를 읽고 지정 된 위치에 배치 합니다.

## <a name="syntax"></a>구문

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>매개 변수

*필드가*\
진행 읽을 VMCS 필드입니다.

*FieldValue*\
진행 매개 변수로 지정 된 VMCS 필드에서 읽은 값을 저장할 위치에 대 한 포인터 `Field` 입니다.

## <a name="return-value"></a>반환 값

|값|의미|
|-----------|-------------|
|0|작업에 성공했습니다.|
|1|현재 VMCS의 `VM-instruction error field` 에서 사용할 수 있는 확장된 상태로 작업이 실패했습니다.|
|2|사용 가능한 상태 없이 작업이 실패했습니다.|

## <a name="remarks"></a>설명

`__vmx_vmread` 함수는 `VMREAD` 컴퓨터 명령에 해당합니다. 매개 변수 값은 `Field` Intel 설명서에 설명 된 인코딩된 필드 인덱스입니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "IA-32 intel Architecture에 대 한 Intel 가상화 기술 사양"의 부록 C를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmread`|X64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
