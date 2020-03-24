---
title: 컴파일러 경고(수준 1) C4813
ms.date: 11/04/2016
f1_keywords:
- C4813
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
ms.openlocfilehash: c63539b14041a8615b0a5ad99932c0d44a4942b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174897"
---
# <a name="compiler-warning-level-1-c4813"></a>컴파일러 경고(수준 1) C4813

'function': 지역 클래스의 friend 함수를 미리 선언해야 합니다.

내부 클래스의 friend 함수가 외부 클래스에서 선언되지 않았습니다.

다음 샘플에서는 C4813을 생성합니다.

```cpp
// C4813.cpp
// compile with: /W1 /LD
void MyClass()
{
   // void func();
   class InnerClass
   {
      friend void func();   // C4813 uncomment declaration above
   };
}
```
