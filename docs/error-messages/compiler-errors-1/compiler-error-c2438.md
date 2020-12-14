---
description: '자세한 정보: 컴파일러 오류 C2438'
title: 컴파일러 오류 C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: 1400ee013e5d507f7fdfe288b97db10ec8216085
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189888"
---
# <a name="compiler-error-c2438"></a>컴파일러 오류 C2438

' identifier ': 생성자를 통해 정적 클래스 데이터를 초기화할 수 없습니다.

생성자는 클래스의 정적 멤버를 초기화 하는 데 사용 됩니다. 정적 멤버는 클래스 선언 외부의 정의에서 초기화 해야 합니다.

다음 샘플에서는 C2438를 생성 합니다.

```cpp
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```
