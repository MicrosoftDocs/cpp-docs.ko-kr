---
description: '자세한 정보: 컴파일러 오류 C3364'
title: 컴파일러 오류 C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: e500b984489de1dfc2cd68d91ac5cb457d3887f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150854"
---
# <a name="compiler-error-c3364"></a>컴파일러 오류 C3364

' delegate ': 대리자 생성자: 인수는 관리 되는 클래스 또는 전역 함수의 멤버 함수에 대 한 포인터 여야 합니다.

대리자 생성자의 두 번째 매개 변수는 멤버 함수의 주소 또는 클래스의 정적 멤버 함수 주소를 사용 합니다. 둘 다 단순 주소로 처리 됩니다.

다음 샘플에서는 C3364를 생성 합니다.

```cpp
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
