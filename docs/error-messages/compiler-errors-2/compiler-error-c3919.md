---
description: '자세한 정보: 컴파일러 오류 C3919'
title: 컴파일러 오류 C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 9f09c9ca29d247162da8f107ceb2ba47ee26bacc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143899"
---
# <a name="compiler-error-c3919"></a>컴파일러 오류 C3919

' event_method ': 함수는 ' type ' 형식 이어야 합니다.

이벤트 접근자 메서드가 올바르게 선언 되지 않았습니다.

이벤트에 대 한 자세한 내용은 [이벤트](../../extensions/event-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3919를 생성 합니다.

```cpp
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```
