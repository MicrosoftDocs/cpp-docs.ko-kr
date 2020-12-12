---
description: '자세한 정보: 컴파일러 오류 C3254'
title: 컴파일러 오류 C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 7d0084f52060803cd99b973c9f6105fc8915c2aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194217"
---
# <a name="compiler-error-c3254"></a>컴파일러 오류 C3254

' explicit override ': 클래스에 명시적 재정의 ' override '가 포함 되어 있지만 함수 선언을 포함 하는 인터페이스에서 파생 되지 않습니다.

메서드를 [명시적으로 재정의할](../../cpp/explicit-overrides-cpp.md) 때 재정의를 포함 하는 클래스가 재정의 하는 함수를 포함 하는 형식에서 직접 또는 간접적으로 파생 되어야 합니다.

다음 샘플에서는 C3254를 생성 합니다.

```cpp
// C3254.cpp
__interface I
{
   void f();
};

__interface I1 : I
{
};

struct A /* : I1 */
{
   void I1::f()
   {   // C3254, uncomment : I1 to resolve this C3254
   }
};

int main()
{
}
```
