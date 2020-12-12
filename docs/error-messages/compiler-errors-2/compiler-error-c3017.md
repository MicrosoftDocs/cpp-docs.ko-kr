---
description: '자세한 정보: 컴파일러 오류 C3017'
title: 컴파일러 오류 C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: bbfffbb9d9f9b0c34dbf0dab57c28d7fd6892fd9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285840"
---
# <a name="compiler-error-c3017"></a>컴파일러 오류 C3017

OpenMP 'for' 문의 종료 테스트 형식이 잘못되었습니다.

**`for`** OpenMP 문의 루프는 완전 하 고 명시적으로 지정 되어야 합니다.

다음 샘플에서는 C3017을 생성합니다.

```cpp
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```
