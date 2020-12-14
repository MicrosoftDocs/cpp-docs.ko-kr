---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4521'
title: 컴파일러 경고(수준 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: ff4f565fb243fb5dd2df165ed5f3e3b1baf40c5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297410"
---
# <a name="compiler-warning-level-3-c4521"></a>컴파일러 경고(수준 3) C4521

' class ': 복사 생성자를 여러 개 지정 했습니다.

클래스에는 단일 형식의 여러 복사 생성자가 있습니다. 이 경고는 정보 제공 용입니다. 프로그램에서 생성자를 호출할 수 있습니다.

이 경고를 표시 하지 않으려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4521를 생성 합니다.

```cpp
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```
