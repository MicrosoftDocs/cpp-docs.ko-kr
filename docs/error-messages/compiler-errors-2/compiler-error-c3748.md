---
description: '자세한 정보: 컴파일러 오류 C3748'
title: 컴파일러 오류 C3748
ms.date: 11/04/2016
f1_keywords:
- C3748
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
ms.openlocfilehash: f4cb51cfbb331867c18c0f892bd9527309fb4d63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340192"
---
# <a name="compiler-error-c3748"></a>컴파일러 오류 C3748

' interface ': 관리 되는 인터페이스가 이벤트를 발생 시킬 수 없습니다.

[__Event](../../cpp/event.md) 키워드는 인터페이스 안에 나타날 수 없습니다.

다음 샘플에서는 C3748를 생성 합니다.

```cpp
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```
