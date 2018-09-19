---
title: 컴파일러 오류 C3748 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3748
dev_langs:
- C++
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31b2d0434ec48f0c1d7ecf767ce2746e2c603401
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116856"
---
# <a name="compiler-error-c3748"></a>컴파일러 오류 C3748

'interface': 관리 되는 인터페이스 이벤트를 발생 하지 않을 수 있습니다

합니다 [__event](../../cpp/event.md) 키워드는 인터페이스 내에서 사용할 수 없습니다.

다음 샘플에서는 C3748 오류가 생성 됩니다.

```
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```