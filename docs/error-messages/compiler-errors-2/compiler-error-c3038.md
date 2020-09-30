---
title: 컴파일러 오류 C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 7da7dcf1f03c05511ba4bb970e898bc06b9ae3bd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508415"
---
# <a name="compiler-error-c3038"></a>컴파일러 오류 C3038

'var': 'private' 절의 변수는 바깥쪽 컨텍스트에서 환산(reduction) 변수일 수 없습니다.

병렬 지시문의 [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 절에 표시되는 변수는 병렬 구문에 바인딩하는 작업 공유 지시문의 [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp) 절에 지정할 수 없습니다.

다음 샘플에서는 C3038을 생성합니다.

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
