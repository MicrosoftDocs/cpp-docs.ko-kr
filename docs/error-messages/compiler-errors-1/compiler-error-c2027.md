---
title: 컴파일러 오류 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751003"
---
# <a name="compiler-error-c2027"></a>컴파일러 오류 C2027

정의 되지 않은 형식 ' type ' 사용

형식은 정의 될 때까지 사용할 수 없습니다. 오류를 해결 하려면 형식을 참조 하기 전에 형식이 완전히 정의 되어 있어야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2027를 생성 합니다.

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>예제

선언 되었지만 정의 되지 않은 형식에 대 한 포인터를 선언할 수 있습니다. 그러나 C++ 는 정의 되지 않은 형식에 대 한 참조를 허용 하지 않습니다.

다음 샘플에서는 C2027를 생성 합니다.

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
