---
title: 컴파일러 오류 C2450 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2450
dev_langs:
- C++
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7402e538da4b538792a21d87208c954d1ce31777
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082533"
---
# <a name="compiler-error-c2450"></a>컴파일러 오류 C2450

'type' 형식의 switch 식은 올바르지 않습니다.

`switch` 식이 잘못 된 형식입니다. 정수 형식 또는 클래스 형식으로 계산 되어야 정수 형식으로 명확한 변환을 사용 하 여 합니다. 이 사용자 정의 형식으로 계산 되 면 변환 연산자를 제공 해야 합니다.

다음 샘플에서는 C2450를 생성합니다.

```
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```