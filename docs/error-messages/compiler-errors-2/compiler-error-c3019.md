---
description: '자세한 정보: 컴파일러 오류 C3019'
title: 컴파일러 오류 C3019
ms.date: 11/04/2016
f1_keywords:
- C3019
helpviewer_keywords:
- C3019
ms.assetid: 31a6d9b6-d29f-4499-9ad8-48dd751e87c7
ms.openlocfilehash: d2f07eabdbe0694e2c227cace26ac81f3a5dc237
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285788"
---
# <a name="compiler-error-c3019"></a>컴파일러 오류 C3019

OpenMP ' for ' 문의 증가값 형식이 잘못 되었습니다.

OpenMP 루프의 증분 부분은 **`for`** 연산자의 왼쪽과 오른쪽에 모두 인덱스 변수를 사용 해야 합니다.

다음 샘플에서는 C3019를 생성 합니다.

```cpp
// C3019.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 1, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i = j + n)   // C3019
      // Try the following line instead:
      // for (i = 0; i < 10; i++)
         j *= 2;
   }
}
```
