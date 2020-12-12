---
description: '자세한 정보: 컴파일러 오류 C2594'
title: 컴파일러 오류 C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 972fb58624a7f2ba185c34f2e58fd9f2dc15217d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120154"
---
# <a name="compiler-error-c2594"></a>컴파일러 오류 C2594

' operator ': ' type1 '에서 ' type2 ' (으)로의 변환이 모호 합니다.

*Type1* 에서 *type2* 로의 변환이 다른 것 보다 더 직접적 이었습니다. *Type1* 에서 *type2* 로 변환할 수 있는 두 가지 솔루션을 제안 합니다. 첫 번째 옵션은 *type1* 에서 *type2* 로의 직접 변환을 정의 하는 것이 고 두 번째 옵션은 *type1* 에서 *type2* 로의 변환 시퀀스를 지정 하는 것입니다.

다음 샘플에서는 C2594를 생성 합니다. 오류에 대 한 권장 해결 방법은 변환의 시퀀스입니다.

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
