---
title: 컴파일러 오류 C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 11e5792344b6f8fba6183f4ab87e1799db803b46
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757945"
---
# <a name="compiler-error-c3704"></a>컴파일러 오류 C3704

' function ': vararg 메서드는 이벤트를 발생 시킬 수 없습니다.

Vararg 메서드에서 [__event](../../cpp/event.md) 를 사용 하려고 했습니다. 이 오류를 해결 하려면 다음 코드 샘플과 같이 `fireEvent(int i, ...)` 호출을 `fireEvent(int i)` 호출로 바꿉니다.

다음 샘플에서는 C3704를 생성 합니다.

```cpp
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```
