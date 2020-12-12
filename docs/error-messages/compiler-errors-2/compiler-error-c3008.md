---
description: '자세한 정보: 컴파일러 오류 C3008'
title: 컴파일러 오류 C3008
ms.date: 11/04/2016
f1_keywords:
- C3008
helpviewer_keywords:
- C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
ms.openlocfilehash: 30ec8602ba9759eded7edc642931109216a68967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305340"
---
# <a name="compiler-error-c3008"></a>컴파일러 오류 C3008

'arg': OpenMP 'directive' 지시문의 인수에 닫는 ')'가 없습니다.

인수를 사용하는 OpenMP 지시문에 닫는 괄호가 없습니다.

다음 샘플에서는 C3008을 생성합니다.

```c
// C3008.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x   // C3008
   // Try the following line instead:
   #pragma omp parallel shared(x)
   {
   }
}
```
