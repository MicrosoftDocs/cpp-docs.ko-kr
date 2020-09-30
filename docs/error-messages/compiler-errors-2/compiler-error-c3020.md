---
title: 컴파일러 오류 C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: cb32ceaf71d0a1c121b6e01e4b49f1db79a84d79
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506495"
---
# <a name="compiler-error-c3020"></a>컴파일러 오류 C3020

' var ': OpenMP ' for ' 루프의 인덱스 변수는 루프 본문에서 수정할 수 없습니다.

OpenMP **`for`** 루프가 루프 본문의 인덱스 (루프 카운터)를 수정할 수 없습니다 **`for`** .

다음 샘플에서는 C3020를 생성 합니다.

```cpp
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

[A.6 lastprivate](../../parallel/openmp/reference/openmp-clauses.md#lastprivate) 로 선언 된 변수는 병렬화 된 루프 내에서 인덱스로 사용할 수 없습니다.

다음 샘플에서는 a.6 lastprivate이 가장 바깥쪽 for 루프 내에서 idx_a에 대 한 쓰기를 트리거하기 때문에 두 번째 a.6 lastprivate에 대해 C3020을 제공 합니다. A.6 lastprivate은 가장 바깥쪽 for 루프 외부의 idx_a에 대 한 쓰기를 트리거하기 때문에 첫 번째 a.6 lastprivate은 오류를 제공 하지 않습니다 (기술적으로 마지막 반복이 끝날 때). 다음 샘플에서는 C3020를 생성 합니다.

```cpp
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```
