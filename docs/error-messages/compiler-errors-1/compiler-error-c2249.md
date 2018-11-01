---
title: 컴파일러 오류 C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f3f82549cf5d9230adfee7e83248e92f8e93e769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555634"
---
# <a name="compiler-error-c2249"></a>컴파일러 오류 C2249

'member': 가상 기본 'class'에 선언 된 멤버에 액세스 액세스할 수 없는 경로

합니다 `member` 비공용에서 상속 된 `virtual` 기본 클래스 또는 구조체입니다.

## <a name="example"></a>예제

다음 샘플 C2249를 생성합니다.

```
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

## <a name="example"></a>예제

C2249 다른 스트림에 스트림을 c + + 표준 라이브러리에서 할당 하려는 경우에 발생할 수 있습니다.  다음 샘플 C2249를 생성합니다.

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```