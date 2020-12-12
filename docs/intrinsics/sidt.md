---
description: '다음에 대 한 자세한 정보: __sidt'
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: 075351bc10981dd8453381e9ce9393a046dfd884
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306965"
---
# <a name="__sidt"></a>__sidt

**Microsoft 전용**

지정 된 메모리 위치에 인터럽트 설명자 테이블 레지스터 (IDTR)의 값을 저장 합니다.

## <a name="syntax"></a>구문

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>매개 변수

*대상이*\
진행 IDTR이 저장 된 메모리 위치에 대 한 포인터입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__sidt`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`__sidt` 함수는 `SIDT` 컴퓨터 명령에 해당합니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "Intel 아키텍처 소프트웨어 개발자 설명서, 볼륨 2: 명령 집합 참조" 문서를 검색 하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
