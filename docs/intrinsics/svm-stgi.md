---
description: '다음에 대 한 자세한 정보: __svm_stgi'
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 8a6c7c221ed0bbf71a00685e8a0545818dd507a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336845"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Microsoft 전용**

전역 인터럽트 플래그를 설정 합니다.

## <a name="syntax"></a>구문

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>설명

`__svm_stgi` 함수는 `STGI` 컴퓨터 명령에 해당합니다. 전역 인터럽트 플래그는 i/o 완료, 하드웨어 온도 경고 또는 디버그 예외 등의 이벤트가 발생 하 여 마이크로프로세서에서 인터럽트를 무시, 연기 또는 처리할지 여부를 결정 합니다.

이 함수는 게스트 운영 체제 및 해당 애플리케이션과 호스트 가상 머신 모니터의 상호 작용을 지원합니다. 자세한 내용을 보려면 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) 사이트에서 "AMD64 아키텍처 프로그래머의 수동 볼륨 2: 시스템 프로그래밍"을 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
