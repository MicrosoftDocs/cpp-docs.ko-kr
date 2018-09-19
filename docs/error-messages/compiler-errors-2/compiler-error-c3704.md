---
title: 컴파일러 오류 C3704 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3704
dev_langs:
- C++
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4504534e3a53f37089f0b0ba045b7afde5a8065d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054989"
---
# <a name="compiler-error-c3704"></a>컴파일러 오류 C3704

'function': vararg 메서드 이벤트를 발생 시킬 수 없습니다.

사용 하려는 [__event](../../cpp/event.md) vararg 메서드. 이 오류를 해결 하려면 대체는 `fireEvent(int i, ...)` 호출을 `fireEvent(int i)` 다음 코드 예제와 같이 호출 합니다.

다음 샘플에서는 C3704 오류가 생성 됩니다.

```
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