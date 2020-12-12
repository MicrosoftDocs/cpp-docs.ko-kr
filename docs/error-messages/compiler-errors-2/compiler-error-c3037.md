---
description: '자세한 정보: 컴파일러 오류 C3037'
title: 컴파일러 오류 C3037
ms.date: 11/04/2016
f1_keywords:
- C3037
helpviewer_keywords:
- C3037
ms.assetid: 9ba8a890-d3c7-4cce-93c5-d358e2bfad28
ms.openlocfilehash: f8ccf87ca09aaf90fb07b197279e994eeb27f249
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270058"
---
# <a name="compiler-error-c3037"></a>컴파일러 오류 C3037

'var': 'reduction' 절의 변수는 바깥쪽 컨텍스트에서 shared여야 합니다.

[reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 절에 지정된 변수는 컨텍스트의 각 스레드에 private일 수 없습니다.

다음 샘플에서는 C3037을 생성합니다.

```cpp
// C3037.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel private(g_i)
   // try the following line instead
   // #pragma omp parallel
   {
      #pragma omp for reduction(+:g_i)   // C3037
      for (i = 0 ; i < 10 ; ++i) {
         g_i += i;
      }
   }
}
```
