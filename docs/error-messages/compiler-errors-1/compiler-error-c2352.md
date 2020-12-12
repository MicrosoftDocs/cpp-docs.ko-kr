---
description: '자세한 정보: 컴파일러 오류 C2352'
title: 컴파일러 오류 C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: f8094261c4a0ad23b5603d1e16bbaa4f34e0038e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298307"
---
# <a name="compiler-error-c2352"></a>컴파일러 오류 C2352

'class::function': 비정적 멤버 함수를 잘못 호출했습니다.

**`static`** 멤버 함수는 비정적 멤버 함수를 호출 했습니다. 또는 비정적 멤버 함수가 클래스 외부에서 정적 함수로 호출되었습니다.

다음 샘플에서는 C2352를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

다음 샘플에서는 C2352를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```
