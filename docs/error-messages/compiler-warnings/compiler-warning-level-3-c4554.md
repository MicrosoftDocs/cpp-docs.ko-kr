---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4554'
title: 컴파일러 경고(수준 3) C4554
ms.date: 11/04/2016
f1_keywords:
- C4554
helpviewer_keywords:
- C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
ms.openlocfilehash: daed8757cca5c9d9286f6f6bf94c55149c1687c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257838"
---
# <a name="compiler-warning-level-3-c4554"></a>컴파일러 경고(수준 3) C4554

' operator ': 연산자 우선 순위를 검사 하 여 가능한 오류를 확인 하십시오. 괄호를 사용 하 여 우선 순위를 명확 하 게 설명

다음 샘플에서는 C4554를 생성 합니다.

```cpp
// C4554.cpp
// compile with: /W3 /WX
int main() {
   int a = 0, b = 0, c = 0;
   a = a << b + c;   // C4554
   // probably intended (a << b) + c,
   // but will get a << (b + c)
}
```
