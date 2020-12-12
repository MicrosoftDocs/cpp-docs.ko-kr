---
description: '자세한 정보: 컴파일러 오류 C3060'
title: 컴파일러 오류 C3060
ms.date: 11/04/2016
f1_keywords:
- C3060
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
ms.openlocfilehash: a1efe037e75251ef452b0164a2b4e01ea4c38a1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281732"
---
# <a name="compiler-error-c3060"></a>컴파일러 오류 C3060

'member': friend 함수는 클래스 내부에서 정규화된 이름을 사용하여 정의할 수 없으며 선언만 할 수 있습니다.

Friend 함수가 정규화된 이름을 사용하여 정의되었으며 이는 허용되지 않습니다.

다음 샘플에서는 C3060을 생성합니다.

```cpp
// C3060.cpp
class A {
public:
   void func();
};

class C {
public:
   friend void A::func() { }   // C3060
   // Try the following line and the out of class definition:
   // friend void A::func();
};

// void A::func(){}
```
