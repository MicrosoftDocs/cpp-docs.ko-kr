---
description: '자세한 정보: 컴파일러 오류 C 3005'
title: 컴파일러 오류 C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: df9e0c94aa0ba47e1c2f63858419c15881f9bd74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272424"
---
# <a name="compiler-error-c3005"></a>컴파일러 오류 C3005

'error_text': OpenMP 'directive' 지시문에 예기치 못한 토큰이 있습니다.

OpenMP 지시문 형식이 잘못되었습니다.

다음 샘플에서는 C3005를 생성합니다.

```c
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

C3005는 pragma와 같은 줄에 여는 중괄호를 배치하면 발생할 수 있습니다.

```c
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```
