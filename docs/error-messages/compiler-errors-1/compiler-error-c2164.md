---
description: '자세한 정보: 컴파일러 오류 C2164'
title: 컴파일러 오류 C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 9afe0809075f83c77ffae2ef77bc72c9e0f194e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145520"
---
# <a name="compiler-error-c2164"></a>컴파일러 오류 C2164

' function ': 내장 함수를 선언 하지 않았습니다.

`intrinsic`Pragma가 선언 되지 않은 함수를 사용 합니다 ( **/oi** 와만 발생). 또는 컴파일러 내장 함수 중 하나가 헤더 파일을 포함 하지 않고 사용 되었습니다.

다음 샘플에서는 C2164를 생성 합니다.

```c
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```
