---
description: '자세한 정보: 컴파일러 오류 C2784'
title: 컴파일러 오류 C2784
ms.date: 11/04/2016
f1_keywords:
- C2784
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
ms.openlocfilehash: dcee0cc2c6c8154bafe4a37fe83c66b1c8d477d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297917"
---
# <a name="compiler-error-c2784"></a>컴파일러 오류 C2784

'declaration': 'type'의 템플릿 인수를 'type'에서 추론할 수 없습니다.

컴파일러가 제공된 함수 인수에서 템플릿 인수를 확인할 수 없습니다.

다음 샘플에서는 C2784를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2784.cpp
template<class T> class X {};
template<class T> void f(X<T>) {}

int main() {
   X<int> x;
   f(1);   // C2784

   // To fix it, try the following line instead
   f(x);
}
```
