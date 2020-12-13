---
description: '다음에 대 한 자세한 정보: __svm_vmsave'
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: 5c0e4eb5f2d4c0f73921572811b070c8f87a2673
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333679"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Microsoft 전용**

지정 된 VMCB (가상 컴퓨터 제어 블록)에 프로세서 상태의 하위 집합을 저장 합니다.

## <a name="syntax"></a>구문

```C
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>매개 변수

*VmcbPhysicalAddress*\
진행 VMCB의 실제 주소입니다.

## <a name="remarks"></a>설명

`__svm_vmsave` 함수는 `VMSAVE` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용은 [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) 사이트에서 "AMD64 아키텍처 프로그래머의 수동 볼륨 2: 시스템 프로그래밍," 문서 번호 24593, 수정 버전 3.11 이상 "문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_vmsave`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
