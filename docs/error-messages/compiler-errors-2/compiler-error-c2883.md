---
description: '자세한 정보: 컴파일러 오류 C2883'
title: 컴파일러 오류 C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 2ff905f5f1ca8fea4f175799e576e4538bbab164
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332346"
---
# <a name="compiler-error-c2883"></a>컴파일러 오류 C2883

' name ': 함수 선언이 using 선언에 의해 도입 된 ' identifier '와 충돌 합니다.

함수를 두 번 이상 정의 하려고 했습니다. 첫 번째 정의는 선언을 사용 하 여 네임 스페이스에서 만들어졌습니다 **`using`** . 두 번째는 로컬 정의입니다.

다음 샘플에서는 C2883를 생성 합니다.

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
