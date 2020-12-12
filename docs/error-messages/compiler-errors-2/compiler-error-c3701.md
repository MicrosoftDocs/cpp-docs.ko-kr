---
description: '자세한 정보: 컴파일러 오류 C3701'
title: 컴파일러 오류 C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: 8ebc8ac41091770a59876fb829d86997d7f5709c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228692"
---
# <a name="compiler-error-c3701"></a>컴파일러 오류 C3701

' function ': event_source에 이벤트가 없습니다.

이벤트 메서드가 없는 클래스에서 [event_source](../../windows/attributes/event-source.md) 를 사용 하려고 했습니다. 이 오류를 해결 하려면 하나 이상의 이벤트를 클래스에 추가 합니다.

다음 샘플에서는 C3701를 생성 합니다.

```cpp
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```
