---
description: '자세한 정보: 컴파일러 오류 C2079'
title: 컴파일러 오류 C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 73ca5d334ac3bf3157b61a1b2a9489282ae1fe00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151218"
---
# <a name="compiler-error-c2079"></a>컴파일러 오류 C2079

' identifier '는 정의 되지 않은 클래스/구조체/공용 구조체 ' 이름 '을 사용 합니다.

지정 된 식별자는 정의 되지 않은 클래스, 구조체 또는 공용 구조체입니다.

이 오류는 익명 공용 구조체를 초기화 하 여 발생할 수 있습니다.

다음 샘플에서는 C2079를 생성 합니다.

```cpp
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

해결 방법:

```cpp
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

또한 전방 선언이 범위에만 있는 형식의 스택에서 개체를 선언 하려고 하면 C2079이 발생할 수 있습니다.

```cpp
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

해결 방법:

```cpp
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```
