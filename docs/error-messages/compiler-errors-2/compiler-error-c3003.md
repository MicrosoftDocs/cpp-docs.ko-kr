---
description: '자세한 정보: 컴파일러 오류 C3003'
title: 컴파일러 오류 C3003
ms.date: 11/04/2016
f1_keywords:
- C3003
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
ms.openlocfilehash: 1bed98ebd9e0a383700583e1e23e0a977cb6e3fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326045"
---
# <a name="compiler-error-c3003"></a>컴파일러 오류 C3003

'directive': 지시문 절 다음에는 OpenMP 지시문 이름이 올 수 없습니다.

OpenMP 지시문 이름이 OpenMP 지시문 절 다음에 올 수 없습니다.

다음 샘플에서는 C3003을 생성합니다.

```c
// C3003.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x, y, z) for   // C3003
}
```
