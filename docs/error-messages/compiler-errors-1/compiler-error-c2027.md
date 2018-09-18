---
title: 컴파일러 오류 C2027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69aae289fbab56cd77e544118909b2d7ef72ae0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032044"
---
# <a name="compiler-error-c2027"></a>컴파일러 오류 C2027

정의 되지 않은 형식 'type' 사용

형식 정의 될 때까지 사용할 수 없습니다. 이 오류를 해결 하려면 형식 참조 하기 전에 완전히 정의 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2027 오류가 발생 합니다.

```
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

선언 되지만 정의 되지 않은 형식에 대 한 포인터를 선언 하는 것이 가능 합니다.  하지만 Visual c + +는 정의 되지 않은 형식에 대 한 참조를 허용 하지 않습니다.

다음 샘플에서는 C2027 오류가 발생 합니다.

```
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