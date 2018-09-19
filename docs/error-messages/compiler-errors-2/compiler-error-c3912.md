---
title: 컴파일러 오류 C3912 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3912
dev_langs:
- C++
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26ffa49a6b54769db5b24d91ffcaf72579a6e458
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115257"
---
# <a name="compiler-error-c3912"></a>컴파일러 오류 C3912

'event': 형식의 이벤트는 대리자 형식 이어야 합니다.

이벤트 선언 된 하지만 적절 한 형식이 없습니다.

자세한 내용은 [이벤트](../../windows/event-cpp-component-extensions.md)합니다.

다음 샘플에서는 C3912 오류가 생성 됩니다.

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```