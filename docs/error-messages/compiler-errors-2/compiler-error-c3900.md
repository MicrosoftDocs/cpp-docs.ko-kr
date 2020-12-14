---
description: '자세한 정보: 컴파일러 오류 C3900'
title: 컴파일러 오류 C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 7b210eb6369b8953f36821d45690de8656113af2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238936"
---
# <a name="compiler-error-c3900"></a>컴파일러 오류 C3900

' member ': 현재 범위에서 사용할 수 없습니다.

속성 블록은 함수 선언과 인라인 함수 정의만 포함할 수 있습니다. 속성 블록에는 함수 이외의 멤버를 사용할 수 없습니다. 형식 정의, 연산자 또는 friend 함수는 허용 되지 않습니다. 자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md)을 참조하세요.

이벤트 정의에는 액세스 메서드와 함수만 포함 될 수 있습니다.

다음 샘플에서는 C3900를 생성 합니다.

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

다음 샘플에서는 C3900를 생성 합니다.

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
