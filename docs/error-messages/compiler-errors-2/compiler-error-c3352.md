---
description: '자세한 정보: 컴파일러 오류 C3352'
title: 컴파일러 오류 C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: 66d6921c86c6b7a30026880f01ab2a5dada11a65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150945"
---
# <a name="compiler-error-c3352"></a>컴파일러 오류 C3352

' function ': 지정한 함수가 ' type ' 대리자 형식과 일치 하지 않습니다.

에 대 한 매개 변수가 목록에 `function` 있고 대리자가 일치 하지 않습니다.

자세한 내용은 [delegate (c + + 구성 요소 확장)](../../extensions/delegate-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3352를 생성 합니다.

```cpp
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
