---
title: 컴파일러 오류 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225477"
---
# <a name="compiler-error-c2464"></a>컴파일러 오류 C2464

' identifier ': ' n e w '를 사용 하 여 참조를 할당할 수 없습니다.

참조 식별자가 연산자를 사용 하 여 할당 되었습니다 **`new`** . 참조는 메모리 개체가 아니므로 **`new`** 포인터를 반환할 수 없습니다. 표준 변수 선언 구문을 사용 하 여 참조를 선언 합니다.

다음 샘플에서는 C2464를 생성 합니다.

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
