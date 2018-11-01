---
title: 컴파일러 경고(수준 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: b1a7d715057f4c6d8ada104ad07f6ad0b9c52fb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564637"
---
# <a name="compiler-warning-level-1-c4624"></a>컴파일러 경고(수준 1) C4624

'derived class': 기본 클래스의 소멸자에 액세스할 수 없거나 이러한 소멸자가 삭제되므로 소멸자가 암시적으로 삭제된 것으로 정의됩니다.

기본 클래스에서 소멸자에 액세스할 수 없거나 소멸자가 삭제되었으므로 파생 클래스에 대해 생성되지 않습니다. 스택에 이 형식의 개체를 만들려고 하면 컴파일러 오류가 발생합니다.

다음 샘플에서는 C4624를 생성하고 해결 방법을 보여 줍니다.

```
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```