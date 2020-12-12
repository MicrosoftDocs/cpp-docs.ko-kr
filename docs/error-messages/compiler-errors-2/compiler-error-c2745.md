---
description: '자세한 정보: 컴파일러 오류 C2745'
title: 컴파일러 오류 C2745
ms.date: 11/04/2016
f1_keywords:
- C2745
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
ms.openlocfilehash: 3f80ce1c13e8f1beeaa241e0638dfc9de784c3fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123034"
---
# <a name="compiler-error-c2745"></a>컴파일러 오류 C2745

' token ':이 토큰을 식별자로 변환할 수 없습니다.

식별자는 올바른 문자로 구성 되어야 합니다.

다음 샘플에서는 C2745를 생성 합니다.

```cpp
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```
