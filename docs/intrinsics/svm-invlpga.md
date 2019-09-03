---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219892"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Microsoft 전용**

컴퓨터의 변환 분리 버퍼에서 주소 매핑 항목을 무효화 합니다. 매개 변수는 무효화할 페이지의 가상 주소와 주소 공간 식별자를 지정 합니다.

## <a name="syntax"></a>구문

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>매개 변수

*Vaddr*\
진행 무효화할 페이지의 가상 주소입니다.

*as_id*\
진행 무효화할 페이지의 ASID (주소 공간 식별자)입니다.

## <a name="remarks"></a>설명

`__svm_invlpga` 함수는 `INVLPGA` 컴퓨터 명령에 해당합니다. 이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용은 다음 문서를 검색 하십시오. "AMD64 아키텍처 프로그래머의 수동 볼륨 2: 시스템 프로그래밍 ( [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) 사이트에서 "문서 번호 24593, 수정 버전 3.11)

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**헤더 파일** \<intrin.h >

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
