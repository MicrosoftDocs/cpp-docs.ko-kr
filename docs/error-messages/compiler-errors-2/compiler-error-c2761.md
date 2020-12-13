---
description: '자세한 정보: 컴파일러 오류 C2761'
title: 컴파일러 오류 C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 624a375aedc78b6d63f3a6c5a1185edfade28c7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336153"
---
# <a name="compiler-error-c2761"></a>컴파일러 오류 C2761

' function ': 멤버 함수를 재선언 할 수 없습니다.

멤버 함수는 다시 선언할 수 없습니다. 이를 정의할 수 있지만 다시 선언할 수는 없습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2761를 생성 합니다.

```cpp
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

클래스 또는 구조체의 비정적 멤버를 정의할 수 없습니다.  다음 샘플에서는 C2761를 생성 합니다.

```cpp
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```
