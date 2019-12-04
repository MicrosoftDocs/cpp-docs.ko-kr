---
title: 컴파일러 오류 C3890
ms.date: 11/04/2016
f1_keywords:
- C3890
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
ms.openlocfilehash: 8d93afa2ac8e365eff2f9256235b391f561cb977
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736544"
---
# <a name="compiler-error-c3890"></a>컴파일러 오류 C3890

' var ': 리터럴 데이터 멤버의 주소를 가져올 수 없습니다.

가비지 수집 힙에 리터럴 데이터 멤버가 있습니다.  가비지 수집 힙의 개체는 이동할 수 있으므로 주소를 가져오는 것은 유용 하지 않습니다.

다음 샘플에서는 C3890를 생성 합니다.

```cpp
// C3890.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   int p = &Y1::staticConst;   // C3890
   int p2 = Y1::staticConst;   // OK
}
```
