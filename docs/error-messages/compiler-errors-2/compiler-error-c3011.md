---
description: '자세한 정보: 컴파일러 오류 C3011'
title: 컴파일러 오류 C3011
ms.date: 11/04/2016
f1_keywords:
- C3011
helpviewer_keywords:
- C3011
ms.assetid: 24c3a917-ebff-4deb-9155-23adf6468531
ms.openlocfilehash: 3a8591ad528c68bb5d072049e2b85567699fc5c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286035"
---
# <a name="compiler-error-c3011"></a>컴파일러 오류 C3011

병렬 영역 내부에서는 직접 인라인 어셈블리를 사용할 수 없습니다.

`omp` 병렬 영역은 인라인 어셈블리 명령을 포함할 수 없습니다.

다음 샘플에서는 C3011을 생성합니다.

```cpp
// C3011.cpp
// compile with: /openmp
// processor: /x86
int main() {
   int   n = 0;

   #pragma omp parallel
   {
      _asm mov eax, n   // Delete this line to resolve this error.
   }   // C3011
}
```
