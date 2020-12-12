---
description: '자세한 정보: 컴파일러 오류 C 3015'
title: 컴파일러 오류 C3015
ms.date: 11/04/2016
f1_keywords:
- C3015
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
ms.openlocfilehash: 84d1431ef04b16631ba6f32aa9b41dc08cef8f2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285879"
---
# <a name="compiler-error-c3015"></a>컴파일러 오류 C3015

OpenMP 'for' 문의 초기화 형식이 잘못되었습니다.

**`for`** OpenMP 문의 루프는 완전 하 고 명시적으로 지정 되어야 합니다.

다음 샘플에서는 C3015를 생성합니다.

```cpp
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```
