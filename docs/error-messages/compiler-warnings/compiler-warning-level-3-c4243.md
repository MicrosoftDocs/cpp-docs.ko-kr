---
title: 컴파일러 경고 (수준 3) C4243
ms.date: 11/04/2016
f1_keywords:
- C4243
helpviewer_keywords:
- C4243
ms.assetid: ca72f9ad-ce0b-43a9-a68c-106e1f8b90ef
ms.openlocfilehash: ed5cc87f1bc376526f5129aa157c38a3f034b20b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051738"
---
# <a name="compiler-warning-level-3-c4243"></a>컴파일러 경고 (수준 3) C4243

' 변환 형식 ' 변환이 ' type1 '에서 ' type2 ' (으)로의 변환이 있지만 액세스할 수 없습니다.

파생 클래스에 대 한 포인터는 기본 클래스에 대 한 포인터로 변환 되지만 파생 클래스는 개인 또는 보호 된 액세스를 사용 하 여 기본 클래스를 상속 합니다.

다음 샘플에서는 C4243를 생성 합니다.

```cpp
// C4243.cpp
// compile with: /W3
// C4243 expected
struct B {
   int f() {
      return 0;
   };
};

struct D : private B {};
struct E : public B {};

int main() {
   // Delete the following 2 lines to resolve.
   int (D::* d)() = (int(D::*)()) &B::f;
   d;

   int (E::* e)() = (int(E::*)()) &B::f; // OK
   e;
}
```