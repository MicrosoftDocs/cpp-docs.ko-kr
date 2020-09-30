---
title: 컴파일러 오류 C3052
ms.date: 11/04/2016
f1_keywords:
- C3052
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
ms.openlocfilehash: 40857432e07baffea69d8201cc3e0241698c93da
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506207"
---
# <a name="compiler-error-c3052"></a>컴파일러 오류 C3052

'var': default(none) 절 밑의 데이터 공유 절에 변수가 없습니다.

[default(none)](../../parallel/openmp/reference/openmp-clauses.md#default-openmp) 가 사용되는 경우 구조화된 블록에 사용되는 모든 변수가 [shared](../../parallel/openmp/reference/openmp-clauses.md#shared-openmp) 또는 [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp)으로 명시적으로 지정되어야 합니다.

다음 샘플에서는 C3052를 생성합니다.

```cpp
// C3052.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(none) // shared(n1) private(n1)
   {
      n1 = 0;   // C3052 use either a shared or private clause
   }
}
```
