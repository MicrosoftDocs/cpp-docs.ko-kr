---
description: '자세한 정보: 컴파일러 오류 C3656'
title: 컴파일러 오류 C3656
ms.date: 11/04/2016
f1_keywords:
- C3656
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
ms.openlocfilehash: ad87b989bf0e094a011ac5451745d5d296a0c223
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134435"
---
# <a name="compiler-error-c3656"></a>컴파일러 오류 C3656

' override ': 재정의 지정자를 반복할 수 없습니다.

명시적 override 키워드는 한 번만 지정할 수 있습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3656를 생성 합니다.

```cpp
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```
