---
description: '자세한 정보: 컴파일러 오류 C2635'
title: 컴파일러 오류 C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 8ecc6faaefb3dea5f0cfcded4d6817a807580254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123385"
---
# <a name="compiler-error-c2635"></a>컴파일러 오류 C2635

' identifier1 * '를 ' identifier2 '로 변환할 수 없습니다 \* . 가상 기본 클래스에서의 변환이 암시 됩니다.

변환 하려면 기본 클래스에서 파생 클래스로 캐스트를 사용 해야 **`virtual`** 합니다 .이는 허용 되지 않습니다.

다음 샘플에서는 C2635를 생성 합니다.

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
