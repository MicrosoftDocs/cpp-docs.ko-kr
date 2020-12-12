---
description: '자세한 정보: 컴파일러 오류 C2677'
title: 컴파일러 오류 C2677
ms.date: 11/04/2016
f1_keywords:
- C2677
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
ms.openlocfilehash: 6a7570fa972897658c9ffa81052148e9ce7cd6cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267809"
---
# <a name="compiler-error-c2677"></a>컴파일러 오류 C2677

이항 ' operator ': ' type ' 형식을 사용 하는 전역 연산자가 없거나 허용 되는 변환이 없습니다.

연산자를 사용하려면 지정된 형식에 대해 오버로드하거나 연산자가 정의된 형식으로의 변환을 정의해야 합니다.

다음 샘플에서는 C2677를 생성 합니다.

```cpp
// C2677.cpp
class C {
public:
   C(){}
} c;

class D {
public:
   D(){}
   operator int(){return 0;}
} d;

int main() {
   int i = 1 >> c;   // C2677
   int j = 1 >> d;   // OK operator int() defined
}
```
