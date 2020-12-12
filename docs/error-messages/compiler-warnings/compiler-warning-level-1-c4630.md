---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4630'
title: 컴파일러 경고(수준 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 49a73dcd3ce11fefa1d4275e57ad98092c242d8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318912"
---
# <a name="compiler-warning-level-1-c4630"></a>컴파일러 경고(수준 1) C4630

' symbol ': 멤버 정의에는 ' extern ' 저장소 클래스 지정자를 사용할 때 잘못 되었습니다.

데이터 멤버 또는 멤버 함수는로 정의 됩니다 **`extern`** . 전체 개체가 가능 하더라도 멤버는 외부 일 수 없습니다. 컴파일러는 키워드를 무시 합니다 **`extern`** . 다음 샘플에서는 C4630를 생성 합니다.

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
