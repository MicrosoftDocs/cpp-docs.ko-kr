---
description: '자세한 정보: 컴파일러 오류 C3034'
title: 컴파일러 오류 C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: 379fedfe3af65b2def83d737daeccac670838c2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270175"
---
# <a name="compiler-error-c3034"></a>컴파일러 오류 C3034

OpenMP 'directive1' 지시문은 'directive2' 지시문 내부에 직접 중첩될 수 없습니다.

일부 지시문은 중첩될 수 없습니다. 이 오류를 해결하려면 두 지시문의 문을 하나의 지시문 블록으로 병합하거나 연속 지시문을 생성할 수 있습니다.

다음 샘플에서는 C3034를 생성합니다.

```cpp
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```
