---
title: 컴파일러 오류 C2745
ms.date: 11/04/2016
f1_keywords:
- C2745
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
ms.openlocfilehash: 53a218fd80c6b8261aa0dda6bcaa1c347db73458
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563998"
---
# <a name="compiler-error-c2745"></a>컴파일러 오류 C2745

'token':이 토큰을 식별자로 변환할 수 없습니다

식별자는 유효한 문자 구성 해야 합니다.

다음 샘플에서는 C2745 오류가 생성 됩니다.

```
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```