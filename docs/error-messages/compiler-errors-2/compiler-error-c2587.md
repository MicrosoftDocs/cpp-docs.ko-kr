---
description: '자세한 정보: 컴파일러 오류 C2587'
title: 컴파일러 오류 C2587
ms.date: 11/04/2016
f1_keywords:
- C2587
helpviewer_keywords:
- C2587
ms.assetid: 7637a2c7-35d4-4b5a-a8f2-515a7bda98fd
ms.openlocfilehash: a5d447f2e1a08c310fdd5c2d42afef768f191f4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177603"
---
# <a name="compiler-error-c2587"></a>컴파일러 오류 C2587

' identifier ': 지역 변수를 기본 매개 변수로 잘못 사용 했습니다.

지역 변수는 기본 매개 변수로 사용할 수 없습니다.

다음 샘플에서는 C2587를 생성 합니다.

```cpp
// C2587.cpp
// compile with: /c
int i;
void func() {
   int j;
   extern void func2( int k = j );  // C2587 -- local variable
   extern void func3( int k = i );   // OK
}
```
