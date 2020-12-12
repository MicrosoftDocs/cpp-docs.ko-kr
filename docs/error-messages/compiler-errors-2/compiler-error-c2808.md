---
description: '자세한 정보: 컴파일러 오류 C2808'
title: 컴파일러 오류 C2808
ms.date: 11/04/2016
f1_keywords:
- C2808
helpviewer_keywords:
- C2808
ms.assetid: 3d745102-d3b3-4735-a7d2-ad42d5bf3cfa
ms.openlocfilehash: bdc47ff480afa77c22784536c1ed6337358e3d87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320576"
---
# <a name="compiler-error-c2808"></a>컴파일러 오류 C2808

단항 ' operator operator '에 정식 매개 변수가 너무 많습니다.

단항 연산자에는 비 void 매개 변수 목록이 있습니다.

다음 샘플에서는 C2808를 생성 합니다.

```cpp
// C2808.cpp
// compile with: /c
class X {
public:
   X operator! ( X );   // C2808 nonvoid parameter list
   X operator! ( void );   // OK
};
```
