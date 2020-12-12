---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4927'
title: 컴파일러 경고(수준 1) C4927
ms.date: 11/04/2016
f1_keywords:
- C4927
helpviewer_keywords:
- C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
ms.openlocfilehash: ddd131a5b87004fba56e80adbe5d9bea263f376a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301869"
---
# <a name="compiler-warning-level-1-c4927"></a>컴파일러 경고(수준 1) C4927

변환이 잘못 되었습니다. 사용자 정의 변환이 암시적으로 두 번 이상 적용 되었습니다.

두 개 이상의 사용자 정의 변환이 암시적으로 단일 값에 적용 됩니다. 컴파일러는 명시적 변환을 찾지 못했지만 사용 된 변환을 찾습니다.

다음 샘플에서는 C4927를 생성 합니다.

```cpp
// C4927.cpp
// compile with: /W1
struct B
{
   operator int ()
   {
      return 0;
   }
};

struct A
{
   A(int i)
   {
   }

   /*
   // uncomment this constructor to resolve
   A(B b)
   {
   }
   */
};

A f1( B& b)
{
   return A(b);
}

B& f2( B& b)
{
   return b;
}

A f()
{
   B b;
   return A(b);   // ok
   return f1(b);  // ok
   return b;      // C4927
   return B(b);   // C4927
   return f2(b);  // C4927
}

int main()
{
   B b;
   A a = b;
   A a2(b);
}
```
