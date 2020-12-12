---
description: '자세한 정보: 컴파일러 오류 C3002'
title: 컴파일러 오류 C3002
ms.date: 11/04/2016
f1_keywords:
- C3002
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
ms.openlocfilehash: 00984b6d3ed0845dd532f82462d9c44f6893a846
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326058"
---
# <a name="compiler-error-c3002"></a>컴파일러 오류 C3002

'name1 name2': OpenMP 지시문 이름이 여러 개 있습니다.

여러 지시문 이름은 허용되지 않습니다.

다음 샘플에서는 C3002를 생성합니다.

```c
// C3002.c
// compile with: /openmp
int main()
{
   #pragma omp parallel single   // C3002
}
```
