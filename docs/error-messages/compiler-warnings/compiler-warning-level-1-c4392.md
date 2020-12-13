---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4392'
title: 컴파일러 경고(수준 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: d10b966f6727ec3461255d3789a6e9a7aed78c22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339893"
---
# <a name="compiler-warning-level-1-c4392"></a>컴파일러 경고(수준 1) C4392

' signature ': 내장 함수에 대 한 인수 개수가 잘못 되었습니다. ' number ' 개의 인수가 필요 합니다.

컴파일러 내장 함수 선언에 잘못 된 수의 인수가 있습니다. 결과 이미지가 올바르게 실행 되지 않을 수 있습니다.

이 경고를 해결 하려면 선언을 수정 하거나 선언을 삭제 하 고 단순히 적절 한 헤더 파일을 #include 합니다.

다음 샘플에서는 C4392를 생성 합니다.

```cpp
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```
