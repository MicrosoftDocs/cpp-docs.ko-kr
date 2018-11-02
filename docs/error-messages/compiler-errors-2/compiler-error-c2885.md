---
title: 컴파일러 오류 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652129"
---
# <a name="compiler-error-c2885"></a>컴파일러 오류 C2885

'class::identifier': 하지 유효한 using 선언 비 클래스 범위의

사용 하는 [를 사용 하 여](../../cpp/using-declaration.md) 선언 잘못 됩니다.

## <a name="example"></a>예제

이 오류는 Visual c + + 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 없습니다: 필요가 더 이상 유효를 `using` 중첩된 형식이 선언 이름을에 형식을 배치 하는 중첩된 형식에 대 한 각 참조를 명시적으로 한 정해야 공간 또는 형식 정의 만듭니다.

다음 샘플 C2885를 생성합니다.

```
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

## <a name="example"></a>예제

사용 하는 경우는 `using` 키워드는 클래스 멤버를 c + +를 사용 하 여 다른 클래스 (파생된 클래스) 내에서 해당 멤버를 정의 해야 합니다.

다음 샘플 C2885를 생성합니다.

```
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