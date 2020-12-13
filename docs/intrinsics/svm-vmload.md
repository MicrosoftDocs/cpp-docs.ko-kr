---
description: '다음에 대 한 자세한 정보: __svm_vmload'
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: 975f6aed50007b0b184bbab2b9b48790e5e20616
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333710"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Microsoft 전용**

지정 된 VMCB (가상 컴퓨터 제어 블록)에서 프로세서 상태의 하위 집합을 로드 합니다.

## <a name="syntax"></a>구문

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>매개 변수

*VmcbPhysicalAddress*\
진행 VMCB의 실제 주소입니다.

## <a name="remarks"></a>설명

`__svm_vmload` 함수는 `VMLOAD` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) 사이트에서 "AMD64 아키텍처 프로그래머의 수동 볼륨 2: 시스템 프로그래밍" 문서 번호 24593, 수정 버전 3.11 문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
