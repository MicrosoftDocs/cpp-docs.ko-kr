---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4584'
title: 컴파일러 경고(수준 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 32a6b797f7fb0cf2c1a087999c8172e11686e27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281628"
---
# <a name="compiler-warning-level-1-c4584"></a>컴파일러 경고(수준 1) C4584

' class1 ': 기본 클래스 ' class2 '은 (는) 이미 ' a.winmd '의 기본 클래스입니다.

사용자가 정의한 클래스는 두 클래스에서 상속 되는데, 그 중 하나는 다른 클래스에서 상속 됩니다. 예를 들어:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

이 경우 클래스 C에서 경고가 발생 합니다. 클래스 B는 클래스 A에서 상속 되 고 클래스 B는 클래스 a 에서도 상속 하기 때문입니다. 이 경고는 이러한 기본 클래스의 멤버 사용을 완전히 정규화 해야 한다는 알림을 제공 하며, 참조 하는 클래스 멤버의 모호성으로 인해 컴파일러 오류가 생성 됩니다.
