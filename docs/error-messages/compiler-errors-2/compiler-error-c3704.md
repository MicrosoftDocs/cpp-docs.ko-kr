---
description: '자세한 정보: 컴파일러 오류 C3704'
title: 컴파일러 오류 C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: aae489b2d8657a1e62adc654d148be6cd0403af1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278183"
---
# <a name="compiler-error-c3704"></a>컴파일러 오류 C3704

' function ': vararg 메서드는 이벤트를 발생 시킬 수 없습니다.

Vararg 메서드에서 [__event](../../cpp/event.md) 를 사용 하려고 했습니다. 이 오류를 해결 하려면 `fireEvent(int i, ...)` 다음 코드 샘플과 같이 호출을 호출로 바꿉니다 `fireEvent(int i)` .

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
