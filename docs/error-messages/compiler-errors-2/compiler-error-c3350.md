---
description: '자세한 정보: 컴파일러 오류 C3350'
title: 컴파일러 오류 C3350
ms.date: 11/04/2016
f1_keywords:
- C3350
helpviewer_keywords:
- C3350
ms.assetid: cfbbc338-92b5-4f34-999e-aa2d2376bc70
ms.openlocfilehash: edda71fdf8f1160d17099a7cee228a053ddd881b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326016"
---
# <a name="compiler-error-c3350"></a>컴파일러 오류 C3350

'delegate': 대리 생성자에 인수가 number개 있어야 합니다.

대리자 인스턴스를 만드는 경우 인수 두 개, 대리자 함수를 포함하는 형식 인스턴스 및 함수를 전달해야 합니다.

다음 샘플에서는 C3350을 생성합니다.

```cpp
// C3350.cpp
// compile with: /clr
delegate void SumDelegate();

public ref class X {
public:
   void F() {}
   static void F2() {}
};

int main() {
   X ^ MyX = gcnew X();
   SumDelegate ^ pSD = gcnew SumDelegate();   // C3350
   SumDelegate ^ pSD1 = gcnew SumDelegate(MyX, &X::F);
   SumDelegate ^ pSD2 = gcnew SumDelegate(&X::F2);
}
```
