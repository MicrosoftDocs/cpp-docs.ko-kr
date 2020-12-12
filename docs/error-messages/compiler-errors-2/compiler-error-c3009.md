---
description: '자세한 정보: 컴파일러 오류 C3009'
title: 컴파일러 오류 C3009
ms.date: 11/04/2016
f1_keywords:
- C3009
helpviewer_keywords:
- C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
ms.openlocfilehash: fd261901293fd002465f4767f2b4389e1c388614
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305327"
---
# <a name="compiler-error-c3009"></a>컴파일러 오류 C3009

'label': OpenMP 구조화된 블록 외부에서 내부로 점프할 수 없습니다.

코드가 OpenMP 블록 안이나 밖으로 점프할 수 없습니다.

다음 샘플에서는 C3009를 생성합니다.

```c
// C3009.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
   lbl2:;
   }
   goto lbl2;   // C3009
}
```
