---
description: '자세한 정보: 컴파일러 오류 C3912'
title: 컴파일러 오류 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: 5c7828fa055aff08ea57759bdf3ee9b9677cc0f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144068"
---
# <a name="compiler-error-c3912"></a>컴파일러 오류 C3912

' event ': 이벤트 형식이 대리자 형식 이어야 합니다.

이벤트가 선언 되었지만 적절 한 형식이 아닙니다.

자세한 내용은 [이벤트](../../extensions/event-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3912를 생성 합니다.

```cpp
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```
