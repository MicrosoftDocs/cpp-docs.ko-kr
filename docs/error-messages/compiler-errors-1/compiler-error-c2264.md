---
description: '자세한 정보: 컴파일러 오류 C2264'
title: 컴파일러 오류 C2264
ms.date: 11/04/2016
f1_keywords:
- C2264
helpviewer_keywords:
- C2264
ms.assetid: 158b72cc-cee9-4a08-bd79-b7a5955345a8
ms.openlocfilehash: a838271897db7a1ce553e6e9ea0d3f3e0c985a9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328420"
---
# <a name="compiler-error-c2264"></a>컴파일러 오류 C2264

' function ': 함수 정의 또는 선언에 오류가 있습니다. 함수를 호출 하지 않았습니다.

잘못 된 정의 또는 선언으로 인해 함수를 호출할 수 없습니다.

다음 샘플에서는 C2264를 생성 합니다.

```cpp
// C2264.cpp
struct C {
   // Delete the following line to resolve.
   operator int(int = 0){}   // incorrect declaration
};

struct D {
   operator int(){return 0;}   // OK
};

int main() {
   int i;

   C c;
   i = c;   // C2264

   D d;
   i = d;   // OK
}
```
