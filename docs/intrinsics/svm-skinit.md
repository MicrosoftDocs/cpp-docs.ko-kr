---
description: '다음에 대 한 자세한 정보: __svm_skinit'
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: dd35566664a6bff4a57ea986fc99ffcd731c79e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206268"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Microsoft 전용**

가상 컴퓨터 모니터 등의 안정형 보안 소프트웨어 로드를 시작 합니다.

## <a name="syntax"></a>구문

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>매개 변수

*block_address*\
64K 바이트 SLB (Secure Loader Block)의 32 비트 실제 주소입니다.

## <a name="remarks"></a>설명

`__svm_skinit` 함수는 `SKINIT` 컴퓨터 명령에 해당합니다. 이 함수는 프로세서 및 TPM (신뢰할 수 있는 플랫폼 모듈)을 사용 하 여 *보안 커널 (보안 커널* ) 이라고 하는 신뢰할 수 있는 소프트웨어를 확인 하 고 로드 하는 보안 시스템의 일부입니다. 가상 컴퓨터 모니터는 보안 커널의 예입니다. 보안 시스템은 초기화 프로세스 중 로드 된 프로그램 구성 요소를 확인 합니다. 컴퓨터가 다중 프로세서 인 경우 인터럽트, 장치 액세스 또는 다른 프로그램에 의해 구성 요소가 변조 되지 않도록 보호 합니다.

*Block_address* 매개 변수는 SLB ( *보안 로더 블록* ) 라고 하는 64k 메모리 블록의 실제 주소를 지정 합니다. SLB에는 *보안 로더* 라는 프로그램이 포함 되어 있습니다. 컴퓨터의 운영 환경을 설정한 다음 보안 커널을 로드 합니다.

이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) 사이트에서 "AMD64 아키텍처 프로그래머의 수동 볼륨 2: 시스템 프로그래밍"을 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
