---
description: '자세한 정보: 컴파일러 오류 C2552'
title: 컴파일러 오류 C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: bd028af17ac5535eb1f72acf053dda193d4cc636
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134526"
---
# <a name="compiler-error-c2552"></a>컴파일러 오류 C2552

'identifier': 이니셜라이저 목록을 사용하여 비 집합체를 초기화할 수 없습니다.

집합체 식별자가 잘못 초기화되었습니다.

[집계](../../c-language/initializing-aggregate-types.md) 는 다음과 같이 정의 됩니다.

- 배열

- 다음을 갖지 않은 클래스, 구조체 및 공용 구조체

  - 생성자

  - 전용 또는 보호된 멤버

  - 기본 클래스

  - 가상 함수

또한 Visual C++는 생성자를 포함하는 집합체에서 데이터 형식을 허용하지 않습니다.

다음은 형식에서 집합체 초기화를 시도할 경우 C2552가 실행될 수 있는 이유를 나타냅니다.

- 형식에 하나 이상의 사용자 정의 생성자가 있습니다.

- 형식에 하나 이상의 비정적 전용 데이터 멤버가 있습니다.

- 형식에 가상 함수가 하나 이상 있습니다.

- 형식에 기본 클래스가 있습니다.

- 형식이 ref 클래스 또는 CLR 인터페이스입니다.

- 형식에 요소가 소멸자인 고정되지 않은 차원 배열(0 배열)이 있습니다.

다음 샘플에서는 C2552 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
