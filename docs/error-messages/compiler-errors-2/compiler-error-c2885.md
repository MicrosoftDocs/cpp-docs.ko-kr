---
description: '자세한 정보: 컴파일러 오류 C2885'
title: 컴파일러 오류 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 040f7a151c34fe7b5e30b6aad1e5bc956b3e5cf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337487"
---
# <a name="compiler-error-c2885"></a>컴파일러 오류 C2885

' class:: identifier ': 클래스 범위가 아닌 범위에서 올바른 using 선언이 아닙니다.

[Using](../../cpp/using-declaration.md) 선언을 잘못 사용 했습니다.

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. 더 이상 중첩 형식에 대 한 선언을 사용할 수 없습니다 **`using`** . 중첩 된 형식에 대 한 각 참조를 명시적으로 한정 하거나, 네임 스페이스에 형식을 넣거나, typedef를 만들어야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2885를 생성 합니다.

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

**`using`** 키워드를 클래스 멤버와 함께 사용 하는 경우 c + +에서는 다른 클래스 (파생 클래스) 내에서 해당 멤버를 정의 해야 합니다.

다음 샘플에서는 C2885를 생성 합니다.

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
